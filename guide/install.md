
# 安装使用

需要安装Node.js v16及以上版本。

### 安装与运行

* 获取项目代码

```
git clone https://github.com/nihaojob/vue-fabric-editor.git
```

* 安装依赖

```
cd vue-fabric-editor
npm install
```

* 运行

```
npm run dev
```

* 打包

```
npm run build
```

### 项目目录

核心文件在core目录中，功能组件在components中。

```
├── src
│   ├── App.tsx
│   ├── App.vue
│   ├── assets      // 静态资源
│   │   ├── editor
│   │   ├── filters
│   │   └── fonts
│   ├── components // vue功能组件
│   │   ├── align.vue  // 元素对齐
│   │   ├── attribute.vue // 属性修改
│   │   ├── bgBar.vue // 画布设置
│   │   ├── centerAlign.vue // 居中对齐
│   │   ├── clone.vue // 复制 
│   │   ├── color.vue // 颜色组件 支持渐变与单色设置
│   │   ├── contextMenu // 右键菜单
│   │   ├── del.vue // 元素删除
│   │   ├── dragMode.vue // 
│   │   ├── filters.vue // 滤镜
│   │   ├── flip.vue // 反转
│   │   ├── fontTmpl.vue // 字体样式模板 
│   │   ├── group.vue // 组合操作
│   │   ├── history.vue // 历史记录
│   │   ├── importFile.vue  // 插入图片文件
│   │   ├── importJSON.vue  // 导入JSON文件
│   │   ├── importTmpl.vue  // 模板
│   │   ├── inputNumber  // 数字左键 支持左右滑动调节
│   │   ├── lang.vue // 国际化
│   │   ├── layer.vue // 图层管理
│   │   ├── lock.vue // 图层锁定
│   │   ├── previewCurrent.vue // 图片预览
│   │   ├── replaceImg.vue // 图片替换
│   │   ├── save.vue // 文件保存 支持图片、JSON格式
│   │   ├── setSize.vue  
│   │   ├── svgEl.vue // 分类SVG素材
│   │   ├── svgIcon
│   │   ├── tools.vue  // 插入元素 
│   │   └── zoom.vue   // 画布缩放功能
│   ├── config
│   │   └── constants
│   ├── core  // 编辑器核心文件
│   │   ├── EditorGroupText.ts    // 组内文字可编辑
│   │   ├── EditorWorkspace.ts  //画布区域模拟
│   │   ├── index.ts // 入口文件
│   │   ├── initAligningGuidelines.ts // 辅助线工
│   │   ├── initCenterAlign.ts   //  对齐方式功能
│   │   ├── initControls.ts      // 自定义控制条
│   │   ├── initControlsRotate.ts   // 自定义控制条
│   │   ├── initHotKeys.ts // 快捷键
│   │   ├── initializeLineDrawing.js    // 线条绘制
│   │   ├── objects // 自定义元素 箭头、线条
│   │   └── ruler  // 标尺功能
│   ├── env.d.ts
│   ├── hooks
│   │   └── select.js
│   ├── language //  国际化文件
│   │   ├── en.json
│   │   ├── index.ts
│   │   ├── pt.json
│   │   └── zh.json
│   ├── main.ts
│   ├── mixins
│   │   └── select.ts
│   ├── router
│   │   ├── index.ts
│   │   └── routes.ts
│   ├── styles
│   │   ├── index.less
│   │   ├── resetViewUi.less
│   │   └── variable.less
│   ├── utils
│   └── views
│       └── home  // 程序入口
├── tsconfig.json
├── tsconfig.node.json
├── typings
│   ├── extends.d.ts
│   └── vue3-clipboard.d.ts
└── vite.config.ts
```

### 架构说明

通过组件 src/views/home.vue 作为入口文件，初始化Core功能代码的实例，并将实例通过 _Provide_/inject的方式注入到各个业务组件中，组件调用Core实例提供的API方法来实现业务功能。

<figure><img src="/public/Foxmail20230508010441.png" alt=""><figcaption></figcaption></figure>

