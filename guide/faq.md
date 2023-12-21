

# 常见问题

我将Fabric.js开发者的高频、高质量交流内容整理汇总在星球内，如果你还在使用Fabric.js做开发，相信我，与众多Fabric.js的开发者交流比单打独斗更高效。

<figure><img src="/public/231202037-18fe913f-81ab-4cd6-aa87-ada471e27586.png" alt=""><figcaption></figcaption></figure>

1. [移动端事件适配 touch事件](https://t.zsxq.com/0d8Fph4ZX)。
2. [如何给元素设置背景图片？](https://t.zsxq.com/0dx3Iu1cH)
3. [如何实现在fabric.js画布中插入gif图片？](https://t.zsxq.com/0doQ8rrO9)
4. [给单一组件设置控制条样式](https://t.zsxq.com/0dWA1cHRy)。
5. [免费可商用的字体素材](https://t.zsxq.com/0dUxqJzDb)。
6. [缩放画布后官方辅助线无法对齐问题。](https://t.zsxq.com/0dR73U5ej)
7. [如何实现超出画布后，元素不展示，控制条展示？](https://t.zsxq.com/0dqg0G8It)
8. [vue-fabric-editor项目部署到Nginx。](https://t.zsxq.com/0dLuVgHou)
9. [加载远程图片报crossOrigin的问题的3个解决办法。](https://t.zsxq.com/0dao4OZbn)
10. [如何让元素拖拽不超出画布？](https://t.zsxq.com/0dU4AXIlV)
11. [中文字体文件太大，加载太慢怎么处理？](https://t.zsxq.com/0daMiTHZG)
12. [如何实现竖排文字？](https://t.zsxq.com/0dM3rUhs3)
13. [保存为JSON时保留自定义属性。](https://t.zsxq.com/0dBRjf2Lg)
14. 更多内容持续积累...

### 如何高效地反馈问题？ <a href="#ru-he-gao-xiao-di-fan-kui-wen-ti" id="ru-he-gao-xiao-di-fan-kui-wen-ti"></a>

感谢您向我们反馈问题。

1. 我们推荐如果是小问题（错别字修改，小的 bug fix）直接提交 PR。
2. 如果是一个新需求，请提供：详细需求描述，最好是有伪代码示意。
3. 如果是一个 BUG，请提供：复现步骤，错误日志以及相关配置，并尽量填写下面的模板中的条目。
4. 不要挤牙膏似的交流，扩展阅读：[如何向开源项目提交无法解答的问题](https://zhuanlan.zhihu.com/p/25795393)

最重要的是，请明白一件事：开源项目的用户和维护者之间并不是甲方和乙方的关系，issue 也不是客服工单。在开 issue 的时候，请抱着一种『一起合作来解决这个问题』的心态，不要期待我们单方面地为你服务。



## 常见问题

### 1. 素材加载很慢

因为项目默认引用的github静态资源，所以会很慢，你可按照自定义素材配置进行修改。

### 2. 如何自定义素材

所有自定义素材在[https://github.com/nihaojob/vue-fabric-editor-static](https://github.com/nihaojob/vue-fabric-editor-static) 项目中保存。

1. 字体文件。
2. 字体样式模板。
3. 设计模板。

如果你想自定义一个设计模板，可以在编辑器中编辑完成后，在右上角点击保存为JSON,同时保存一张图片，将json文件和图片放在静态目录中，并在src/components/[importTmpl.vue](http://importtmpl.vue/)中增加新增的路径。



