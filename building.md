# Setting installation directory

- autoconf: ./configure --prefix=/path/of/installation
- cmake: cmake -DCMAKE_INSTALL_PREFIX=/path/of/installation build_dir
- meson: meson setup --prefix=/path/of/installation build_dir

# Enabling language servers within nvim

See https://neovim.io/doc/user/lsp.html for the full reference.

## nvim configuration

Add something like this in your `init.lua` (example to use clangd for C and C++):

```
vim.api.nvim_create_autocmd(
    'FileType',
    {
        pattern = { 'c', 'cpp' },
        callback = function()
            vim.lsp.start({
                name = 'clangd',
                cmd = {'/usr/bin/clangd'},
                root_dir = vim.fs.dirname(
                    vim.fs.find({'compile_commands.json'}, {upward = true})[1]
                ),
            })
        end
    }
)
```

This will launch clangd when the current buffer type C or C++, with root directory being
the first upward directory containing a `compile_commands.json` file.
One can repeat this with other language servers.

## keybindings

[i-Ctrl-X Ctrl-O](https://neovim.io/doc/user/insert.html#i_CTRL-X_CTRL-O): Completion using omnifunc.

One can also use [the standard tags keybindings](https://neovim.io/doc/user/tagsrch.html#tag-commands):

- Ctrl-\] / Ctrl-t: Go to tag / return from tag.
- :[s]tj: Go to tag / split and go to tag.
- :tags: list tags
- etc.
 
## direct command

[:lua vim.lsp.buf.format()](https://neovim.io/doc/user/lsp.html#vim.lsp.buf.format\(\)): reformat the current buffer
etc.

