# Akizakura

Akizakura は kawaii-music.moe のデザイン規則を **1 枚の CSS** にまとめた、依存ゼロの軽量 UI フレームワーク。
「線を最小限にし、余白と近接で構造を伝える」ことを最優先の設計思想とする。

ダークモードに標準対応。トークンが OS 設定（`prefers-color-scheme`）と `<html data-theme>` に連動して切り替わるので、利用側はトークンを使って組むだけでよい（詳細は [`design-doc/color.md`](design-doc/color.md) のダークモード節）。

- デザイン規則の原典: [`design-doc/`](design-doc/)
- フレームワーク本体: [`frontend/src/akizakura.css`](frontend/src/akizakura.css)
- 配信サイト一式: [`frontend/`](frontend/)（Cloudflare Pages の公開ルート）

## 構成

```
design-doc/              デザイン規則（時間に依存しない決定事項）
frontend/                Cloudflare Pages の公開ルート
  index.html             ランディングページ
  demo.html              全コンポーネントのデモ
  llms.txt               LLM 向け索引
  llms-full.txt          LLM 向け完全リファレンス
  src/akizakura.css      フレームワーク本体（配布物）
  _redirects             /akizakura.css → /src/akizakura.css のクリーン URL
  _headers               CORS / キャッシュ / Content-Type
```

## 使い方（利用側 HTML）

フォント（IBM Plex Sans JP）はこの CSS に含めない。`<head>` で読み込む。

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link rel="stylesheet"
      href="https://fonts.googleapis.com/css2?family=IBM+Plex+Sans+JP:wght@300;400;500;600;700&display=swap">
<link rel="stylesheet" href="https://akizakura.pages.dev/akizakura.css">
```

詳細はデプロイ後の `/llms-full.txt`、またはローカルの
[`frontend/llms-full.txt`](frontend/llms-full.txt) を参照。

## ローカルプレビュー

`frontend/demo.html` / `frontend/index.html` をブラウザで直接開くだけで確認できる。
本番に近い形（`_redirects` / `_headers` 込み）で見たい場合は Wrangler のローカルサーバを使う。

```sh
npm install      # 初回のみ（wrangler を取得）
npm run dev      # http://localhost:8788 で frontend/ を配信
```

## Cloudflare Pages へ公開

### 方法 A: Wrangler で直接アップロード（Git 連携なしで最短）

```sh
npm install                                                  # 初回のみ
npx wrangler login                                           # 初回のみ（または CLOUDFLARE_API_TOKEN を設定）
npx wrangler pages project create akizakura --production-branch main   # 初回のみ
npm run deploy                                               # = wrangler pages deploy frontend --project-name akizakura
```

公開 URL は `https://akizakura.pages.dev`。

### 方法 B: Git 連携（push で自動デプロイ）

Cloudflare ダッシュボード → Workers & Pages → Create → Pages → Git 連携で、このリポジトリを接続し、以下を設定する。

| 項目 | 値 |
|---|---|
| Build command | （なし。空欄） |
| Build output directory | `frontend` |

ビルド不要の静的サイトなので、出力ディレクトリに `frontend` を指定するだけでよい。

## 配信される主な URL

| URL | 内容 |
|---|---|
| `/` | ランディングページ |
| `/demo`（`/demo.html` は自動正規化） | コンポーネントデモ |
| `/akizakura.css` | CSS 本体（配布用クリーン URL） |
| `/llms.txt` | LLM 向け索引 |
| `/llms-full.txt` | LLM 向け完全リファレンス |
