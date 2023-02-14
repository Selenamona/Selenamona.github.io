---
layout:     post
title:      自动打包同级目录下的项目
summary:
categories: Terminal
technique: true
---


```javascript
let fs = require("fs");
const path = require("path");
const child_process = require("child_process");
const command = "npm run build";
const targetDirs = process.argv.slice(2);
let dirs = [];
if (targetDirs.length) {
  dirs = targetDirs;
} else {
  const pro_path = path.resolve(__dirname, "./"); // /Users/yixin/Desktop/Saas
  dirs = fs.readdirSync(pro_path); // 【array】目录内所有文件及文件夹
}

// 过滤非文件夹，获取项目目录
const runApps = dirs.filter((item) => {
  return item.indexOf(".") < 0;
});

console.log(`打包项目列表：`, runApps);

runApps.forEach(async (i) => {
  child_process.exec(
    `cd ${i} && git checkout SPDB_test && ${command}`,
    (error, stdout, stderr) => {
      if (error) {
        console.log("执行失败：", error);
        return 
      }
      console.log("\033[93m"+`开始打包${i}`+"\033[0m")

      console.log(stderr);
      console.log(stdout);
    }
  ); 
});

process.on("unhandledRejection", (reason, p) => {
  console.log("Unhandled Rejection at: Promise", p, "reason:", reason);
});

/**
 * node test.js 打包所有项目
 * node test.js XXX 打包指定项目
 */

````
