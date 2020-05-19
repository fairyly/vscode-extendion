# vscode-extension

>vscode-extension

## install

```
安装脚手架:

npm install -g yo generator-code

然后cd到你的工作目录，运行 yo code

根据向导一步步选择即可
```
## 项目结构
>项目结构其实很简单，主要是清单文件package.json以及extension.js这个插件入口文件：

```
package.json部分关键内容如下（已省略其它）
{
	// 扩展的激活事件
	"activationEvents": [
		"onCommand:extension.sayHello"
	],
	// 入口文件
	"main": "./extension",
	// 贡献点，vscode插件大部分功能配置都在这里
	"contributes": {
		"commands": [
			{
				"command": "extension.sayHello",
				"title": "Hello World"
			}
		]
	}
}
src/extension.js 内容如下：
const vscode = require('vscode');

/**
 * 插件被激活时触发，所有代码总入口
 * @param {*} context 插件上下文
 */
exports.activate = function(context) {
	console.log('恭喜，您的扩展"vscode-plugin-demo"已被激活！');
	// 注册命令
	let disposable = vscode.commands.registerCommand('extension.helloWorld', function () {
		// The code you place here will be executed every time your command is executed

		// Display a message box to the user
		vscode.window.showInformationMessage('Hello World!');
	});

	context.subscriptions.push(disposable);
};

/**
 * 插件被释放时触发
 */
exports.deactivate = function() {
	console.log('您的扩展"vscode-plugin-demo"已被释放！')
};
```



## 参考

- [Extension API](https://code.visualstudio.com/api)
- [vscode-extension-samples](https://github.com/Microsoft/vscode-extension-samples)
- [VSCode插件开发-基础项目结构](https://github.com/fairyly/html-demo/blob/gh-pages/2.5.7%20VSCode%E6%8F%92%E4%BB%B6%E5%BC%80%E5%8F%91-%E5%9F%BA%E7%A1%80%E9%A1%B9%E7%9B%AE%E7%BB%93%E6%9E%84.md)
- [VSCode插件开发-中文文档](https://liiked.github.io/VS-Code-Extension-Doc-ZH/#/)
