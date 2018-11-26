---
title: js 初识
tags: js 初识
notebook: js 初识
---
# js初识
## javascript 在世界中常规用途
 - 行为交互: 根据用户的操作行为去做出一些相应的反馈
- 数据交互: 在前后端之间进行数据的传输
- 逻辑交互: 根据目前不同的状态，去做出一些不同的事 情
## javascript组成部分
  - ECMAscript （js的核心：语法，计算，数据类型，流程语句 .....）
  - DOM (Document Object Model) 文档对象模型 （对页面文档的相关操作）
  - BOM (Browers Object Model) 浏览器对象模型 （对浏览器相关操作）
## javascript书写位置
  - 行间 <br>
    `
    <input type="button" onclick="alert(1);" value = "click">
    `<br>
    优点：直接，简单明了<br>
 	缺点：可读性差，不易维护，不易扩展
 - 内部<br>
 `  <script>
    alert(1);
    </script>
 `<br>
    优点： js和html分离，可以复用代码<br>
    缺点：代码不能多文件使用
 - 外部<br>
    `
        <script src=""></script>
    `<br>
    优点：多文件共用
## 注释
- 单行注释 //注释掉的内容
- 多行注释 /* 注释掉的内容 */
## 标识符
  标识符：变量名，常量名，函数名，函数参数名，对象属性名的统称
### 标识符的命名规则
 - 由数字，字母，下划线和美元符（$）组成
 - 首字符不能使用数字
 - 不能使用js的关键字和保留字
### 关键字和保留字
 - 关键字： js 本身已经使用了的单词
 - 保留字： js 觉得自己将来有可能会使用的单词
### 驼峰命名
 - 小驼峰命名：从第二个单词开始，首字母大写
 - 大驼峰命名：从第一个单词开始，首字母大写 
## console
 浏览器自带的调试工具，可以方便的调试 HTML，js，网络，性能 F12打开
 console
    全局对象，向控台输出内容
    console.log(值)
    console.dir
## undefined 和 null
  - undefined 未定义： 通常发生在变量声明了但是没有赋值或者对象的属性不存在的时候
  - null 空对象： 通常出现在元素未找到时
     - null不能进行属性操作