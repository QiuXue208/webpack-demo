# webpack-demo

 ### 使用webpack
 1. 用babel-loader将ES6转译为ES5
 2. 用sass-loader将SCSS转译为CSS


 ### 操作步骤

 ######   创建目录、进入目录

 ` mkdir webpack-demo && cd webpack-demo `

 ######   创建package.json文件

 ` npm init -y `

 ######   安装webpack、webpack-cli

 ` npm install webpack webpack-cli --save-dev `

 ######   使用配置

 ` touch webpack.config.js `

 ######   编辑文件


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

 ######   运行webpack.config.js文件，将entry文件拷贝到output中的文件

 ` npx webpack `

######   创建新的文件

 `mkdir -p src/js`

 `cd src/js`
 
 `touch app.js module-1.js module-2.js`

 ######  编辑新创建的文件的内容

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

 ###### 修改webpack.config.js文件

```
  /* 将src/js/app文件拷贝到dist/bundle.js中 */
  const path = require('path');

  module.exports = {
    //入口
    entry: './src/js/app.js',
    //输出
    output: {
      filename: 'bundle.js',
      path: path.resolve(__dirname, 'dist')
    }
  };
```

