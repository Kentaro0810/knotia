# GitHub Pages公開手順

1. GitHubでPublicリポジトリ `knotia` を作成します。
2. この完成版フォルダ内のファイルと `assets`、`supabase` フォルダをアップロードします。
3. `config.js`をgithub.devで開き、Supabase URLとPublishable Keyだけを設定して保存します。
4. Settings → Pagesを開きます。
5. Source: Deploy from a branch、Branch: main、Folder: /(root) を選びSaveします。
6. 数分後、`https://kentaro0810.github.io/knotia/`を開きます。

## 絶対にGitHubへ置かないもの
- Supabase Service Role Key
- Resend API Key
- 利用者のパスワード
- 管理者用の秘密鍵
