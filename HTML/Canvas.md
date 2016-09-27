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

## 使用图片

- 载入图片需要使用 `onload` 方法

```js
img.onload = e => {
  ctx.drawImage(img, x, y, width, height);
}
```

## 转换为图片格式

```js
var canvas = document.getElementById('canvas');
canvas.toDataURL('image/png', 1);
```

### 安全问题

在使用 `toDataURL` 和 `toBlob` 方法将 Canvas 转换为图片的时候会产生一个安全问题：

```
Uncaught SecurityError: Failed to execute 'toBlob' on 'HTMLCanvasElement': Tainted canvases may not be exported.
```

造成这个问题的原因是在 Canvas 中请求并渲染了来自不同域的图片，浏览器不允许再通过 Canvas 的方法转换为图片。

要解决这个问题，可以把图片内容经过同域的服务进行中转。

## 其他

- 清除 Canvas 内容

```js
ctx.clearRect(0, 0, canvas.width, canvas.height);
```

## 参考资料

- [Canvas cheat sheet](https://simon.html5.org/dump/html5-canvas-cheat-sheet.html)
