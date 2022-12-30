---
coverY: 0
---

# 🌰 cheatsheet

#### 通用原则

- 别想着过早的优化代码。先得保证它们可读有可理解才行。
- 在任何代码库中，无论有多少人参与及贡献，所有代码都应该如同一个人编写的一样。
- 严格执行一致认可的风格。
- 如果有疑议，则使用现有的、通用的模式。

#### 格式

- 在多个选择器的规则集中，每个单独的选择器独占一行。
- 在规则集的左大括号前保留一个空格。
- 在声明块中，每个声明独占一行。
- 每个声明前保留一级缩进。
- 每个声明的冒号后保留一个空格。
- 对于声明块的最后一个声明，始终保留结束的分号。
- 规则集的右大括号保持与该规则集的第一个字符在同一列。
- 每个规则集之间保留一个空行。

#### 声明顺序

```css
.selector {
  /* Positioning */
	position
	z-index
	top / right / bottom / left

  /* Display & Box Model */
	display
	overflow
	box-sizing
	width / height
	margin / padding
	border
  /* Other */
	background
	color
	font
}
```

### 索引

- [编写如一、符合习惯的 CSS 的原则](https://github.com/necolas/idiomatic-css/tree/master/translations/zh-CN)
