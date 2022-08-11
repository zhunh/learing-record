## babel

1.核心库 @babel/core

2.CLI命令行工具 @babel/cli

在终端使用的工具。使用：

```js
./node_modules/.bin/babel src --out-dir lib
常用参数：
--plugins
--presets
```

plugins：代码转换功能插件

preset：一组预设插件

3.@babel/preset-env

```js
npm install --save-dev @babel/preset-env

./node_modules/.bin/babel src --out-dir lib --presets=@babel/env
```

### 配置

文件配置，babel.config.json（需要 `v7.8.0` 或更高版本）

```json
{
  "presets": [
    [
      "@babel/preset-env",
      {
        "targets": {
          "edge": "17",
          "firefox": "60",
          "chrome": "67",
          "safari": "11.1"
        }
      }
    ]
  ]
}
```



