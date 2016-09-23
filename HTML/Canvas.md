# Canvas

**内容**

<!-- toc -->

## 多行文本的展示

Canvas 本身没有办法处理带换行字符的文本，例如这样的：`This is \n a paragraph \n ...`

解决方案，分割字符串后循环在 Canvas 上进行 `fillText`：

```js
function wrapText (text, x, y, size) {
  var textArray = text.split('\n');
  textArray.forEach(text => {
    ctx.fillText(text, x, y);
    y += size;
  });
}
```

## TIPS

- 载入图片需要使用 `onload` 方法

```js
img.onload = e => {
  ctx.drawImage(img, x, y, width, height);
}
```

- 清除 Canvas 内容

```js
ctx.clearRect(0, 0, canvas.width, canvas.height);
```

## 参考资料

- [Canvas cheat sheet](https://simon.html5.org/dump/html5-canvas-cheat-sheet.html)
