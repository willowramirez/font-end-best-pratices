<!--
 * @LastEditors: Tao Yang
 * @Description: 暂无描述
 * @FilePath: /front-end-best-pratices/notes/naming-cheatsheet.md
 * @Date: 2022-11-19 15:15:04
 * @LastEditTime: 2022-11-19 19:24:09
 * @Author: Tao Yang
-->

[TOC]

## 使用英语

## 命名约定

选择一个命名约定并遵循它，camelCase, PascalCase, snake_case

## 标识符（S-I-D）

- 短（Short）
- 直观（Intuitive）
- 描述性的（Descriptive）：以最有效的方式反映它的作用/拥有的东西

## 避免使用缩写

## 避免上下文重复

## 反映预期结果

## 函数命名

### A/HC/LC 模式

```
prefix? + action (A) + high context (HC) + low context? (LC)
```

| 函数名                 |   前缀   | 动作（A） | 高语境（HC） | 低语境（LC） |
| :--------------------- | :------: | --------- | ------------ | ------------ |
| `getUser`              |          | `get`     | `User`       |              |
| `getUserMessages`      |          | `get`     | `User`       | `Messages`   |
| `handleClickOutside`   |          | `handle`  | `Click`      | `Outside`    |
| `shouldDisplayMessage` | `should` | `Display` | `Message`    |              |

#### 动作：描述函数的作用

- get：立即访问数据
- set：以声明方式设置变量
- reset：将变量设置回其初始值或状态。
- remove：从某处移除某物
- delete：从存在领域彻底抹去某些东西。`add(need a destination)/remove create(require no destination)/delete`
- compose：从现有数据创建新数据。主要适用于字符串、对象或函数。
- handle：处理一个动作。通常在命名回调方法时使用。

#### 语境：函数运行的域

#### 前缀：前缀增强了变量的含义。它很少用在函数名中。

- is：描述当前上下文的特征或状态（通常为 boolean）。
- has：描述当前上下文是否拥有某个值或状态（通常为 boolean）。
- should：反映了一个肯定的条件语句（通常是 boolean）加上一个特定的动作。
- min/max：表示最小值或最大值。在描述边界或限制时使用。
- prev/next：指示当前上下文中变量的前一个或下一个状态。在描述状态转换时使用。

### 单数和复数：取决于它们是单个值还是多个值。

## 索引

- [Naming CheatSheet](https://github.com/kettanaito/naming-cheatsheet)

---

### 我们不是唯一阅读我们代码的人

### 我们的心情与我们正在写的代码无关

### 人类读我们的代码，而不是电脑

### 在写完代码之后对它进行阅读
