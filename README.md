# vimdockery

A tool to help you write vim help doc. The syntax is inspired by typst.

## Syntax

**Render Switch**

```
#par(ignore-vimdoc:true)[
  this is a paragraph only appears in markdown.
]
#par(ignore-markdown:true)[
  this is a paragraph only appears in vimdoc.
]
```

**Title**

```
#title[Document Title]
```

Generated markdown:

```markdown
# Document Title
```

Generated vimdoc:

```vimdoc
filename.txt                                                     Document Title
```

**Headers**

```
= Header 1
== Header 1.1
=== Section 1.1.1
```

Generated markdown, markdown's level-1 header is reserved for the document title:

```markdown
## Header 1

### Header 1.1

#### Section 1.1.1
```

Generated vimdoc, level 3 headers won't be uppercase, and won't in the table of
contents:

```vimdoc
===============================================================================
1. Header 1                                                 *myplugin-header-1*

HEADER 1.1                                                *myplugin-header-1.1*

Section 1.1.1                                          *myplugin-section-1.1.1*
```

**Indent**

```
#par(indent: 8)

This is a paragraph with indent.
```

Generated markdown:

```markdown
        This is a paragraph with indent.
```

Generated vimdoc:

```vimdoc
        This is a paragraph with indent.
```

**List**

```
+ Item 1
+ Item 2
  - Item 2.1
  - Item 2.2
```

Generated markdown:

```markdown
1. Item 1
2. Item 2
   - Item 2.1
   - Item 2.2
```

Generated vimdoc:

```vimdoc
1. Item 1
2. Item 2
    - Item 2.1
    - Item 2.2
```

**table**

**Definition**

Infer a definition from annotations in lua code. Annotations must start with
three dashes `---`.

```
#def(fun: math.add)
```

Generated markdown:

```markdown
<a name="myplugin-math.add()"><strong>myplugin-math.add()</strong></a>

Add two numbers.

Parameters:

- `left` (number) The left operand.
- `right` (number) The right operand.

Return:

- (number) The sum of the two numbers.
```

Generated vimdoc:

```vimdoc
add({left}, {right})                                       *myplugin-math.add()*
  Add two numbers.

  Parameters: ~
    - {left}   (number) The left operand.
    - {right}  (number) The right operand.

  Return: ~
    (number) The sum of the two numbers.
```

The definition type include

- `fun` for function: `@param`, `@return`
- `class` for class: `@class`, `@field`
- `alias` for alias: `@alias`
- `enum` for enum: `@enum`

If there are addtional information, you can add it like this:

```
#def(fun: math.add)[
  This is a function to add two numbers.
]
```

**link**

```
#link("https://typst.app/docs/reference/model/link/")["typst reference"]
#image("https://typst.app/docs/assets/typst-logo.svg")[typst logo]
#tag(autocmd-groups)
#opt(option-name)
#cmd(:filetype)
```

If `#tag` in separate line, it will create a tag. Otherwise, it will is a
hot-link to the tag.

**table**

```
#table(
  columns: 3,
  table.header(["opt"], ["description"]),
  [opt1]
  [description1]
  [opt2]
  [description2]
  [opt3]
  [
    description3
    with
    multiple
    lines
  ]
)
```
