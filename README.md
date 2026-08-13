# fuzistamp 公開・LINE接続手順

このフォルダーは、富士フイルムのスタンプラリーだけを入れた専用アップロード一式です。ほかのミニアプリのファイルやLIFF IDは含めていません。

## 1. GitHubへアップロード

1. [fuzistampのアップロード画面](https://github.com/takataka5727/fuzistamp/upload)を開きます。
2. このフォルダーの「中身」をすべてドラッグします。親フォルダーごとではなく、`index.html` がリポジトリ直下に見える状態にします。
3. 画面下の「Commit changes」を押します。

アップロードするもの:

- `index.html`
- `styles.css`
- `app-config.js`
- `app.js`
- `assets` フォルダー
- `.nojekyll`
- `IMAGE_SOURCES.md`
- `README.md`

## 2. GitHub Pagesを有効化

1. リポジトリの「Settings」→「Pages」を開きます。
2. Sourceを「Deploy from a branch」にします。
3. Branchを「main」、フォルダーを「/(root)」にして保存します。
4. 数分後、次のURLで表示を確認します。

```text
https://takataka5727.github.io/fuzistamp/
```

## 3. LINE用のLIFFを新規作成

既存ミニアプリと混ざらないよう、fuzistamp専用のLIFFアプリを新規作成します。

1. LINE Developersコンソールで、fuzistamp用のLINEログインチャネルまたはLINEミニアプリチャネルを用意します。
2. LIFFアプリを追加し、Endpoint URLに次を設定します。

```text
https://takataka5727.github.io/fuzistamp/
```

3. 発行されたLIFF IDを、このフォルダーの `app-config.js` に設定します。

```javascript
line: {
  liffId: "ここにfuzistamp専用のLIFF ID",
},
```

4. 更新した `app-config.js` をGitHubへ再アップロードします。
5. LINEで確認するときは、発行されたLIFF URLを使います。

```text
https://liff.line.me/発行されたLIFF_ID
```

他のミニアプリのLIFF IDは設定しないでください。

## 補足

現在のスタンプ取得・景品交換状態は端末の `localStorage` に保存するモックです。本番運用では、サーバー側のスタンプ発行、不正取得防止、景品交換記録が必要です。

