# Agent Guide — sage-slidev-template

> このファイルは AI コーディングエージェント（Codex など）がプロジェクトを理解するためのリファレンスです。

## プロジェクト概要

**Slidev** (https://sli.dev) で動く 16:9 日本語プレゼンテーションテンプレートです。  
すべてのスライドは `slides.md` に Markdown + YAML frontmatter で記述し、カスタムレイアウト（Vue SFC）と `style.css` でデザインを制御します。

- パッケージ名: `sage-slidev-template`
- Node.js: 22.12 LTS 以上
- Slidev バージョン: **53.x** (`@slidev/cli`)
- テーマ: `@slidev/theme-default`（レイアウトとスタイルは本プロジェクト側で上書き）
- フォント: **BIZ UDPゴシック** 400/700（`@fontsource/biz-udpgothic` から読み込み、ビルドに含まれる）

## npm スクリプト

| コマンド | 説明 |
| --- | --- |
| `npm run dev` | 開発サーバーを起動してブラウザで開く |
| `npm run build` | `dist/` に静的サイトを出力 |
| `npm run export` | PDF を書き出す（Playwright Chromium 使用） |
| `npm run preview` | ビルド済み `dist/` をプレビュー |

## ディレクトリ構成

```
slide-template/
├── slides.md              # ★ メインのスライド定義（全ページ）
├── style.css              # グローバルCSS（配色・レイアウトスタイル）
├── package.json
├── layouts/               # カスタム Slidev レイアウト（Vue SFC）
│   ├── cover.vue
│   ├── agenda.vue
│   ├── section.vue
│   ├── split.vue
│   ├── side-title.vue
│   ├── default.vue
│   ├── two-columns.vue
│   ├── three-columns.vue
│   ├── three-rows.vue
│   ├── code-explain.vue
│   ├── note-table.vue
│   └── closing.vue
├── components/            # グローバル Vue コンポーネント
│   ├── DeckFooter.vue     # ページフッター（タイトルとページ番号）
│   ├── MediaPlaceholder.vue  # 画像/図版プレースホルダー
│   └── HamsterMark.vue    # 装飾用ハムスターマーク
├── public/images/         # 静的画像アセット
│   ├── cover-photo.jpg
│   ├── agenda-photo.jpg
│   ├── section1-crop.jpg / section1.jpg
│   ├── section2-crop.jpg / section2.jpg
│   ├── closing-photo.jpg
│   ├── background-photo.jpg
│   ├── example-photo.jpg
│   ├── hamster-*.png      # テーマ装飾画像
│   └── .gitkeep
├── dist/                  # ビルド出力（gitignore）
└── .work/                 # Slidev 内部キャッシュ（gitignore）
```

## スライドの書き方

`slides.md` はスライド区切り `---` で分割されたMarkdownです。各スライドの先頭に YAML frontmatter を置き、`layout:` でレイアウトを指定します。

### グローバル frontmatter（先頭スライド）

```yaml
theme: default
title: プレゼンテーションのタイトル
author: 発表者名
aspectRatio: 16/9
canvasWidth: 1280
colorSchema: light
fonts:
  sans: BIZ UDPGothic
  serif: BIZ UDPGothic
  mono: BIZ UDPGothic
  local: [BIZ UDPGothic]
htmlAttrs:
  lang: ja
drawings:
  enabled: false
transition: fade
```

### スロット記法

本文のデフォルトスロットの後に `::スロット名::` を書いてスロットに内容を配置します。

```md
本文をここに書く

::title::

# 見出し
```

## レイアウト一覧と使い方

### cover（表紙）
- props: `image`, `imageAlt`
- 左側に白半透明フレーム（タイトル）、右側に画像
- `layout: cover` を先頭スライドに使用

### agenda（目次）
- props: `image`, `imageAlt`
- 左側にリスト、右側に画像

### section（章扉）
- props: `image`, `imageAlt`
- 背景画像付きの中央タイトル枠（左ボーダー）

### split（左右分割 — 画像と文章）
- props: `image`, `imageAlt`, `side`（`left` | `right`、デフォルト `right`）
- `side` で画像の位置を指定（`right` = 右に画像、`left` = 左に画像）
- `::media::` スロットで画像の代わりに任意のコンテンツを配置可能

### side-title（サイドタイトル帯）
- props: `side`（`left` | `right`、デフォルト `left`）
- `::title::` スロットに見出しを配置（セージグリーン背景＋白文字の帯）
- 本文はデフォルトスロット

### default（標準レイアウト）
- スロット: `::title::` (セージグリーンの上部帯見出し)
- 本文はデフォルトスロット

### two-columns（2列）
- スロット: `::left::`, `::right::`, `::title::`

### three-columns（横3列）
- スロット: `::first::`, `::second::`, `::third::`, `::title::`
- 列間に罫線が入る

### three-rows（縦3段）
- スロット: `::first::`, `::second::`, `::third::`, `::title::`
- 段間に罫線が入る

### code-explain（コード解説）
- スロット: `::code::`, `::explanation::`, `::title::`
- 左にコードブロック、右に解説

### note-table（表と補足）
- スロット: `::note::`, `::table::`, `::title::`
- 左に補足文（230px）、右に表

### closing（終了ページ）
- props: `image`, `imageAlt`
- 左側にメッセージ、右側に画像

## コンポーネント

### DeckFooter
全レイアウトで使用。`$frontmatter.footer` または `$slidev.configs.title` を表示。  
`footer: false` で非表示、`footer: 任意の文字列` で上書き可能。

### MediaPlaceholder
画像プレースホルダー。`src` が指定されていれば `<img>` を表示、なければラベルを表示。  
props: `src`, `alt`, `label`（デフォルト「画像・図版」）, `fit`（`cover` | `contain`、デフォルト `cover`）

### HamsterMark
テーマの装飾用アイコン（`/images/hamster-geometric.png`）。現在スライドでは使用していない。

## 配色（CSS カスタムプロパティ）

| 変数 | 値 | 用途 |
| --- | --- | --- |
| `--sage` | `#59635d` | メインカラー（見出し帯背景、タイトル文字） |
| `--ink` | `#4a3a1c` | 本文テキスト（ブラウン） |
| `--accent` | `#975b40` | 小見出し・リストマーカー（ハムスターテーマで上書き済み） |
| `--charcoal` | `#202124` | 補助的な濃いグレー |
| `--rule` | `#dbc7ae` | 罫線・ボーダー（ハムスターテーマで上書き済み） |
| `--paper` | `#ffffff` | 背景色 |
| `--media` | `#fbf3e5` | 画像プレースホルダー背景（ハムスターテーマで上書き済み） |

## 画像の扱い

- 画像は `public/images/` に配置する
- frontmatter の `image` パスには `public` を含めない（例: `/images/cover-photo.jpg`）
- `imageAlt` で代替テキストを指定する
- 画像は `object-fit: cover` でトリミングされる（`MediaPlaceholder` の `fit` prop で変更可）

## 編集時の注意事項

1. **`slides.md` がメイン**  
   スライドの追加・削除・並び替えはすべて `slides.md` で行う。`---` でスライドを区切る。

2. **レイアウトVueファイルは薄い**  
   各レイアウトは HTML 構造と slot 定義のみ。スタイルは `style.css` に集約されている。

3. **スタイル変更は `style.css`**  
   配色・余白・フォントサイズの変更は `style.css` の CSS カスタムプロパティとクラスを編集する。

4. **`node_modules/`, `dist/`, `.work/` は触らない**  
   これらは生成物またはキャッシュ。`.gitignore` に含まれている。

5. **HTMLの使用**  
   Slidev は Markdown 中に HTML（`<br>`, `<hr>`, Vue コンポーネントタグなど）を直接書ける。このテンプレートでも `<br>` や `<hr>` を多用している。

6. **本文中の2段組**  
   `default` レイアウトの本文内で2段組にするには `<div class="columns">` で囲む。表と補足は `<div class="table-with-note">` を使う。

7. **フッター制御**  
   スライド単位で `footer: false`（非表示）または `footer: 任意のテキスト`（上書き）を frontmatter に書く。

## Slidev の基本情plash

- 公式ドキュメント: https://sli.dev
- カスタムレイアウト: https://sli.dev/guide/write-layout
- スライドの書き方: https://sli.dev/guide/syntax
- Slidev はVite + Vue 3ベースで、Markdown をスライドとしてレンダリングする
- `layouts/` に置いた `.vue` ファイルは自動的にレイアウトとして認識される
- `components/` に置いた `.vue` ファイルは自動的にグローバルコンポーネントとして登録される

