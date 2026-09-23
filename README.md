# Slidev テンプレート

同梱のPPTXを参考にした、16:9の日本語プレゼンテーション用テンプレートです。
本文・表紙・章扉は白基調とし、見出し帯には深いセージグリーンと白文字を使っています。ブラウンの本文、バーガンディの小見出し、色付きの罫線でメリハリを付けています。
写真はユーザーが用意した画像を使用しています。

## 起動

Node.js 22.12以上（または対応する新しいLTS）を使用します。

```sh
npm install
npm run dev
```

`slides.md`を編集するとプレビューに反映されます。

```sh
npm run build    # 静的サイトをdist/に出力
npm run export   # PDFを書き出し
```

## レイアウト

17枚のサンプルから必要なページを複製・削除して使います。

| layout | 用途 | 設定・スロット |
| --- | --- | --- |
| `cover` | 表紙。白背景、左側のタイトル枠 | `image`, `imageAlt` |
| `agenda` | 目次。左に項目、右に画像領域 | `image`, `imageAlt` |
| `section` | 章扉。白背景と中央タイトル枠 | `image`, `imageAlt` |
| `split` | 画像と文章の左右分割 | `side: left/right`, `image`, `imageAlt`, `::media::` |
| `side-title` | 左右いずれかにセージグリーンの見出し帯 | `side: left/right`, `::title::` |
| `default` | セージグリーンの上部見出し帯と自由な本文 | `::title::` |
| `two-columns` | 2列の説明 | `::left::`, `::right::`, `::title::` |
| `three-columns` | 横3列の説明 | `::first::`, `::second::`, `::third::`, `::title::` |
| `three-rows` | 縦3段の説明 | `::first::`, `::second::`, `::third::`, `::title::` |
| `code-explain` | 左にコード、右に解説 | `::code::`, `::explanation::`, `::title::` |
| `note-table` | 左に補足、右に表 | `::note::`, `::table::`, `::title::` |
| `closing` | 終了ページ。白背景と右側の画像 | `image`, `imageAlt` |

上帯・横帯レイアウトでは、本文の後に`::title::`を置き、見出しを記入します。

```md
---
layout: default
---

本文を記入します。

::title::

# スライドの見出し
```

## 画像や図版の差し替え

画像を`public/images/`に置き、スライドのfrontmatterで指定します。
パスに`public`は含めません。

```yaml
layout: split
side: right
image: /images/example.jpg
imageAlt: 画像の内容を説明するテキスト
```

画像は領域に合わせてトリミングします。画像全体を表示する場合や、独自のVueコンポーネントを入れる場合は、`split`の`::media::`スロットを利用できます（`image`は指定しません）。

```md
::media::

<MediaPlaceholder src="/images/diagram.png" alt="構成図" fit="contain" style="width: 100%; height: 100%" />
```

その他のレイアウトにも自由な内容を埋めたい場合は、対応する`layouts/*.vue`内の`MediaPlaceholder`を編集してください。

## フォントと配色

- BIZ UDPゴシックの400・700を`@fontsource/biz-udpgothic`から読み込みます。ビルドにフォントが含まれ、閲覧端末へのインストールやGoogle Fontsへの接続は不要です。
- ライセンスは依存パッケージ内の`LICENSE`（SIL Open Font License）を参照してください。
- 配色・余白・文字サイズは`style.css`で変更できます。
- フッターは先頭の`title`に連動します。ページ単位の`footer: 任意の文字列`で変更、`footer: false`で非表示にできます。
- 本文の2段組は`columns`、表と補足文の組み合わせは`table-with-note`を使います。

参考: [Slidevのカスタムレイアウト](https://sli.dev/guide/write-layout)、[Slidevの設定](https://sli.dev/custom/)。

## 使い方：型を選んで内容を入れる

スライド冒頭の`layout:`で型を選び、`::...::`の下に各欄の内容をMarkdownで書きます。レイアウト用のHTMLは不要です。各型の実例は`slides.md`にあります。

横3列（8枚目）：

```md
---
layout: three-columns
---

::first::

## 一つ目

説明文

::second::

## 二つ目

説明文

::third::

## 三つ目

説明文

::title::

# スライドの見出し
```

縦3段は`layout: three-rows`に変え、同じ`::first::`〜`::third::`へ内容を入れます（9枚目）。2列は`layout: two-columns`と`::left::`・`::right::`を使います（7・14枚目）。

コードと解説（10・11枚目）：

````md
---
layout: code-explain
---

::code::

```js
console.log('Hello')
```

::explanation::

## コードの説明

ここに説明を記入します。

::title::

# コードの見出し
````

表と補足は`layout: note-table`を使い、`::note::`に説明、`::table::`にMarkdownの表を記入します（13枚目）。

## 写真の差し替え

右上のマークは表示していません。写真を`public/images/`に置き、`slides.md`の`image`と`imageAlt`を編集してください。

## 配置済みの写真

用意された写真をpublic/images/に配置して使用しています。直下にあった同一内容の画像は整理済みです。

| ページ | 元ファイル | 使用ファイル |
| --- | --- | --- |
| 表紙 | 表題.jpg | cover-photo.jpg |
| 目次 | 目次.jpg | agenda-photo.jpg |
| 章扉1 | section1.jpg | section1-crop.jpg |
| 章扉2 | section2.jpg | section2-crop.jpg |
| 謝辞 | 謝辞.jpg | closing-photo.jpg |
| 背景と目的 | 背景.jpg | background-photo.jpg |
| 事例の紹介 | 事例.jpg | example-photo.jpg |

目次は横長写真の全体が見える配置です。章扉2枚はffmpegでハムスターとカップが見える縦長の構図に切り出し、切り出し前の画像もpublic/images/に残しています。`split`の2つのサンプルにも画像を設定しています。

## クレジット

サンプルに含まれる写真は [Unsplash](https://unsplash.com/) の素材を使用しています。実際のプレゼンテーションでは、用途に合った画像に差し替えてください。
