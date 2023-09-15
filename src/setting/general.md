# 汎用設定

まずは一般的な設定をしましょう。
設定ファイルは、ディレクトリ `~/.config/nvim` 以下に配置します。
次のようなディレクトリ構造を作りましょう。

```txt
.
├── init.lua         # 設定のエントリポイント
└── lua
   └── general.lua   # 汎用設定
```

## `init.lua`

`init.lua` は neovim の設定のエントリとなるファイルです。
ここでは `general.lua` の読み込みを行います。

```lua
vim.loader.enable()  -- 設定の読み込みを高速化
require('general')   -- general.lua を読み込む
```

## `general.lua`

`general.lua` には一般的な設定を書きます。

```lua
-- 行番号を表示
vim.o.number = true
-- ファイルエンコーディングを指定
vim.o.fenc = 'utf-8'
-- TODO
```
