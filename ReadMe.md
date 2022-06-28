从零搭建vue-cli
# 1、初始化项目环境

## 1.1 初始化项目

```
  npm init
```

## 1.2 安装webpack

```
  npm install webpack webpack -D
```

## 1.3 测试webpack

```
  新建 src/main.js
  // package.json -> scripts
  "serve": "webpack ./src/main.js --mode development"
  如果在dist中生成main.js说明webpack 生成正常
```

# 2、配置功能

## 2.1 配置webpack基本配置

```
  const path = require('path')

  module.exports = {
    mode: 'development',
    entry: {
      main: path.resolve(__dirname, '../src/main.js')
    },
    output: {
      path: path.resolve(__dirname, '../dist/main.js'),
      filename: 'js/[name].[hash:8].js',
      chunkFilename: 'js/[name].[hash:8].js',
      publicPath: './'
    }
  }
```
修改package.json
```
"serve": "webpack ./src/main.js --config ./build/webpack.config.js"
```