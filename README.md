# miniprogram-gifmaker

GIF动画制作微信小程序

<img width="180" height="180" src="https://github.com/planet0104/miniprogram-gifmaker/blob/master/code0.jpg" />
<img width="180" height="180" src="https://github.com/planet0104/miniprogram-gifmaker/blob/master/code1.jpg" />

其中GIF生成的功能是用Rust实现的，使用stdweb和gif两个库，将Rust代码编译成asmjs

> 本来打算到<b>Webassembly</b>，性能更好，但是发现微信对wasm支持有问题：<b>第一、</b>在开发者工具中测试没问题，真机调试以后，只要杀死小程序，第二次进入，重新执行require，Webassembly重新编译的时候就过不去了。在android中没有任何提示，Promise的catch和then方法都不会调用；在iOS中提示:Error: Out of executable memory at import0。使用最简单的代码、第二次编译一份不同的代码也都不行。<b>第二、</b>android5.1中不支持Webassemlby。所以只能选择asmjs的编译目标。
> <b>编译到Webassembly</b>用stdweb编译到wams和js文件以后，微信小程序直接是不可以用的，首先HelloWorld代码中的alert()不支持，可以在生成的js中实现一个alert函数，其中调用微信的wx.showModal来实现弹窗。其次微信小程序中没有fetch方法，可以在生成的js中实现一个返回Promise的fetch函数，或者直接修改Webassemlby编译那一块的代码，使用小程序API的FileSystemManager.readFile来读取wasm文件。

https://crates.io/crates/stdweb

https://crates.io/crates/gif

<b>/ministdweb</b> Rust代码(生成GIF)

<b>/program</b> 微信小程序代码

program中的代码可以直接在微信开发工具编译运行，/workers/ministdweb.js是编译好的Rust代码。

<img src="https://github.com/planet0104/miniprogram-gifmaker/blob/master/screenshot.png" />
