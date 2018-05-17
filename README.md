# babel
本文介绍Babel6.x的安装过程~

首先呢，可以使用Babel在线转换 https://babeljs.io/repl/

1、首先安装babel-cli（用于在终端使用babel）  

　　npm install -g babel-cli
 

2、然后安装babel-preset-es2015插件

　　npm install --save babel-preset-es2015
　　注：Babel5版本默认包含各种转换插件，然而Babel6.x相关转换插件需要自己下载，如transform-es2015-arrow-functions、transform-es2015-classes等，而ES2015 preset包含了所有插件。如果不安装任何插件，那么在命令行进行转换是没有任何效果的！

　　其中--save参数自动更新package.json文件，写进依赖项

 

3、在命令行输入：

　　babel es6.js --presets es2015
输出：

　　"use strict";

　　[1, 2, 3].map(function (x) {
　　  return x * x;
　　});
　　注：后面的参数--presets es2015表示使用该插件进行编译，如果不写上转换是没有效果的。

　

4、插件配置

　　每一次都写上该参数那是很麻烦的，可以在当前目录下新建配置文件 .babelrc。

　　但是在windows系统中，不允许直接右键建立没有文件名的文件，可以通过cmd命令行创建：在当前文件夹打开cmd并键入命令

　　type nul>.babelrc
　　即可在当前目录下建立文件.babelrc，接着在文件中写入：

　{
　　　"presets": ['es2015']
　}
　　那么就可以直接在命令行中使用babel es6.js进行转换而无需添加表明所用插件的参数

 

　　除了建立.babelrc文件之外，也可在package.json中进行配置，添加以下属性即可：

  "babel": {
   　　"presets": ["es2015"]
  }
 

附Babel常用命令：

1、转换es6.js文件并在当前命名行程序窗口中输出

　　babel es6.js
 

2、将es6.js转换后输出到es5.js文件中（使用 -o 或 --out-file ）

　　babel es6.js -o es5.js 

　　babel es6.js --out-file es5.js
 

3、实时监控es6.js一有变化就重新编译（使用 -w 或 --watch ）

　　babel es6.js -w --out-file es5.js

　　babel es6.js --watch --out-file es5.js
 

4、编译整个src文件夹并输出到lib文件夹中（使用 -d 或 --out-dir ）

　　babel src -d lib

　　babel src --out-dir lib
 

5、编译整个src文件夹并输出到一个文件中

　　babel src --out-file es5.js
 

6、直接输入babel-node命令，可以在命令行中直接运行ES6代码

　　babel-node