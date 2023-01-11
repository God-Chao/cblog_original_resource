---
title: vue基础
category: 笔记
tags:
  - vue
banner_img: /img/banner/vue.jpg
index_img: /img/cover/vue.jpg
excerpt: vue的基本指令以及vue2.0脚手架知识
date: 2022-12-01 12:52:02
---
## 1.指令

**v-text**
设置元素的文本值
```html
<p v-text="aaa"></p>
等价于
<p>aaa</p>
```

**v-html**
与v-text用法一致，只是内容可以嵌套html语句

**v-on**
绑定事件
```html
<input type="button" @click="fun">
```

**v-show**
根据表达式的真假，切换元素的显示和隐藏
```html
<img src="xxx" v-show="age>=18">
```

**v-if**
跟v-show用法一致

**v-bind**
设置元素的属性（比如src，title，class）
```html
<img :src="imgSrc" :class="{active:isActive}">
```

**v-for**
根据数据生成列表结构
```html
<li v-for="item in arr">
<li v-for="(item,index) in arr">
```

**v-model**
获取和设置表单元素的值（双向数据绑定）
```html
<input type="text" v-model="message">
```

## 2.模板

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Vue</title>
    <!-- 导入vue -->
    <script src="https://cdn.jsdelivr.net/npm/vue@2/dist/vue.js"></script>
</head>

<body>
    <div id="app">
      
    </div>
    <script>
        var app = new Vue({
            el: "#app",
            data: {
                num: 1
            },
            methods: {
                fun: function () {
                  
                }
            }
        })
    </script>
</body>

</html>
```

## 3.脚手架

**创建脚手架工程**
```bash
# npm下载vue脚手架
$ npm install @vue/cli

# 创建vue工程
$ vue create 项目名称

# 开启服务
$ npm run serve

# 查看vue的默认配置
$ vue inspect > output.js
```

**修改默认配置**
```bash
# 查看vue的默认配置
vue inspect > output.js

# 在vue.config.js中修改配置
# 在 https://cli.vuejs.org/zh/config/ 中查找配置

# 关闭语法检查
lintOnSave: false
```

**部署**
```bash
# 打包
npm run build
```