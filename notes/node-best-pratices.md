<!--
 * @LastEditors: Tao Yang
 * @Description: 暂无描述
 * @FilePath: /front-end-best-pratices/notes/node-best-pratices.md
 * @Date: 2022-11-19 20:18:31
 * @LastEditTime: 2022-11-20 13:29:41
 * @Author: Tao Yang
-->

[TOC]

## 1. 项目结构实践

### 1.1 组件式构建你的解决方案

### 1.2 分层设计组件，保持 Express 在特定的区域

- 将组件代码分成 web, services, DAL 层

### 1.3 封装公共模块成为 NPM 的包

### 1.4 分离 Express 'app' and 'server'

### 1.5 使用易于设置环境变量，安全和分级的配置（[nconf](https://www.npmjs.com/package/nconf), [config](https://www.npmjs.com/package/config) 和 [convict](https://www.npmjs.com/package/convict)）

## 2. 错误处理最佳实践

### 2.1 使用 Async-Await 和 promises 用于异步错误处理，避免使用回调

### 2.2 仅使用内建的错误对象

### 2.3 区分运行错误和程序设计错误

### 2.4 集中处理错误，不要在 Express 中间件中处理错误

## 索引

- [Node.js 最佳实践](https://github.com/goldbergyoni/nodebestpractices/blob/master/README.chinese.md)
