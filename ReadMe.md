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
      filename: 'js/[name].[contenthash:8].js',
      chunkFilename: 'js/[name].[contenthash:8].js',
      publicPath: './'
    }
  }
```
修改package.json
```
"serve": "webpack ./src/main.js --config ./build/webpack.config.js"
```
## 2.2 配置 ES6/7/8 转 ES5代码

```
npm install babel-loader @babel/core @babel/preset-env
```

```
module: {
  rules: [
    {
      test: /\.jsx?$/,
      exclude: /node_modules/,
      use: [
        {
          loader: 'babel-loader'
        }
      ]
    }
  ]
}
```
在根目录添加babel.config.js
```
module.exports = {
  presets: [
    "@babel/preset-env"
  ]
}
```
- babel-loader 只会转语法，对api不会

```
npm install @babel/polyfill
```

## 2.2.1 ES6/7/8 Api 转es5

## 2.2.2 按需引入polyfill

```
npm install core-js@2 @babel/runtime-corejs2 -S
```

修改babel.config.js

```
module.exports = {
  presets: [
    ["@babel/preset-env", {
      "useBuiltIns": "usage"
    }]
  ]
}
```

## 2.2.3 配置scss转css

```
npm install sass-loader dart-sass css-loader style-loader -D
```
```
module: {
  rules: [
    {
      test: /\.jsx?$/,
      exclude: /node_modules/,
      use: [
        {
          loader: 'babel-loader'
        }
      ]
    },
    {
      test: /\.(scss|sass)$/,
      use: [
        {
          loader: 'style-loader'
        },
        {
          loader: 'css-loader'
        },
        {
          loader: 'sass-loader',
          options: {
            implementation: require('dart-sass')
          }
        },
        {
          loader: 'postcss-loader'
        }
      ]
    }
  ]
}
```

## 2.3

```
npm install postcss-loader autoprefixer -D
```
```
{
  loader: 'postcss-loader'
}
```
项目更目录新建 postcss.config.js
```
// postcss.config.js
module.exports = {
  plugins: {
    autoprefixer: {}
  }
}

```