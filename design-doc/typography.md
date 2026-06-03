# Typography

## フォント

| 用途 | フォント | 備考 |
|---|---|---|
| 本文 | IBM Plex Sans JP | sans-serif をフォールバック |
| 見出し / サイト名 | IBM Plex Sans JP | 本文と同じファミリ。ウェイトと字間で差をつける |

Google Fonts から読み込むウェイト: **300 / 400 / 500 / 600 / 700**

CSS 変数として `--font: 'IBM Plex Sans JP', sans-serif;` を `:root` に定義し、UI 側からは必ず `var(--font)` 経由で参照する。

## ヘッダー（サイトタイトル）

| 項目 | 値 |
|---|---|
| font-family | IBM Plex Sans JP |
| font-weight | 600 |
| letter-spacing | 0.02em |
| font-size | 1.4rem |
| 区切り `.` の色 | `var(--accent)`（[color.md](color.md) 参照） |

### ヘッダーの文字列規則

- 既定: `KAWAII-MUSIC.MOE`
- サブサイト / アーカイブの場合は `.MOE` の部分を文脈に応じて差し替える。
  - 例: サンプルパック → `KAWAII-MUSIC.SAMPLES`
- `.` の **前** は常に `KAWAII-MUSIC` 固定。`.` の **後ろ** がそのコンテキストを表す。
- `.` は単独で `<span>` に分け、accent 色を当てる。

### マークアップ例

```html
<h1 class="site-title">KAWAII-MUSIC<span>.</span>MOE</h1>
```

## 本文

- font-family: `var(--font)`
- font-weight: 400（既定）

## 見出し

| 要素 | font-size |
|---|---|
| h1 | 2rem |
| h2 | 1.5rem |
| h3 | 1.2rem |

セクションを特に強調したい場合は h2 を 1.6rem まで引き上げてもよい（ページ最上位の見出し用途）。
ヘッダー（サイトタイトル）は上記スケールから独立した固定値（1.4rem）を使う。

## 行間（line-height）

ブラウザ既定の line-height をそのまま使用し、ドキュメント全体には独自の値を設定しない。
特定要素で詰まりすぎ・空きすぎる場合のみ、その要素単位で局所的に上書きする。

## リンク（アンカー）

```css
a {
  color: currentColor;
  text-decoration: none;

  &:hover {
    color: var(--link-hover);
  }
}
```

- 既定ではテキスト色を継承（`currentColor`）し、下線は付けない。
- ホバー時のみ `--link-hover`（アクセント系の暗い派生色）に切り替える（[color.md](color.md) 参照）。

## 等幅フォント

専用の等幅フォントは導入しない。
将来コードや英数字を等幅で見せたい場面が出た場合は、`monospace` のフォールバックのみで運用する。それで不足する場合に改めてフォントを選定する。

## コード表示

インラインの `code` とブロックの `pre` は、上記方針どおり専用フォントを足さず `monospace` フォールバックで表示する。
背景は線ではなく面（[`--surface-tint`](color.md)）で軽く囲い、角丸は [`--radius`](shape.md) を使う（[layout](layout.md) の「線は最小限」に沿う）。`pre` 内の `code` は二重に囲わないよう背景を持たせない。
