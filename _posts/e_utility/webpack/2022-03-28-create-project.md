---
layout: post
title:  webpack 搭建项目
summary:
categories: Utility
technique: true
---

```javascript
// webpack 版本
"webpack": "^5.70.0",
"webpack-cli": "^4.9.2",  
"webpack-dev-server": "^4.7.4"
```

```javascript
// webpack.config.js
const path = require("path"); // node 的路径模块
module.exports = {
  entry: {
    app: ["./src/main.js"], // 入口文件
  },
  output: {
    path: path.resolve(__dirname, "dist"), // 输出位置
    publicPath: "/my/", // 指定资源文件引用的目录，见 index.html
    filename: "bundle.js" // 输出文件名称
  },
  mode: "development",
  devServer: {
    static: {
      // 指定服务启动的静态页面目录
      directory: path.join(__dirname, "public")
    }
  }
};
```
```html
<!-- public/index.html -->
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>源码</title>
</head>
<body>
  <div id="app">源码学习</div>
</body>
</body>
</html>
</html>
<!-- 注意路径引用 -->
<script src="/my/bundle.js"></script>  
```
