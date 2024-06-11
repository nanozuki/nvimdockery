# vimdockery

A tool to help you write vim help doc. The syntax is inspired by typst.

## Syntax

**Headers**

```
= Header 1
== Header 2
```

**Leading**

```
#set leading(8)

This is a paragraph with leading.
```

**Function**

A doc for a function.

```
#function("nvim_create_augroup({name}, {opts})",
  intro[
    Create or get an autocommand group |autocmd-groups|.

    To get an existing group id, do: >lua
        local id = vim.api.nvim_create_augroup("MyGroup", {
            clear = false
        })
  ],
  paramter(name, string)[The name of the group]
  paramter(opts, dictionary)[
    - clear (bool) optional: defaults to true. Clear existing
      commands if the group already exists |autocmd-groups|.
  ],
  return(number)[id of the created group]
)
```

**link**

```
#hyperlink("https://typst.app/docs/reference/model/link/")["typst reference"]
#help("autocmd-groups")
#tag("plugin-tag-name")
#option("option-name")
```

**meta**

```
#plugin(plugin-name)[short description]
```
