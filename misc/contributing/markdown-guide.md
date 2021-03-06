# Markdown Guide

## Markdown Guide

This guide is inspired by GitHub's "Mastering Markdown" Guide, found [here](https://guides.github.com/features/mastering-markdown/).

### Background

Markdown is a simple way to format text for display on a website.

### Markdown Syntax

#### Headers

```text
# This is an <h1> tag
## This is an <h2> tag
###### This is an <h6> tag
```

## This is an \ tag

### This is an \ tag

**This is an \ tag**

#### Emphasis \(Bold, Italic\)

```text
*This text is italic*
_This is also italic_
```

_This text is italic_ _This is also italic_

```text
**This text is bold**
__This is also bold__
```

**This text is bold** **This is also bold**

```text
_You **can** also combine them_
```

_You **can** also combine them_

#### Lists

_Unordered_

```text
* Item 1
* Item 2
  * Item 2a
  * Item 2b
```

* Item 1
* Item 2
  * Item 2a
  * Item 2b

_Ordered_

You do not need to manually number your ordered list. Subsequent items in the list will be automatically numbered if you use `-` instead of numbers.

```text
1. Item 1
- Item 2
- Item 3
   1. Item 3a
   - Item 3b
```

1. Item 1
2. Item 2
3. Item 3
   1. Item 3a
   2. Item 3b

_Combined_

```text
1. Item 1
- Item 2
   - Sub-item
   - Sub-item
```

1. Item 1
2. Item 2
   * Sub-item
   * Sub-item

_Task Lists_

```text
- [x] first, choose an ordered or unordered list style, then add checkboxes
- [x] completed item
- [ ] incomplete item
```

* [x] first, choose an ordered or unordered list style, then add checkboxes
* [x] completed item
* [ ] incomplete item

#### Tables

You can create tables by assembling a list of words and dividing them with hyphens - \(for the first row\), and then separating each column with a pipe `|`:

```text
Column 1 Header | Column 2 Header
------------ | -------------
Content from cell 1 | Content from cell 2
Content in the first column | Content in the second column
```

| First Header | Second Header |
| :--- | :--- |
| Content from cell 1 | Content from cell 2 |
| Content in the first column | Content in the second column |

#### Strikethrough

```text
~~strikethrough text like this~~
```

~~strikethrough text like this~~

#### Images

Image syntax allows for alternative text. The format is `![alt text](URL)`. The URL can be a relative project path or an external website URL.

```text
![Org Logo](../logo_square.png)
![Org Logo](https://raw.githubusercontent.com/wendikristine/documentation-template/master/logo_square.png)
```

![Org Logo](../../.gitbook/assets/logo_square.png)

![Org Logo](https://raw.githubusercontent.com/wendikristine/documentation-template/master/logo_square.png)

#### Links

Links are created automatically in most cases \(and always on Github\). Or, you can specify a link with alternative text.

[http://github.com](http://github.com) - automatic!

```text
[GitHub](http://github.com) link
```

[GitHub](http://github.com) link

#### Block Quotes

```text
> "Not enough blinky lights."
> - Henry Neeman, SiPE 2018
```

> "Not enough blinky lights."  
> ~ Henry Neeman, SiPE 2018

#### Code

```text
I think you should use an
`<addr>` element here instead.
```

I think you should use an  
`<addr>` element here instead.

```text
mkdir lesson06/   
cd lesson06
```

Markdown supports language-specific syntax highlighting.

```javascript
function fancyAlert(arg) {
  if(arg) {
    $.facebox({div:'#foo'})
  }
}
```

```javascript
function fancyAlert(arg) {
  if(arg) {
    $.facebox({div:'#foo'})
  }
}
```

You can also simply indent your code by four spaces:

```text
function fancyAlert(arg) {
  if(arg) {
    $.facebox({div:'#foo'})
  }
}
```

#### Horizontal Rule

```text
---
```

#### Emoji

GitHub supports emoji! :sparkles: :camel: :boom:

To see a list of every image we support, check out the Emoji Cheat Sheet.

