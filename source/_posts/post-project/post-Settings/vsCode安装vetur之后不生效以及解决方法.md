---
title: vsCoe安装vetur之后不生效以及解决方法 
date:  2019-08-20 20:17:06
tags:  工具配置
---


打开文件——首选项——设置——最下面的vetur，进入到 settings.json文件编辑之中，将以下代码复制进去：

```json
{
 // 强制单引号
 "prettier.singleQuote": true,
 // 尽可能控制尾随逗号的打印
 "prettier.trailingComma": "all",
 // 开启 eslint 支持
 "prettier.eslintIntegration": true,
 // 保存时自动fix
 "eslint.autoFixOnSave": true,
 // 添加 vue 支持
 "eslint.validate": [
  "javascript",
  "javascriptreact",
  {
   "language": "vue",
   "autoFix": true
  }
 ],
 // 使用插件格式化 html
 "vetur.format.defaultFormatter.html": "js-beautify-html",
 // 格式化插件的配置
 "vetur.format.defaultFormatterOptions": {
  "js-beautify-html": {
   // 属性强制折行对齐
   "wrap_attributes": "force-aligned"
  }
 },
 "vetur.format.defaultFormatter": {
     "html": "prettier",
     "css": "prettier",
     "postcss": "prettier",
     "scss": "prettier",
     "less": "prettier",
     "js": "prettier",
     "ts": "prettier",
     "stylus": "stylus-supremacy"
 },
 // html颜色高亮
 "files.associations": {
     ".eslintrc": "json",
     "*.vue": "html"
 },
 "emmet.syntaxProfiles": {
     "javascript": "jsx",
     "vue": "html",
     "vue-html": "html"
 }
}

```

然后就实现了代码高亮等需要的功能了。