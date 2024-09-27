
# Webpack入门

本指南介绍如何使用Webpack和pnpm设置一个基本的React项目

## 项目设置

1. 创建项目并初始化:
   ```
   mkdir my-react-project
   cd my-react-project
   pnpm init
   ```

2. 安装依赖:
   ```
   pnpm add react react-dom
   pnpm add -D webpack webpack-cli webpack-dev-server babel-loader @babel/core @babel/preset-env @babel/preset-react html-webpack-plugin
   ```

3. 创建Webpack配置文件 `webpack.config.js`

4. 创建源文件:
   - `src/index.html`
   - `src/index.js`
   - `src/App.js`

5. 在 `package.json` 中添加脚本:
   ```json
   "scripts": {
     "start": "webpack serve --mode development",
     "build": "webpack --mode production"
   }
   ```

## Webpack配置解析

### 模块规则(Module Rules)

```javascript
module: {
  rules: [
    {
      test: /\.js$/,
      exclude: /node_modules/,
      use: {
        loader: 'babel-loader',
        options: {
          presets: ['@babel/preset-env', '@babel/preset-react']
        }
      }
    }
  ]
}
```

- `test: /\.js$/`: 匹配所有.js文件
- `exclude: /node_modules/`: 排除node_modules目录
- `use: { loader: 'babel-loader', ... }`: 使用babel-loader处理匹配的文件
- `options`: 配置Babel预设,用于转换现代JavaScript和JSX

### 插件(Plugins)

```javascript
plugins: [
  new HtmlWebpackPlugin({
    template: './src/index.html'
  })
]
```

`HtmlWebpackPlugin` 的作用:
- webpack专注于js的解析，因此需要插件帮助生成HTML文件

## 关键概念

1. **Loaders**: 让Webpack能够处理非JavaScript文件（如CSS、图片等）。

2. **Plugins**: 执行范围更广的任务,如打包优化、资源管理、环境变量注入等。

3. **babel-loader**: 使用Babel转换JavaScript文件,使其兼容更多浏览器。

4. **HtmlWebpackPlugin**: 简化HTML文件的创建,自动引入打包资源。

## 使用说明

- 开发模式: `pnpm start`
- 生产构建: `pnpm run build`



