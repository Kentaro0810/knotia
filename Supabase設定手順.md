# Supabase設定手順（iPad・ダッシュボードのみ）

## 1. プロジェクト作成
Supabaseで新しいプロジェクトを作成します。

## 2. SQLを実行
1. Supabase Dashboard → SQL Editor
2. New query
3. `supabase/setup.sql`を開き、中身をすべて貼り付け
4. Run

## 3. 最初の管理者を設定
1. 先にKnotiaの登録画面からKentaro0810のアカウントを申請
2. SQL Editorで次を実行（メールは実際のものへ変更）

```sql
update public.profiles
set role='admin', status='approved'
where email='あなたのメールアドレス';
```

## 4. config.jsを設定
Supabase Dashboard → Project Settings → APIから次を確認します。
- Project URL
- Publishable key（またはanon public key）

`config.js`の仮文字を置き換えます。Service Role Keyは絶対に書きません。

## 5. 認証設定
Authentication → URL Configurationで、GitHub Pagesの公開URLをSite URLとRedirect URLへ追加します。

## 6. メール通知（任意だが正式版では推奨）
1. Edge Functions → Deploy a new function → Via Editor
2. 関数名を `notify-application-result` にする
3. `supabase/edge-function-notify-application-result.ts`の内容を貼る
4. Deploy
5. Edge FunctionsのSecretsへ `RESEND_API_KEY` と `EMAIL_FROM` を設定

※メール送信サービス側で送信元ドメイン等の設定が必要です。未設定でも画面上の承認結果とアプリ内通知は動作します。

## 7. Realtime
SQLでboard_postsとdirect_messagesをRealtime publicationへ追加済みです。Database → Publicationsで両テーブルが有効か確認します。
