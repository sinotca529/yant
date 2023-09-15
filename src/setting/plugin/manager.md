# プラグインマネージャ

プラグインの管理には [lazy.nvim](https://github.com/folke/lazy.nvim) を使います。

次のようにディレクトリ構造を更新しましょう。

```txt
.
├── init.lua
└── lua
   ├── general.lua
   ├── plugins.lua        # プラグインマネージャの設定
   └── plugin             # 各プラグインの設定を置くディレクトリ
     └── color-scheme.lua # カラースキームプラグインの設定
```

設定を以下のように更新・編集し、 Neovim を(再)起動すると次が行われます。

- `lazy.nvim` のインストール
- カラースキームのインストールと適用

## `init.lua`

`plugins.lua` を読み込むために、 `init.lua` を次のように書き換えます。

```lua
vim.loader.enable()  -- 設定の読み込みを高速化
require('general')   -- general.lua を読み込む
require('plugins')   -- plugins.lua を読み込む
```

## `plugins.lua`

`lazy.nvim` にプラグインの設定をわたします。

```lua
-- lazy.nvim が存在しないならインストールする
local lazypath = vim.fn.stdpath('data') .. '/lazy/lazy.nvim'
if not vim.loop.fs_stat(lazypath) then
    local lazy_repo = 'https://github.com/folke/lazy.nvim.git '
    vim.api.nvim_command('!git clone --filter=blob:none --branch=stable ' .. lazy_repo .. lazypath)
end
vim.opt.rtp:prepend(lazypath)

require('lazy').setup({
    -- カラースキームプラグインの設定を読み込む
    require('plugin.color-scheme')
})
```

## `color-scheme.lua`

試しに、カラースキームを入れてみましょう。
ここでは [gruvbox-material](https://github.com/sainnhe/gruvbox-material) を使います。

```lua
return {
    -- インストールするプラグインがある github のユーザ名とリポジトリ名
    'sainnhe/gruvbox-material',
    -- プラグインの読み込み時に実行する処理
    config = function()
        -- カラースキームを設定
        vim.cmd.colorscheme('gruvbox-material')
    end,
}
```