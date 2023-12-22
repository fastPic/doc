# 插件化架构

讨论参见 https://github.com/nihaojob/vue-fabric-editor/issues/205

## Editor Core模块封装

初始化实例后，将初始化后的实例注入到各个组件中，供其他组件调用，引入插件机制，确保其他插件可灵活的引入到Editor对象中。

```typescript
import CanvasRuler from '@/core/ruler/ruler';
import EditorWorkspace from '@/core/EditorWorkspace';


// 初始化 fabric画布
const canvas = new fabric.Canvas('canvas')

// 引入插件 可选传入自定义配置
Editor.use(EditorWorkspace).use(CanvasRuler, { color: 'red', size: 0.1 })
// 初始化编辑器
const editor = new Editor(canvas)

```



## 插件化

为什么要插件，fabric.js已经是一个支持发布订阅，可扩展的canvas  library。再基于fabric.js封装一个层插件化架构，是否过度设计的一些辩证思考。

1. 我们希望构建一个可便捷扩展的编辑器，而非底层library。
2. 编辑器应用与libray不在一个分层中，编辑器依赖library，但是编辑器属于更上层的应用层，有自己独特的生命周期与扩展需求。
3. 生命周期：导入文件前后、插入素材、保存文件前后等操作，我们很多功能模块需要根据这些周期相应的处理。
4. 扩展需求：编辑器需要天然支持可快速扩展右键菜单和快捷键的功能，以及模块内的API和事件通知。
5. 基于fabric.js 和 编辑器的插件机制，我对比了一下现有功能模块，可以更好的将功能内聚在插件内，而非组件和功能耦合在一起。例如：
   1. 导入文件前进行字体的加载、画布大小的设置。
   2. 导出文件前隐藏标尺、画布大小调整操作。
   3. 保存文件后恢复标尺、画布大小。
   4. 快捷键、右键菜单可通过配置化的方式导入到个个模块，将功能内聚在功能模块中。

插件化应尽可能的简化，便于开发人员快速理解与扩展，但要满足基础的需求：

1. 插件可收到重要生命周期事件。
2. 插件可快速扩展快捷键。
3. 插件可快速扩展右键菜单。
4. 插件可保留出功能API，与发布订阅自己的插件事件。
5. 插件可获取原生fabric.js 的canvas 对象。
6. 插件之间可相互通讯（尽量避免，但需支持）。
7. 防止插件名称、API、订阅事件冲突。

### 插件代码Demo

**插件的静态属性：**

name： 插件名称

defautOption：插件内部使用的配置

events：插件内发布的事件，可供外部订阅。

apis：插件内暴露的API方法，可供外部调用。

hotkeys：插件内需要的快捷键事件名称，可接收回调。

**插件生命周期：**

init：初始化插件时调用。

destroy：销毁插件时调用。

**编辑器生命周期：**

hookSaveBefore：保存文件前。

hookSaveAfter：保存文件后。

**快捷键扩展事件：**

hotkeyEvent：插件中配置的hotkeys中的快捷键被触发时，调用该方法，并通过入参的形式返回时间名称。

**右键菜单扩展事件：**

contextMenu：当触发右键点击事件时，会调用该方法获取右键菜单的内容，返回数字形式，支持子菜单扩展。



```typescript
import ExtednPlugin from '@/core/ExtednPlugin';
// 注册插件
class rulerPlugin extends ExtednPlugin {
    // 插件名称
    name = 'ruler'
    // 插件默认配置
    defaultOption = {
        color: 'red',
        size: 0.2
    }
    // 内置事件，可通知其他插件
    events = {
        'createRulerStart': 'CREATE_RULER_START'
    }
    // API 暴露给外部使用
    apis = ['enableRuler', 'disableRuler']

    // 快捷键
    hotkeys = ['crtl+h']
  
    // 默认实现 ExtednPlugin
    // constructor(canvas, event, option = {}){
        // 自动将外部传入的属性合并
        // this.defaultOption = {defaultOption..., option}
        // 调用初始化方法
        // this.init()
        // 挂载上下文
        // this.ctx = { canvas, event, editor }
    //}
 
    // 初始化逻辑
    init(){
        // 获取属性
        const { color } = this.defaultOption
        // 通过上下文获取 canvas和event对象
        const { canvas, editor } = this
        canvas.on('', () => {
            // 发布事件
            this.editor.emit(this.events.createRulerStart)
            // 调用其他插件方法
            editor.getPlugin('otherPluginName')?.otherApiName()
        })
    }

    // 销毁逻辑
    destroy(){
      canvas.off('')
    }

   // 右键菜单的扩展 支持子菜单
   contextMenu() {
     // 判断条件 返回菜单与事件，可
    	if(true){
         return [{
            text: '菜单',
            command: this._commandHandler
          },
          {
            text: '父菜单',
            child:[{
                text: '子菜单',
                command: this._commandHandler
              }]
          }]     
      }
    }

    // 快捷键功能函数
    _commandHandler(){
      console.log('快捷键事件')
    }
  
    // 生命周期-保存前 隐藏标尺
    hookSaveBefore(){
        this._hideGuideline()
    }
    
    // 生命周期-保存后 展示标尺
    hookSaveAfter(){
        this._showGuideline()
    }

    // 快捷键回调
    hotkeyEvent(eventName, event){
        // 快捷键 显示隐藏标尺
        if(event = 'crtl+h'){
            this.status = !this.status
            this.status ? this._showGuideline() : this._hideGuideline
        }
    }
    
    // 暴漏给外部的API  激活标尺
    enable(){
        
    }   
    
    // 暴漏给外部的API  关闭标尺
    disable(){
    
    }
    
    // 私有方法  隐藏标尺
    _hideGuideline(){}

    // 私有方法  显示标尺
    _showGuideline(){}
    
}



// 初始化 fabric画布
const canvas = new fabric.Canvas('canvas')

// 引入插件 可选传入自定义配置
Editor.use(EditorWorkspace).use(CanvasRuler, { color: 'red', size: 0.1 })

// 初始化编辑器
const editor = new Editor(canvas)

// 调用插件方法 1
editor.enableRuler()
// 调用插件方法 2
const ruler = editor.getPlugin('ruler')
rule.enableRuler()


// 事件订阅
const ruler = editor.getPlugin('ruler')
editor.on(ruler.event.createRulerStart, () => {
  // do something
})

```



## Editor 架构说明

按照插件化重构后，将分层更加清晰，扩展更便捷。

1. Edirot：提供插件调度、安装机制。
2. plugin：约束插件规则，提供功能插件。
3. Components：业务组件，调用Edirot对象提供的API方法，可订阅编辑器内的事件。
4. commonUse：组件需高频使用的功能，如当前是单选、多选、选中ID等功能，属于业务功能，单独将组件需要的功能封装在通用hook中，供components使用。

<figure><img src="/public/Vue-Fabric-Editor.png" alt=""><figcaption></figcaption></figure>





#### 待定

内置插件：快捷键、导入文件、导出文件、导出图片、右键菜单、控制条样式、阴影、边框、字体。

增强插件：画布、标尺、滤镜、图片替换、居中对齐。

1. getPlugin(String) 获取插件
2. loadJSON(String) 根据JSON渲染&#x20;
3. loadFileJSON() 弹出选择本地JSON
4. saveJSON() 导出json
5. saveFile('json' | 'png' | 'jpeg') 导出文件
