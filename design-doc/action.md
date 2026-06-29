# Action

操作を起こすためのコントロール群のうち、[button](button.md) に含めない特殊な形のもの（FAB・スイッチ・セグメント・アイコンボタン）。

## アイコンボタン（icon-btn）

- 枠も塗りも持たない、アイコンだけのボタン。ナビのアクション枠などに使う。
- 色は周囲を継承し、ホバーで [`--link-hover`](color.md) と薄い面（[`--surface-tint`](color.md)）。
- フォーカスは [`--border-focus`](color.md) のリングで示す（[form](form.md) と統一）。

## FAB（フローティングアクションボタン）

- **円形にはしない。** 角丸は [`--radius-lg`](shape.md)（Material 3 自体も角丸方形の FAB を採用しており、akizakura の「角丸は固定トークン・pill にしない」方針とも一致する）。
- 塗りは [`--accent`](color.md)、文字色は [`--bg`](color.md)。影は弱い [`--shadow-card`](color.md) のみ（[card](card.md) の影方針に従い、強い elevation は使わない）。
- ラベルを添える extended 形（`fab--extended`）も用意する。位置は `fab--fixed` で右下に浮かせる（opt-in）。
- 1 画面に複数置かない（主たるアクション 1 つ）。

## スイッチ（switch）

- ネイティブ checkbox を隠し、トラック＋つまみで表す。
- **トラックは pill にしない。** [`--radius`](shape.md) の角丸矩形にする（[shape](shape.md): トークン外の形状を増やさない）。
- on は [`--accent`](color.md) 塗り、off は [`--text-muted`](color.md)。つまみは [`--bg`](color.md)。
- 単純な ON/OFF はスイッチ、複数択一は [form](form.md) のラジオ、という使い分けにする。

## セグメント（segmented）

- 連結したトグルボタン。外周だけ [`--radius`](shape.md)、内側は 1px で仕切る。
- 選択は [`--accent`](color.md) 塗りで示す（枠を増やして優先度を表現しない＝[button](button.md) と同じ整理）。
- 項目数は 2〜5 程度まで。それ以上は [form](form.md) のセレクトにする。

## 未決事項

- スライダー・日時ピッカー等の複雑な入力系は未規定。
