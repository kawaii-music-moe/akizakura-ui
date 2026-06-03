# Design Doc

kawaii-music.moe のデザインルールを言語化・蓄積するためのディレクトリ。

ここで決めた規則は、合意が固まった段階で `frontend/src` 配下の共通 CSS（CSS 変数など）へ落とし込む。現時点ではまず文章で合意を作り、実装は後追いとする。

## 方針

- 1 トピック = 1 ファイル。決まりが増えたらファイルを追加していく。
- 各ファイルは「決定事項」「理由（必要なら）」「未決事項」を明記する。
- 現状の実装状態（既存ファイルの今の値、どこが未対応か等）は書かない。ここは時間に依存しない規則の置き場として使う。

## 目次

### 上位方針

- [layout.md](layout.md) — レイアウト全体に通底する徹底事項

### トークン

- [typography.md](typography.md) — フォント、ウェイト、ヘッダー規則
- [color.md](color.md) — 配色トークン
- [shape.md](shape.md) — 角丸などの形状トークン
- [breakpoint.md](breakpoint.md) — レスポンシブのブレイクポイント
- [spacing.md](spacing.md) — margin / padding / gap のスケール

### コンポーネント

- [card.md](card.md) — カードコンポーネントの方針
- [list.md](list.md) — リストコンポーネントの方針
- [form.md](form.md) — フォーム（入力・選択・チェック）の方針
- [button.md](button.md) — ボタンの方針（種類・優先度・フォーカス）
- [badge.md](badge.md) — バッジ / タグの方針
- [notice.md](notice.md) — 通知 / メッセージの方針
- [icon.md](icon.md) — アイコンの方針（ソースの使い分け・サイズ・色）
