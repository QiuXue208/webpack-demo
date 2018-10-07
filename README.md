# webpack-demo

 ### 使用webpack
 1. 用babel-loader将ES6转译为ES5
 2. 用sass-loader将SCSS转译为CSS


 ### 操作步骤

 #####   创建目录、进入目录

 ` mkdir webpack-demo && cd webpack-demo `

 #####   创建package.json文件

 ` npm init -y `

 #####   安装webpack、webpack-cli

 ` npm install webpack webpack-cli --save-dev `

 #####  使用配置

 ` touch webpack.config.js `

 #####   编辑文件


```
/* 将src/index.js文件拷贝到dist/main.js中 */
const path = require('path');

module.exports = {
  //入口
  entry: './src/index.js',
  //输出
  output: {
     filename: 'main.js',
     path: path.resolve(__dirname, 'dist')
  }
};
```

 #####   运行webpack.config.js文件，将entry文件拷贝到output中的文件

 ` npx webpack `

#####   创建新的文件

 `mkdir -p src/js`

 `cd src/js`

 `touch app.js module-1.js module-2.js`

 #####  编辑新创建的文件的内容

 module-1.js:
 ```
 function fn(){
    alert('这是模块一')
}
/*当有人调用我时，我就把fn传给他*/
export default fn
 ```
 module-2.js
 ```
 function fn(){
    alert('这是模块二')
}
export default fn
```
app.js:
```
/*这里module1就代表了fn*/
import module1 from './module-1'
import module2 from './module-2'
alert('这是进口文件')
module1()
module2()
```

 ##### 修改webpack.config.js文件

```
/* 将src/js/app.js文件拷贝到dist/js/bundle.js中 */
const path = require('path');

module.exports = {
  //入口
  entry: './src/js/app.js',
  //输出
  output: {
    filename: 'bundle.js',
    path: path.resolve(__dirname, 'dist/js')
  }
};
```
##### 重新运行一下webpack.config.js文件

这次运行入口文件是`./src/js/app`,所以它会将该文件的内容拷贝到`dist/js/bundle.js`文件中

` npx webpack`

##### 创建主页，并引入经过处理后的js文件
` touch index.html`

` vi index.html`

```
<body>
    <script src="./dist/js/bundle.js"></script>
</body>
```

##### 运行webpack-demo项目

由于引入的文件中是app.js文件中拷贝过去的，所以运行的内容为app.js中的内容。

结果如下:

![app](http://pg7gx692c.bkt.clouddn.com/Screenshot_1.png)

![module1](http://pg7gx692c.bkt.clouddn.com/Screenshot_2.png)

![module2](http://pg7gx692c.bkt.clouddn.com/Screenshot_3.png)

