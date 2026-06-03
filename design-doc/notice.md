# Notice

ユーザーへの通知・フィードバックを示すメッセージブロック（情報・成功・エラーなど）。

## 共通方針

- まとまりは **面（[`--surface-tint`](color.md)）** で作り、角丸は [`--radius`](shape.md)、パディングは `--space-md`。
- 状態は **左の細いバー（3px）の色** で示す。
  - 情報: [`--accent`](color.md) / 成功: [`--success`](color.md) / エラー: [`--danger`](color.md) / 既定（中立）: [`--text-muted`](color.md)。
- 内部はアイコン + テキストの横並び、または見出し + 本文の縦並び。要素間は `gap`（`margin` を積まない）。

## 線についての考え方（[layout](layout.md)）

[layout](layout.md) では線は最小限が原則だが、通知は「状態を色で伝える」ことが目的のため、状態色のバーを例外的に使う。
ただし全周を枠で囲わず、**左の 1 本のバーに限定** して情報の主役を奪わないようにする。塗りは中立の `--surface-tint` のままにする。

## マークアップ例

```html
<div class="notice notice--success">
  <span class="material-symbols-outlined icon text-success">check_circle</span>
  <p>保存しました。</p>
</div>
```
