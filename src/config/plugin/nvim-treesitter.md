# nvim-treesitter

[nvim-treesitter](https://github.com/nvim-treesitter/nvim-treesitter) は構文解析系のプラグインです。
デフォルトの解析よりも詳細な解析により、シンタックスハイライト等が強化されます。

## 設定例

```lua
-- lua/plugin/nvim-treesitter.lua

return {
    'nvim-treesitter/nvim-treesitter',
    config = function()
        require('nvim-treesitter.configs').setup({
            ensure_installed = {
                'c', 'cpp', 'llvm', 'rust',
                'lua', 'python',
                'markdown', 'markdown_inline',
                'latex',
            },
            auto_install = true,
            highlight = {
                enable = true,
            }
        })
    end
}
```
