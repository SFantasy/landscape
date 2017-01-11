# DOM

DOM = Document Object Model

## Tricks

- 获取文档中所有的标签

```js
document.querySelectorAll('*')

// 或者
document.all
```

- 获取文档中使用到的标签名称

```js
[...new Set(Array.from(document.all).map(el => el.nodeName))]
```
