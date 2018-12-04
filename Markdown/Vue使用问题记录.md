# Vue使用问题记录

## 1. vue动态定义图片路径
参考：[vue动态定义图片路径](https://www.jianshu.com/p/fab484498e4e)

## 2. webpack + pdfjs报错： window is not defined
参考：[Webpack+pdfjs 报错：window is not defined](https://blog.csdn.net/u010745620/article/details/80953951)
使用pdfjs库的时候，总是报错window is not defined, 几番查找资料并尝试后发现是webpack的问题，webpack打包有个配置项: output.globalObject 配置为"this" 即可避免该错误，该配置默认为"window", 然而webworker 中没有window对象，所以会报错。

正确的配置（部分）如下:
```js
// webpack.config.js
module.exports = {
    // 此处省略部分配置项
    output: {
        filename: '[name].js',
        path: path.resolve(__dirname, 'dist'),
        globalObject: "this"        // 关键在此项配置，需要配置为 "this", 默认为"window"
    },
    // 此处省略部分配置项
}
```