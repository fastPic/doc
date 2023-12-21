
# 贡献指南

你好！我们很高兴你有兴趣为 vue-fabric-editor 做出贡献。在提交你的贡献之前，请花点时间阅读以下指南：

### 快速上手

vue-fabric-editor 依赖Node.js v16版本进行开发，要确保你本地已安装Node.js。

你可以参考[安装与使用](https://nihaojob.gitbook.io/editor/an-zhuang-shi-yong)来了解项目的架构。

## Issue

有任何疑问，欢迎提交[Issue](https://github.com/nihaojob/vue-fabric-editor/issues)。

* 请确定 issue 的类型。
* 请避免提交重复的 issue，在提交之前搜索现有的 issue。
* 在标签(分类参考**标签分类**), 标题 或者内容中体现明确的意图。

随后项目负责人会确认 issue 意图，更新合适的标签，并做出回复或指派开发者。

### 第一次贡献

如果你还不清楚怎么在 GitHub 上提 Pull Request ，可以阅读下面这篇文章来学习：

[如何优雅地在 GitHub 上贡献代码](https://segmentfault.com/a/1190000000736629)

为了能帮助你开始你的第一次尝试，我们用 [good first issues](https://github.com/nihaojob/vue-fabric-editor/labels/good%20first%20issue) 标记了一些比较容易修复的 bug 和小功能。这些 issue 可以很好地作为你的首次尝试。

如果你打算开始处理一个 issue，请先检查一下 issue 下面的留言以确保没有别人正在处理这个 issue。如果当前没有人在处理的话你可以留言告知其他人你将会处理这个 issue，以免别人重复劳动。

如果之前有人留言说会处理这个 issue 但是一两个星期都没有动静，那么你也可以接手处理这个 issue，当然还是需要留言告知其他人。

## commit

我们根据[约定式提交规范](https://www.conventionalcommits.org/zh-hans/v1.0.0/)，这样 history 看起来更加清晰，包含了结构化元素以表明其意图。

```
<type>(<scope>): <subject>
<BLANK LINE>
<body>
<BLANK LINE>
<footer>
```

提交 commit 的类型，包括以下几种

* feat: 新功能
* fix: 修复问题
* docs: 修改文档
* style: 修改代码格式，不影响代码逻辑
* refactor: 重构代码，理论上不影响现有功能
* perf: 提升性能
* test: 增加修改测试用例
* chore: 修改工具相关（包括但不限于文档、代码生成等）
* deps: 升级依赖

提交说明包含了下面的结构化元素：

1. **fix:** _类型_ 为 `fix` 的提交表示在代码库中修复了一个 bug（这和语义化版本中的 [`PATCH`](https://semver.org/lang/zh-CN/#%E6%91%98%E8%A6%81) 相对应）。
2. **feat:** _类型_ 为 `feat` 的提交表示在代码库中新增了一个功能（这和语义化版本中的 [`MINOR`](https://semver.org/lang/zh-CN/#%E6%91%98%E8%A6%81) 相对应）。
3. **BREAKING CHANGE:** 在脚注中包含 `BREAKING CHANGE:` 或 <类型>(范围) 后面有一个 `!` 的提交，表示引入了破坏性 API 变更（这和语义化版本中的 [`MAJOR`](https://semver.org/lang/zh-CN/#%E6%91%98%E8%A6%81) 相对应）。 破坏性变更可以是任意 _类型_ 提交的一部分。
4. 除 `fix:` 和 `feat:` 之外，也可以使用其它提交 _类型_ ，例如 [@commitlint/config-conventional](https://github.com/conventional-changelog/commitlint/tree/master/%40commitlint/config-conventional)（基于 [Angular 约定](https://github.com/angular/angular/blob/22b96b9/CONTRIBUTING.md#-commit-message-guidelines)）中推荐的 `build:`、`chore:`、 `ci:`、`docs:`、`style:`、`refactor:`、`perf:`、`test:`，等等。
5. 脚注中除了 `BREAKING CHANGE: <description>` ，其它条目应该采用类似 [git trailer format](https://git-scm.com/docs/git-interpret-trailers) 这样的惯例。

## Pull Request

我们会 review 以及合并你的代码，也有可能要求你做一些修改或者告诉你我们为什么不能接受这样的修改。

由于谁也无法保证过了多久之后还记得多少，为了后期回溯历史的方便，请在提交 MR 时确保提供了以下信息。

1. 需求点（一般关联 issue 或者注释都算）。
2. 升级原因（不同于 issue，可以简要描述下为什么要处理）。
3. 框架测试点（可以关联到测试文件，不用详细描述，关键点即可）。
4. 关注点（针对用户而言，可以没有，一般是不兼容更新等，需要额外提示）。

## 最后

衷心期望能有越来越多的贡献者和合作者加入，一起共建一款优秀的开源图形编辑器。





