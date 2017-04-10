##Loader
##### Webpack 本身只能处理 JavaScript 模块，如果要处理其他类型的文件，就需要使用 loader 进行转换。
***
##### Loader 可以理解为是模块和资源的转换器，它本身是一个函数，接受源文件
作为参数，返回转换的结果。这样，我们就可以通过 require 来加载任何类型的模块或文件，比如 CoffeeScript、 JSX、 LESS 或图片。
***
* Loader 可以通过管道方式链式调用，每个 loader 可以把资源转换成任意格式并传递给下一个 loader ，但是最后一个 loader 必须返回 JavaScript。
* Loader 可以同步或异步执行。
* Loader 运行在 node.js 环境中，所以可以做任何可能的事情。
* Loader 可以接受参数，以此来传递配置项给 loader。
* Loader 可以通过文件扩展名（或正则表达式）绑定给不同类型的文件。
* Loader 可以通过 npm 发布和安装。
* 除了通过 package.json 的 main 指定，通常的模块也可以导出一个 loader 来使用。
* Loader 可以访问配置。
* 插件可以让 loader 拥有更多特性。
* Loader 可以分发出附加的任意文件。

***
在引用 loader 的时候可以使用全名 json-loader，或者使用短名 json。这个命名规则和搜索优先级顺序在 webpack 的 resolveLoader.moduleTemplates api 中定义。
***
1. Loader 可以在 require() 引用模块的时候添加
2. 也可以在 webpack全局配置中进行绑定
3. 还可以通过命令行的方式使用
***
将 entry.js 中的 require("!style!css!./style.css") 修改为 require("./style.css") ，然后执行：
`	$ webpack entry.js bundle.js --module-bind 'css=style!css'
	# 有些环境下可能需要使用双引号
	$ webpack entry.js bundle.js --module-bind "css=style!css"`