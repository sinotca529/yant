# lazy.nvim

[lazy.nvim](https://github.com/folke/lazy.nvim) はプラグインマネージャです。
プラグインのインストールや更新を便利にしてくれます。
また、プラグインの遅延読み込みを簡単に設定することができます。

## 基本的な使い方

次のようなディレクトリ構造を作ります。

```txt
.
├── init.lua
└── lua
   ├── general.lua
   ├── plugin.lua  # プラグインマネージャの設定
   └── plugin      # 各プラグインの設定を置くディレクトリ
     ├── nvim-treesitter.lua
     ├── ...
     └── color-scheme.lua
```

`plugin.lua` は次のようにします。

```lua
-- lazy.nvim が存在しないならインストールする
local lazypath = vim.fn.stdpath('data') .. '/lazy/lazy.nvim'
if not vim.loop.fs_stat(lazypath) then
    local lazy_repo = 'https://github.com/folke/lazy.nvim.git '
    vim.api.nvim_command('!git clone --filter=blob:none --branch=stable ' .. lazy_repo .. lazypath)
end
vim.opt.rtp:prepend(lazypath)

require('lazy').setup(
    -- プラグイン設定のリスト
    {
        require('plugin.nvim-treesitter'),
        -- ...
        require('plugin.color-scheme'),
    },
    -- lazy.nvim 自体の設定 (省略可)
    {
        ui = {
            border = 'rounded'
        },
    }
)
```

`lua/plugin` 以下に配置したファイルには、各プラグインの設定を書きます。

## 遅延読み込み

Neovim の起動時に読み込まれるプラグインが多いほど、当然 Neovim の起動は遅くなります。
この問題は、 (起動時ではなく) 必要になった時に始めてプラグインを読み込むことで緩和できます。

例として、閉じカッコを自動補完するプラグインを考えましょう。
文字入力を行わない Normal モードではカッコの補完は必要ありません。
このプラグインが必要になるのは始めて Insert モードに移行したあとです。
このような場合は、 `event = 'InsertEnter'` と書くことで Insert モードへの移行時までプラグインの読み込みを遅らせることができます。

```lua
return {
    'windwp/nvim-autopairs',
    event = 'InsertEnter',
    opts = {} -- this is equalent to setup({}) function
}
```

他にも、特定のキーを押したタイミングや特定のコマンドを実行したタイミングにプラグインが読み込まれるような設定を書くことができます。詳しくは [lazy.nvim の README](https://github.com/folke/lazy.nvim/blob/main/README.md) や、 `:help lazy.nvim.txt` を参照してください。
