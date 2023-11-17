# Setup Neovim

[toc]



## MacOS

Download nevim via bew. The original neovim downloaded from brew does not support icon display.

```bash
brew install neovim
```

Download new font. 

```bash
brew tap homebrew/cask-fonts && brew install --cask font-fira-code-nerd-font
```

Open `iterm2`, `profiles -> open profiles -> edit profiles -> Text -> Use a different font -> FiraCode Nerd Font`



### Package Manger

Use [**Lazy.nvim**](https://github.com/LazyVim/LazyVim/blob/main/README-CN.md) as the package manager.  Make directory to store nvim configuration information.

```bash
cd ~/.config
mkdir nvim
```

Clone the starter.

```bash
git clone https://github.com/LazyVim/starter ~/.config/nvim
```

Delete `.git` file for further personal storage.

```bash
rm -rf ~/.config/nvim/.git
```

The file directory of `~/.config/nvim` should be like below.

<pre>
  ~/.config/nvim
├── lua
│   ├── config
│   │   ├── autocmds.lua
│   │   ├── keymaps.lua
│   │   ├── lazy.lua
│   │   └── options.lua
│   └── plugins
│       ├── spec1.lua
│       ├── **
│       └── spec2.lua
└── init.lua
</pre>



### PlugIns

#### [1. Nvim-tree](https://github.com/nvim-tree/nvim-tree.lua)

> Side bar file explorer

Lua files under the directory of `./plugins` , for each plugin, it should have a `.lua` file to store related operations.

```bash
cd ~/.config/nvim/plugins
touch nvim-tree.lua
```

Paste the following lines of code into it.

```lua
return {
  "nvim-tree/nvim-tree.lua",
  version = "*",
  lazy = false,
  dependencies = {
    "nvim-tree/nvim-web-devicons",
  },
  config = function()
    require("nvim-tree").setup {}
  end,
}
```

After that, open the `init.lua` file

```bash
nvim ~/.config/nvim/init.lua
```

Copy the content into it.

```lua
-- disable netrw at the very start of your init.lua
vim.g.loaded_netrw = 1
vim.g.loaded_netrwPlugin = 1

-- set termguicolors to enable highlight groups
vim.opt.termguicolors = true

-- empty setup using defaults
require("nvim-tree").setup()

-- OR setup with some options
require("nvim-tree").setup({
  sort_by = "case_sensitive",
  view = {
    width = 30,
  },
  renderer = {
    group_empty = true,
  },
  filters = {
    dotfiles = true,
  },
})
```

##### Basic Commands


See [:help nvim-tree-commands](doc/nvim-tree-lua.txt)

Basic commands:

`:NvimTreeToggle` Open or close the tree. Takes an optional path argument.

`:NvimTreeFocus` Open the tree if it is closed, and then focus on the tree.

`:NvimTreeFindFile` Move the cursor in the tree for the current buffer, opening folders if needed.

`:NvimTreeCollapse` Collapses the nvim-tree recursively.





#### 2. [ToggleTerm](https://github.com/akinsho/toggleterm.nvim)

> terminal inside neovim 

```bash
cd ~/.config/nvim/plugins
touch ToggleTerm.lua
```

copy into it

``` lua
return
  -- amongst your other plugins
  {'akinsho/toggleterm.nvim', version = "*", config = true}
 
```



Open `init.lua` file and copy into it. Configurations should be put in the setup()

```bash
require("toggleterm").setup()
```





#### 3. [YouCompleteMe](https://github.com/ycm-core/YouCompleteMe)

> 

