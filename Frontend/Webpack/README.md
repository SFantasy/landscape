# Webpack

在使用 Webpack 之前，可以先阅读以下这份文档：[webpack-howto](https://github.com/petehunt/webpack-howto/blob/master/README-zh.md) 来了解一下与 Webpack 相关的内容。

## 如何实现目录文件的整体打包

配合 gulp 以及一些插件使用，不需要对每个页面的文件配置 entry

示例：

```js
var gulp = require('gulp')
var webpack = require('webpack-stream')
var named = require('vinyl-named')
var rename = require('gulp-rename')

gulp.task('default', function () {
  var tmp = {};
  return gulp.src(['src/*.js', 'src/**/*.js'])
    .pipe(named())
    .pipe(rename(function (path) {
      tmp[path.basename] = path
    }))
    .pipe(webpack({
      output: {
        filename: '[name].bundle.js'
      }
    }))
    .pipe(rename(function (path) {
      path.dirname = tmp[path.basename].dirname
    }))
    .pipe(gulp.dest('dist/'))
})
```
