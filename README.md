技术分享——bootstrap
===================
@[响应式布局|bootstrap]
#####一、了解响应式布局
简而言之，就是一个网站能够兼容多个终端——而不是为每个终端做一个特定的版本。这个概念是为解决移动互联网浏览而诞生的。
* 优点：
面对不同分辨率设备灵活性强
能够快捷解决多设备显示适应问题
* 缺点：
兼容各种设备工作量大，效率低下
代码累赘，会出现隐藏无用的元素，加载时间加长
其实这是一种折中性质的设计解决方案，多方面因素影响而达不到最佳效果
一定程度上改变了网站原有的布局结构，会出现用户混淆的情况
#####二、利用css3-Media Query实现响应式布局
* 在link中使用@media：
	```
	<link rel="stylesheet" media="screen and (min-width: 900px)" href="link.css">
	```

* 在样式表中内嵌@media：
	```
	@media screen and (min-width: 900px) {
		选择器 {
			属性: 属性名;
		}
	}
	//screen：指的是一种媒体类型；
	//and：被称为关键词，与其相似的还有not,only。可能的操作符
	//max-width:900px这个就是属性值，媒体特性，也就是就是媒体条件。
	```
	
[举个栗子](http://martin0809.github.io/yetang/demo.html)
#####三、Bootstrap
######1.简介
Bootstrap 是最受欢迎的 HTML、CSS 和 JS 框架，用于开发响应式布局、移动设备优先的 WEB 项目。
Bootstrap 是完全开源的。它的代码托管、开发、维护都依赖 GitHub 平台。[查看Github项目首页](https://github.com/twbs/bootstrap)
######2.起步
下载编译并压缩后的 CSS、JavaScript 和字体文件。也可使用Bootstrap中文网提供的免费CDN加速服务
```
<!-- 新 Bootstrap 核心 CSS 文件 -->
<link rel="stylesheet" href="http://cdn.bootcss.com/bootstrap/3.3.4/css/bootstrap.min.css">

<!-- 可选的Bootstrap主题文件（一般不用引入） -->
<link rel="stylesheet" href="http://cdn.bootcss.com/bootstrap/3.3.4/css/bootstrap-theme.min.css">

<!-- jQuery文件。务必在bootstrap.min.js 之前引入 -->
<script src="http://cdn.bootcss.com/jquery/1.11.2/jquery.min.js"></script>

<!-- 最新的 Bootstrap 核心 JavaScript 文件 -->
<script src="http://cdn.bootcss.com/bootstrap/3.3.4/js/bootstrap.min.js"></script>
```
######3.全局css样式
为了确保适当的绘制和触屏缩放，需要在`<head>`之中**添加 viewport 元数据标签**。
```
<meta name="viewport" content="width=device-width, initial-scale=1">
```
Bootstrap为我们设置了全局 CSS 样式，基本的 HTML 元素均可以通过 class 设置样式并得到增强效果，还有先进的栅格系统。这里我们重点介绍一下栅格系统：
>栅格系统用于通过一系列的行（row）与列（`column`）的组合来创建页面布局，你的内容就可以放入这些创建好的布局中。
>* “行（row）”必须包含在 `.container` （固定宽度）或 `.container-fluid` （100% 宽度）中，以便为其赋予合适的排列（aligment）和内补（padding）。
>* 通过“行（row）”在水平方向创建一组“列（column）”。
>* 你的内容应当放置于“列（column）”内，并且，只有“列（column）”可以作为行（row）”的直接子元素。
>* 类似 `.row` 和 `.col-xs-4` 这种预定义的类，可以用来快速创建栅格布局。Bootstrap 源码中定义的 mixin 也可以用来创建语义化的布局。
>* 通过为“列（column）”设置 `padding` 属性，从而创建列与列之间的间隔（gutter）。通过为 `.row` 元素设置负值 `margin` 从而抵消掉为 .container 元素设置的 `padding`，也就间接为“行（row）”所包含的“列（column）”抵消掉了`padding`。
>* 负值的 `margin`就是下面的示例为什么是向外突出的原因。在栅格列中的内容排成一行。
>* 栅格系统中的列是通过指定1到12的值来表示其跨越的范围。例如，三个等宽的列可以使用三个 `.col-xs-4` 来创建。
>* 如果一“行（row）”中包含了的“列（column）”大于 12，多余的“列（column）”所在的元素将被作为一个整体另起一行排列。
>* 栅格类适用于与屏幕宽度大于或等于分界点大小的设备 ， 并且针对小屏幕设备覆盖栅格类。 因此，在元素上应用任何 `.col-md-*` 栅格类适用于与屏幕宽度大于或等于分界点大小的设备 ， 并且针对小屏幕设备覆盖栅格类。 因此，在元素上应用任何 `.col-lg-*` 不存在， 也影响大屏幕设备。

举个例子：
```
<div class="row">
  <div class="col-md-1">.col-md-1</div>
  <div class="col-md-1">.col-md-1</div>
  <div class="col-md-1">.col-md-1</div>
  <div class="col-md-1">.col-md-1</div>
  <div class="col-md-1">.col-md-1</div>
  <div class="col-md-1">.col-md-1</div>
  <div class="col-md-1">.col-md-1</div>
  <div class="col-md-1">.col-md-1</div>
  <div class="col-md-1">.col-md-1</div>
  <div class="col-md-1">.col-md-1</div>
  <div class="col-md-1">.col-md-1</div>
  <div class="col-md-1">.col-md-1</div>
</div>
<div class="row">
  <div class="col-md-8">.col-md-8</div>
  <div class="col-md-4">.col-md-4</div>
</div>
<div class="row">
  <div class="col-md-4">.col-md-4</div>
  <div class="col-md-4">.col-md-4</div>
  <div class="col-md-4">.col-md-4</div>
</div>
<div class="row">
  <div class="col-md-6">.col-md-6</div>
  <div class="col-md-6">.col-md-6</div>
</div>
```
[运行代码](http://martin0809.github.io/yetang/grid.html#grid)

同时我们还可以设置列的偏移，使用 .col-md-offset-* 类可以将列向右侧偏移。这些类实际是通过使用 * 选择器为当前元素增加了左侧的边距（margin）。例如，.col-md-offset-4 类将 .col-md-4 元素向右侧偏移了4个列（column）的宽度：
```
<div class="row">
  <div class="col-md-4">.col-md-4</div>
  <div class="col-md-4 col-md-offset-4">.col-md-4 .col-md-offset-4</div>
</div>
<div class="row">
  <div class="col-md-3 col-md-offset-3">.col-md-3 .col-md-offset-3</div>
  <div class="col-md-3 col-md-offset-3">.col-md-3 .col-md-offset-3</div>
</div>
<div class="row">
  <div class="col-md-6 col-md-offset-3">.col-md-6 .col-md-offset-3</div>
</div>
```
[运行代码](http://martin0809.github.io/yetang/grid.html#offset)
######4.javascript插件
Bootstrap 自带 12 种 jQuery 插件，扩展了功能，可以给站点添加更多的互动。即使您不是一名高级的 JavaScript 开发人员，您也可以着手学习 Bootstrap 的 JavaScript 插件。利用 Bootstrap 数据 API（Bootstrap Data API），大部分的插件可以在不编写任何代码的情况被触发。
站点引用 Bootstrap 插件的方式有两种：
* 单独引用：使用 Bootstrap 的个别的 *.js 文件。一些插件和 CSS 组件依赖于其他插件。如果您单独引用插件，请先确保弄请这些插件之间的依赖关系。
* 编译（同时）引用：使用 bootstrap.js 或压缩版的 bootstrap.min.js。

**模态框：**
模态框（Modal）是覆盖在父窗体上的子窗体。通常，目的是显示来自一个单独的源的内容，可以在不离开父窗体的情况下有一些互动。子窗体可提供信息、交互等。
* 通过 `data` 属性：在控制器元素（比如按钮或者链接）上设置属性 `data-toggle="modal"`，同时设置 `data-target="#identifier"` 或 `href="#identifier"` 来指定要切换的特定的模态框（带有 `id="identifier"`）。
* 通过` JavaScript`：使用这种技术，您可以通过简单的一行 `JavaScript` 来调用带有 `id="identifier"` 的模态框：
```
$('#identifier').modal(options)
```
		
举个栗子：
```
<h2>创建模态框（Modal）</h2>
<!-- 按钮触发模态框 -->
<button class="btn btn-primary btn-lg" data-toggle="modal" 
   data-target="#myModal">
   开始演示模态框
</button>

<!-- 模态框（Modal） -->
<div class="modal fade" id="myModal" tabindex="-1" role="dialog" 
   aria-labelledby="myModalLabel" aria-hidden="true">
   <div class="modal-dialog">
      <div class="modal-content">
         <div class="modal-header">
            <button type="button" class="close" 
               data-dismiss="modal" aria-hidden="true">
                  &times;
            </button>
            <h4 class="modal-title" id="myModalLabel">
               模态框（Modal）标题
            </h4>
         </div>
         <div class="modal-body">
            在这里添加一些文本
         </div>
         <div class="modal-footer">
            <button type="button" class="btn btn-default" 
               data-dismiss="modal">关闭
            </button>
            <button type="button" class="btn btn-primary">
               提交更改
            </button>
         </div>
      </div><!-- /.modal-content -->
</div><!-- /.modal -->
```
[运行代码](http://martin0809.github.io/yetang/grid.html#modalDemo)

代码讲解：
* 使用模态窗口，您需要有某种触发器。您可以使用按钮或链接。这里我们使用的是按钮。
* 如果您仔细查看上面的代码，您会发现在 `<button>` 标签中，`data-target="#myModal"` 是您想要在页面上加载的模态框的目标。您可以在页面上创建多个模态框，然后为每个模态框创建不同的触发器。现在，很明显，您不能在同一时间加载多个模块，但您可以在页面上创建多个在不同时间进行加载。
* 在模态框中需要注意两点：
	* 第一是 `.modal`，用来把 `<div>` 的内容识别为模态框。
	* 第二是 `.fade` class。当模态框被切换时，它会引起内容淡入淡出。
* `aria-labelledby="myModalLabel"`，该属性引用模态框的标题。
* 属性 `aria-hidden="true"` 用于保持模态窗口不可见，直到触发器被触发为止（比如点击在相关的按钮上）。
* `<div class="modal-header">`，`modal-header` 是为模态窗口的头部定义样式的类。
* `class="close"`，`close` 是一个 CSS class，用于为模态窗口的关闭按钮设置样式。
* `data-dismiss="modal"`，是一个自定义的 HTML5 data 属性。在这里它被用于关闭模态窗口。
* `class="modal-body"`，是 Bootstrap CSS 的一个 CSS class，用于为模态窗口的主体设置样式。
* `class="modal-footer"`，是 Bootstrap CSS 的一个 CSS class，用于为模态窗口的底部设置样式。
* `data-toggle="modal"`，HTML5 自定义的 `data` 属性 `data-toggle` 用于打开模态窗口。

######5.定制
Bootstrap还支持通过自定义 Bootstrap 组件、Less 变量和 jQuery 插件，定制一份属于符合自己要求的 Bootstrap 版本。

----------------------------------------------------------------------------------------------------------------------------------------------
*更多详细内容请查看[Bootstrap中文网](http://v3.bootcss.com/)*
