---
title: gulp给静态资源加版本号 
# cover: /images/gulp.jpg
author: 
  nick: Viola
  link: https://github.com/TangF
tags:
  gulp
---

#### 前言
在现在MVVM很流行的情境下，这种需求其实不是很多。但是，实际项目中遇到了，然后百度，Google都没找到合适的解决方案，所以还是记录一下。

#### 需求
为了清除缓存，给静态资源加上版本号。

#### 打包工具
`gulp`，主要用到的插件：[gulp-asset-rev](https://www.npmjs.com/package/gulp-asset-rev)。
预期效果是：
```
<script type="text/javascript" src="/assets/js/common.js?v=51921f3"></script>
```
#### 实现步骤
首先，下载`gulp-asset-rev`包。找到node_modules --> gulp-assets-rev -->index.js修改为以下代码：
```
var verStr = (options.verConnecter || "") + md5;
    src=src+"?v="+verStr;
```

#### 主要遇到的问题
因为项目里必须是绝对路径引入，但是绝对路径执行打包没有效果，百度了很久都没找到答案，使用场景基本上都是相对路径引入。然后，突然看到文档有写明绝对路径的配置。一定要认真看文档！一定要认真看文档（就算是英文）！
```
hashLen: length of hash version string
Type: Number default: 7

verConnecter: version connect char
Type: String default: '-'

rootPath: it should be assigned when the asset's path is an absolute path
Type: String default: ""

verStr: use custom version string
Type: String
```