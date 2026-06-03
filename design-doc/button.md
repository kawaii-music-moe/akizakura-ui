# Button

操作のトリガーとなるコンポーネント。

## 共通方針

- 角丸は [`--radius`](shape.md) を使う。
- パディングは [spacing](spacing.md) のスケールに従い、縦 `--space-sm` / 横 `--space-md` を標準とする。
- font-family は `var(--font)`、ウェイトは 500（本文 400 より少しだけ強く、押せることを示す）。
- 色は必ず [color](color.md) のトークン経由で指定する。直接記述しない。
- アイコンを伴う場合は [icon](icon.md) に従い、`flex` + `align-items: center`、アイコン↔文字の隙間は `em`（標準 `0.4em`）。

## 種類

| 種類 | 見た目 | 使いどころ |
|---|---|---|
| 既定（`.btn`） | 1px の枠線 + 透明背景 | 通常のアクション。ホバーで枠線と文字を accent 系に切り替える。 |
| 主要（`.btn--primary`） | `--accent` の塗り + `--bg` の文字 | 画面内で最も押させたい 1 つ。塗りで優先度を示す。 |
| 破壊的（`.btn--danger`） | `--danger` の塗り | 削除など取り消しにくい操作。 |
| ゴースト（`.btn--ghost`） | 枠線・背景なし | 線を持たせたくない控えめな操作。[layout](layout.md) の「線は最小限」に沿う選択肢。 |

塗り系（primary / danger）はホバーで暗い派生色（`--accent-dark` など）へ落とす。

## 優先度のルール（[layout](layout.md) 由来）

- 優先度は **塗り** で示し、枠線を増やして示さない。
- 1 画面に主要ボタン（塗り）は原則 1 つ。並んだボタンのうち主役以外は既定（枠線）かゴーストにし、塗りを乱発しない。

## フォーカス / 無効

- フォーカス時は枠線を [`--border-focus`](color.md) に変え、同色の薄いリングを添える（キーボード操作で位置が分かるように）。
- 無効時は文字・枠線を `--text-muted` にし、`cursor: not-allowed`。`disabled` 属性または `aria-disabled="true"` を使う。

## マークアップ例

```html
<button class="btn btn--primary">保存</button>
<button class="btn">キャンセル</button>
<button class="btn btn--ghost">
  <span class="material-symbols-outlined icon">add</span>
  追加
</button>
```
