# webpack-demo

使用webpack
1. 用babel-loader将ES6转译为ES5
2. 用sass-loader将SCSS转译为CSS


操作步骤
1. mkdir webpack-demo && cd webpack-demo //创建目录、进入目录
2. npm init -y  //创建package.json文件
3. npm install webpack webpack-cli --save-dev  //安装webpack、webpack-cli
4. touch webpack.config.js //使用配置
5. 编辑文件
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


