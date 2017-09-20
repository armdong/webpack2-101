# 快速开始
!> 在开始使用 `webpack` 之前，首先确保自己电脑上安装了最新稳定版本的 `Node`。可以通过 `node -v` 查看电脑上安装的 `Node` 版本。如果你成功安装了 `Node`，你可以在命令行工具中使用 `npm` 命令来进行相关开发。本人更倾向于使用 `Yarn` 命令来进行开发。

## 初始化项目
创建项目目录并初始化：以本项目为例（后续代码段都是以本项目为例）。
```bash
mkdir webpack2-101
cd webpack2-101
yarn init -y
```
运行完上述命令后，会创建一个名称为 `webpack2-101` 的文件夹，并在该文件夹根目录下生成一个 `package.json` 文件。

## 安装 Webpack 2
使用 `Yarn` 安装 `webpack`，截至到目前为止，`webpack` 已经发布到 `3.x.x` 了，所以我们安装 `webpack` 的时候，要指定版本号，否则默认会安装 `3.x.x` 的版本。最新的 `2.x.x` 版本是 `2.7.0`，所以需要执行下列命令安装 `2.7.0` 版本的 `webpack`：
```bash
yarn add webpack@2.7.0 --dev # --dev 表示开发依赖项
```

## 运行 Webpack 2
通过 `yarn add webpack@2.7.0 --dev` 命令安装完 `webpack` 后，`webpack` 会安装到项目根目录下的 `node_modules` 文件夹中。接下来我们还需要再做几件事然后运行 `webpack`：
1. 在项目根目录下新建一个 `src` 文件夹；
```bash
mkdir src
```
2. 在 `src` 文件夹下新建一个 `index.js` 文件;
```bash
touch ./src/index.js
```
并在 `index.js` 文件中加入以下代码：
```javascript
console.log('Hello Webpack 2!');
```
3. 运行 `node_modules/.bin/webpack ./src/index.js ./dist/index.js` 命令， `webpack`会动态生成一个与 `./src/index.js` 同名的 `js` 文件 `./dist/index.js`。

## 项目目录结构
到目前为止，我们的项目目录结构如下：
```text
-| webpack2-101
  -| dist
    -| index.js
  -| src
    -| index.js
  -| .gitignore
  -| LICENSE
  -| package.json
  -| README.md
```
