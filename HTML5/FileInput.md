FileInput
---

基础代码

```html
<input type="file" id="file">
```

```js
var file = document.getElementById('file')
```

### 如何获取选择的文件

```js
file.files
```

### 事件监听

```js
file.onchange = function (e) {
  var files = e.target.files
}
```
