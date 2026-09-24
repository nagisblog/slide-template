---
theme: default
title: プレゼンテーションのタイトル
author: 発表者名
info: false
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
layout: cover
image: /images/cover-photo.jpg
---

# プレゼンテーションの<br>タイトル

<hr>

発表者名<br>
所属

---
layout: agenda
image: /images/agenda-photo.jpg
---

# 目次

1. はじめに
2. 背景と目的
3. 提案内容
4. 進め方
5. まとめ

---
layout: section
image: /images/section1-crop.jpg
---

# ここに章のタイトルを<br>入力します

---
layout: split
side: right
footer: false
image: /images/background-photo.jpg
---

# 背景と<br>目的

<hr>

章の内容をひとことで伝える

---
layout: side-title
side: left
---

- このスライドで伝えたい要点を記入します。
- 背景や理由など、理解を助ける説明を加えます。
- 一つの項目に一つの話題をまとめます。
- 補足が多い場合は、次のスライドに分けます。

::title::

# 伝えたい<br>ポイント

---
layout: section
image: /images/section2-crop.jpg
---

# 提案内容

提案の概要や章の説明を記入します

---
layout: two-columns
---

::left::

## 一つ目の観点

ここに説明文を記入します。二つの観点を並べて説明するレイアウトです。

- 主な特徴
- 具体的な内容
- 補足事項

::right::

## 二つ目の観点

同じ長さを目安に文章を記入すると、左右のバランスが整います。

- 主な特徴
- 具体的な内容
- 補足事項

::title::

# 二つの観点から説明する

---
layout: three-columns
---

::first::

## 01 課題を整理する

現状と目指す状態を比べ、解決したい問題を明確にします。

- 利用者の声を集める
- 影響の大きい課題を選ぶ
- 達成したい状態を決める

::second::

## 02 小さく試す

必要な機能に絞って試作し、使い方や実現方法を確かめます。

- 最小限の機能を作る
- 実際の操作を試す
- 改善点を記録する

::third::

## 03 結果を評価する

試作で得られた結果をもとに、次の取り組みを決めます。

- 目標と結果を比較する
- 残った課題を整理する
- 次の担当と期限を決める

::title::

# 取り組みを進める3つのステップ

---
layout: three-rows
---

::first::

## 01 課題を整理する

現状と目指す状態を比べ、解決したい問題を明確にします。<br>利用者の声を集め、影響の大きい課題から優先順位を付けます。

::second::

## 02 小さく試す

必要な機能に絞って試作し、実際の操作を確かめます。<br>使いにくい点や想定との違いを記録し、改善につなげます。

::third::

## 03 結果を評価する

目標と結果を比較し、達成できたことと残った課題を整理します。<br>次に取り組む内容、担当者、期限を決めます。

::title::

# コード例：配列の絞り込みと変換

---
layout: code-explain
---

::code::

<p class="code-caption">hello.c / C言語</p>

```c
#include <stdio.h>

int main(void) {
    printf("Hello, world!\n");
    return 0;
}
```

実行結果：`Hello, world!`

コンパイル：`gcc hello.c -o hello.exe`  
実行（PowerShell）：`.\hello.exe`

::explanation::

## 1. 標準入出力を読み込む

`#include <stdio.h>`で、文字を表示する`printf`を使えるようにします。

## 2. main関数に処理を書く

プログラムは`main`から始まります。`\n`は改行を表します。

## 3. 正常終了を伝える

`return 0;`は、処理が正常に終わったことを示します。

::title::

# Cで「Hello, world!」を表示する

---
layout: side-title
side: right
---

1. 最初に確認する内容
2. 次に検討する内容
3. 最後に決定する内容

<br>

必要に応じて、手順の補足や注意点をここに記入します。

::title::

# 進め方と<br>確認事項

---
layout: split
side: left
image: /images/example-photo.jpg
---

# 事例の紹介

<hr>

写真や図版と合わせて、<br>伝えたい内容を簡潔に説明します。

詳細な説明が必要な場合は、<br>別のスライドにまとめます。

---
layout: note-table
---

::note::

表の見方や比較の前提条件を記入します。

数値や項目は、使用する資料に合わせて差し替えてください。

::table::

| 項目 | 単位 | 目標 | 実績 |
| :--- | :--- | ---: | ---: |
| 項目 A | 件 | — | — |
| 項目 B | 分 | — | — |
| 項目 C | 回 | — | — |
| 項目 D | % | — | — |
| 項目 E | % | — | — |

::title::

# 結果の概要

---
layout: two-columns
---

::left::

## 振り返り

- 今回確認できたこと
- 継続して取り組むこと
- 改善が必要なこと

::right::

## 次の取り組み

担当者や期限など、具体的な進め方を記入します。

必要な資料や確認事項も合わせて整理します。

::title::

# まとめと今後の予定

---
layout: default
---

| 評価項目 | 測定方法 | 目標 | 結果 |
| :--- | :--- | ---: | ---: |
| 評価項目 A | パーセンテージ (%) | — | — |
| 評価項目 B | パーセンテージ (%) | — | — |
| 評価項目 C | 平均評価 | — | — |
| 評価項目 D | 件数 | — | — |
| 評価項目 E | 回数 | — | — |

::title::

# 評価指標の一覧

---
layout: closing
image: /images/closing-photo.jpg
---

# ありがとうございました

<hr>

発表者名<br>
所属・連絡先<br>
example.com
