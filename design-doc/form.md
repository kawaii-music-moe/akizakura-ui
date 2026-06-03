# Form

入力を受け取るコンポーネント群（テキスト入力・選択・チェック類）。

## フィールドの構成

- 「ラベル → コントロール → 補助テキスト（ヒント / エラー）」の縦並びを基本とする。
- まとまりは縦 `flex` + `gap`（[`--space-xs`](spacing.md)）で組み、要素ごとに `margin` を積まない。
- ラベルは `font-weight: 500`。補助テキストは小さめ（0.85rem 目安）で、ヒントは [`--text-sub`](color.md)、エラーは [`--danger`](color.md)。

## コントロール共通

- 角丸は [`--radius`](shape.md)。
- パディングは [spacing](spacing.md) のスケールに従い、縦 `--space-sm` / 横 `--space-md` を標準とする。
- フォントは `var(--font)`、文字色は [`--text`](color.md)。プレースホルダは [`--text-muted`](color.md)。
- フォーカス時は枠線を [`--border-focus`](color.md) に変え、同色の薄いリングを添える。
- エラー状態は枠線を `--danger` にする。

## チェックボックス / ラジオ

- ネイティブ要素を使い、`accent-color` に [`--accent`](color.md) を当てる。独自の作り込みはしない。
- ラベルと横並びにし、隙間は親フォントサイズ連動のため `em`（標準 `0.5em`）で取る（[icon](icon.md) / [spacing](spacing.md) の em 運用に倣う）。
- サイズはフォントに連動させ `1em` を基準にする（[icon](icon.md) のサイズ方針に揃える）。

## グループ化（fieldset）

- 関連する入力のまとまりは枠線で囲わず、`legend`（見出し相当）＋余白で表現する（[layout](layout.md) の「枠で囲わない / 線は最小限」）。

## マークアップ例

```html
<div class="field">
  <label class="label" for="name">名前</label>
  <input class="input" id="name" type="text" placeholder="kawaii">
  <p class="field__hint">表示名に使われます。</p>
</div>

<fieldset class="fieldset">
  <legend>通知設定</legend>
  <label class="check"><input type="checkbox" checked> メールで受け取る</label>
  <label class="check"><input type="checkbox"> SNS で受け取る</label>
</fieldset>
```
