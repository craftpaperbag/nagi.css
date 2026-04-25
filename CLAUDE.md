# nagi.css — プロジェクトガイド

## 概要

セマンティックなHTMLに静けさを与える、日本語向けクラスレスCSSフレームワーク。
単一ファイル・依存なし・約6KB（未圧縮）。

## ファイル構成

```
nagi.css      メインCSS（唯一の成果物）
index.html    デモ・サンプルページ
README.md     ドキュメント
LICENSE       MIT
```

ビルドツール・パッケージマネージャーは一切使用しない。直接CSSを編集する。

## 設計原則（変更時に常に参照すること）

1. **クラスレス** — `class=""` を書かせない。セマンティックなタグに直接スタイルを当てる
2. **日本語最適化** — 行長 `60ch`（約38文字）、行間 `1.8`、日本語システムフォント優先
3. **装飾の最小化** — 色は前景・背景・罫線のグレーのみ。影・カード・アニメーション不使用
4. **引き算の設計** — 機能を足すのではなく、不要なものを削る
5. **CSS変数で上書き可能** — すべて `--nagi-*` プレフィックスで管理

> 「装飾で補強しないと伝わらない情報は、まだ十分に削られていない。」

## CSS変数の命名規則

すべて `--nagi-` プレフィックス。

| カテゴリ | 例 |
|---|---|
| カラー | `--nagi-bg`, `--nagi-fg`, `--nagi-fg-muted`, `--nagi-fg-subtle`, `--nagi-border`, `--nagi-border-strong`, `--nagi-surface`, `--nagi-accent` |
| タイポグラフィ | `--nagi-font-sans`, `--nagi-font-serif`, `--nagi-font-mono` |
| レイアウト | `--nagi-measure` (60ch), `--nagi-measure-wide` (75ch), `--nagi-line-height` (1.8) |
| 余白 | `--nagi-space-xs/sm/md/lg/xl` |
| その他 | `--nagi-radius` (2px), `--nagi-border-width` (0.5px), `--nagi-transition` |

## ダークモード

`@media (prefers-color-scheme: dark)` でカラー変数のみ上書き。構造は共通。

## 唯一のクラス

`.wide` — `max-width` を `--nagi-measure-wide` (75ch) に拡大したいときだけ使用。

## 変更時の注意

- 新しい装飾（影・グラデーション・アニメーション等）を追加しない
- クラスベースのユーティリティを追加しない（設計原則に反する）
- 新しいCSS変数は必ず `--nagi-` プレフィックスをつける
- ダークモード対応が必要な色はカラー変数経由で管理する
- `index.html` は機能追加時にあわせてデモを更新する
