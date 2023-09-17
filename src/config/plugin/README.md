# プラグイン

プラグインを利用して Neovim の機能を拡張しましょう。

## 入れておきたいプラグイン

筆者の独断と偏見で、とりあえず入れておきたいプラグインを列挙しました。
カッコの補完やカーソル移動の強化など、便利なプラグインは他にも沢山ありますから、必要に応じて入れていきましょう。

### 見た目

| プラグイン      | 説明                                         |
| --------------- | -------------------------------------------- |
| nvim-treesitter | 構文解析によるシンタックスハイライト等の強化 |
| lualine.nvim    | ステータスバーの強化                         |

### LSP ・フォーマッタ・リンタ

| プラグイン           | 説明                                                  |
| -------------------- | ----------------------------------------------------- |
| nvim-lspconfig       | LSP client の設定                                     |
| mason.nvim           | LSP client, リンタ, フォーマッタ等のインストーラ      |
| mason-lspconfig.nvim | mason.nvim で入れた LSP を nvim-lspconfig で設定      |
| null-ls.nvim         | LSP client でないものを LSP client として使えるように |
| mason-null-ls.nvim   | mason.nvim で入れたリンタ等を null-ls.nvim で設定     |

### 補完

| プラグイン   | 説明                           |
| ------------ | ------------------------------ |
| nvim-cmp     | 補完エンジン                   |
| nvim-snippy  | コードスニペット               |
| cmp-snippy   | nvim-cmp と nvim-snippy を連携 |
| cmp-nvim-lsp | LSP と nvim-cmp を連携         |

### その他

| プラグイン       | 説明                                       |
| ---------------- | ------------------------------------------ |
| toggle-term.nvim | フローティングウィンドウでターミナルを表示 |
| which-key.nvim   | キーバインドのヒントを表示                 |
| telescope.nvim   | 汎用ファジーファインダ                     |
| gitsigns.nvim    | git 連携                                   |
