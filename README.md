# miniprogram-gifmaker

GIF动画制作微信小程序

<img width="180" height="180" src="https://github.com/planet0104/miniprogram-gifmaker/blob/master/code0.jpg" />
<img width="180" height="180" src="https://github.com/planet0104/miniprogram-gifmaker/blob/master/code1.jpg" />

其中GIF生成的功能是用Rust实现的，使用stdweb和gif两个库

> 本来打算到<b>Webassembly</b>，性能更好，但是发现微信对wasm支持有问题：第一、在开发者工具中测试没问题，真机调试以后，只要杀死小程序，第二次进入，重新执行require，Webassembly重新编译的时候就过不去了。在android中没有任何提示，Promise的catch和then方法都不会调用；在iOS中提示:Error: Out of executable memory at import0。第二次编译一份不同的wasm代码也不行。第二、android5.1中不支持Webassemlby。所以最终选择了asmjs的编译目标。

https://crates.io/crates/stdweb

https://crates.io/crates/gif

<b>/ministdweb</b> Rust代码(生成GIF)

<b>/program</b> 微信小程序代码

program中的代码可以直接在微信开发工具编译运行，/workers/ministdweb.js是编译好的Rust代码。

<img src="https://github.com/planet0104/miniprogram-gifmaker/blob/master/screenshot.png" />
