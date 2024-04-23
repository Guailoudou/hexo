---
title: js笔记
date: 2024-03-01 23:15:21
tags:
- 日志
- 学习
---
- 网页在全屏之间切换
```JavaScript
function toggleFullScreen() {
    if (document.fullscreenElement) {
        document.exitFullscreen();
    } else {
        document.documentElement.requestFullscreen();
    }
}
```



### js事件

`addEventListener('事件',函数)`为添加页面事件监听

```JavaScript
window.onload = function(){
    //页面加载完毕后执行
}
```

```JavaScript
window.addEventListener('resize', function() {
    console.log('窗口大小已改变');
});

const width = window.innerWidth;
const height = window.innerHeight;
console.log(`页面宽度: ${width}px`);
console.log(`页面高度: ${height}px`);

const totalWidth = document.documentElement.clientWidth;
const totalHeight = document.documentElement.clientHeight;
console.log(`文档总宽度: ${totalWidth}px`);
console.log(`文档总高度: ${totalHeight}px`);
```


- click：当用户点击某个元素时触发。
```javascript
element.addEventListener('click', function() {
  // 事件处理代码
});
```
- dblclick：当用户双击某个元素时触发。
```javascript
element.addEventListener('dblclick', function() {
  // 事件处理代码
});
```
- mouseover：当鼠标指针移动到某个元素上方时触发。
```javascript
element.addEventListener('mouseover', function() {
  // 事件处理代码
});
```
- mouseout：当鼠标指针离开某个元素时触发。
```javascript
element.addEventListener('mouseout', function() {
  // 事件处理代码
});
```
- mousemove：当鼠标指针在元素上移动时触发。
```javascript
element.addEventListener('mousemove', function(event) {
  // event.clientX 和 event.clientY 可以获取鼠标的位置
});
```
- mousedown：当鼠标按钮被按下时触发。
```javascript
element.addEventListener('mousedown', function(event) {
  // event.button 可以获取被按下的鼠标按钮
});
```
- mouseup：当鼠标按钮被释放时触发。
```javascript
element.addEventListener('mouseup', function(event) {
  // event.button 可以获取被释放的鼠标按钮
});
```
- keypress：当键盘上的键被按下并释放时触发。
```javascript
element.addEventListener('keypress', function(event) {
  // event.key 可以获取被按下的键
});
```
- keydown：当键盘上的键被按下时触发。
```javascript
element.addEventListener('keydown', function(event) {
  // event.key 可以获取被按下的键
});
```
- keyup：当键盘上的键被释放时触发。
```javascript
element.addEventListener('keyup', function(event) {
  // event.key 可以获取被释放的键
});
```
- change：当元素的值发生变化时触发，如 `<input>`, `<textarea>`, 和 `<select>` 元素。
```javascript
element.addEventListener('change', function() {
  // 事件处理代码
});
```
- focus：当元素获得焦点时触发，如用户点击输入框或使用Tab键导航到元素。
```javascript
element.addEventListener('focus', function() {
  // 事件处理代码
});
```
- blur：当元素失去焦点时触发。
```javascript
element.addEventListener('blur', function() {
  // 事件处理代码
});
```

- submit：当表单提交时触发。
```javascript
formElement.addEventListener('submit', function(event) {
  event.preventDefault(); // 阻止表单的默认提交行为
  // 事件处理代码
});
```
