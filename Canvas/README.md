# Canvas

**内容**

<!-- toc -->

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
