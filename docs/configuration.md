# 搭建 Webpack 配置项

## 添加组件
如果只在命令行中打印 `Hello Webpack 2!!!` 的话，我们无法体验到 `webpack` 和 `javascript` 的威力。接下来，我们在 `src` 文件夹下面新建一个 `component.js` 文件，从页面中输出点东西。

** ./src/component.js **
```javascript
export default (text='Hello Webpack 2') => {
  const element = document.createElement('div');
  element.innerHTML = text;
  return element;
};
```

接下来，我们在 `./src/index.js` 文件中引入刚刚编写的组件：

** ./src/index.js **
```javascript
import component from './component';
document.body.appendChild(component());
```

## 添加 Webpack 配置文件
第一步，新建 `webpack` 配置文件。在项目根目录下新建 `webpack.config.js`，该文件用于管理 `webpack` 的各种配置项。
```bash
touch webpack.config.js
```

第二步，安装 `html-webpack-plugin` 插件。`HtmlWebpackPlugin` 插件会自动生成 `index.html` 文件，并且自动将生成的 `js` 文件动态的以 `script` 标签引入到生成的页面中。

使用 `yarn add html-webpack-plugin --dev` 命令进行安装，安装成功后，会在项目根目录的 `package.json` 文件中的 `devDependencies` 节点下面显示：
```bash
yarn add html-webpack-plugin --dev
```

第三步，编写 `webpack.config.js` 配置项：

** webpack.config.js **
```javascript
const path = require('path');
const HtmlWebpackPlugin = require('html-webpack-plugin');

const PATHS = {
  src: path.join(__dirname, 'src'),
  dist: path.join(__dirname, 'dist'),
};

module.exports = {
  entry: {
    index: PATHS.src,
  },
  output: {
    path: PATHS.dist,
    filename: '[name].js',
  },
  plugins: [
    new HtmlWebpackPlugin({
      title: 'Webpack 2 from scratch',
    }),
  ],
};
```

第四步，运行 `webpack` 命令，这次我们只要在命令行中执行 `node_modules/.bin/webpack` 就可以了，因为我们已经在 `webpack.config.js` 中做了相关配置，例如 `entry` 和 `output` 选项。但是如果每次都要在命令行中输入 `node_modules/.bin/webpack` 命令的话，未免显得太繁琐且容易出现拼写错误。所以，接下来，我们会在 `package.json` 文件中配置 `node` 命令，从而简化在命令行中的命令输入：

** package.json **
```json
"scripts": {
  "build": "webpack"
}
```
这样的话，我们在命令行中只要输入 `yarn build` 就可以执行 `webpack` 命令了。
