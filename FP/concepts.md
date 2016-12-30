# Concepts

整理一些函数式编程中的概念：

<!-- toc -->

## Pure Function

Pure Function，直译一下就是「纯函数」。

Pure Function 的概念很简单，也许你看到这个名词就已经明白这篇文章的主旨了 -- 但我还是需要通俗地解释（科普）一下，毕竟这只是起点而已。

**1. 在给定同样的参数的前提下，Pure Function 都会返回同样的结果。**

例如：

```js
function incresae(n) {
  return n + 1;
}
```

increase 函数的返回值总是在入参 n 的基础上增加 1。

这看起来十分合乎逻辑，但我们的程序肯定没有那么简单，现在我们改写一下 increase 函数：

```js
var  number = 1;

function increase(n) {
  return n + number;
}
```

你一定发现了，increase 函数现在的返回值是由入参 n 和外部定义的一个变量「计算」所得的。

如果我们的程序里有另一个函数：

```
function doubleNumber(number) {
  return number * 2;
}
```

我想你一定知道我要表达的意思了：Fure Function 的返回值，只能由其函数入参所决定，而不能有其他的干扰因素（比如这里的变量 `number`）。

**2. Pure Function 在计算返回值的时候不会产生 Side Effect **

所谓 Side Effect 就是我们在平时经常做的一些工作，例如：I/O 操作，修改函数入参或函数外部的变量，抛出异常等。

就 JavaScript 而言，我们常用的 `console.log()` 函数 -- 会输出内容到控制台，用来生成随机数的 `Math.random()` -- 会改变全局的 seed，这实在是太多太多了。

你可以大概在脑海里列举一下你所熟悉语言中那些会产生 Side Effect 的操作。

套用一个句式：

会产生 Side Effect 的 Function 不是真正的 Pure Function 。

可以想象的是，Pure Function 有很多的优点，例如：

每个 Pure Function 的运行结果都是可重现的。这样的好处就是 Pure Function 十分容易进行测试 -- 因为这完全是一个透明的盒子。

## High Order Function

在数学与计算机科学中，所谓「高阶函数」就是：

- 把函数作为其参数传入
- 返回值为一个函数
