---
title: .gitignore をホワイトリストで運用
weight: 1
---

# .gitignore をホワイトリストで運用する設定
{{< highlight gitconfig "linenos=true" >}}
# -------------------------------------------- #
# ホワイトリスト型の .gitignore
# 参考: https://ai-inter1.com/python-print/
# -------------------------------------------- #
# 各記号の意味
# * : /以外の0文字以上の文字列にマッチ
# ? : /以外の1文字にマッチ
# [0-9] : /以外の指定した1文字にマッチ
# **: 0個以上のファイル or ディレクトリにマッチ
# !で始まる行 : !以降のパターン文字列が示すファイル or ディレクトリを無視しない。前の無視指定を上書きする
# -------------------------------------------- #

# 【1】 全ファイルを無視する設定
# すべてのファイルを無視するが、フォルダは全て追加する
# この設定でも git は空フォルダを無視することに注意。
*
!*/

# 【2】 任意のファイルやフォルダを追加する設定
# 指定したフォルダの下にあるファイルとフォルダを追加する
# 二重のアスタリスクは0個以上のファイルやディレクトリに一致することを示す。
# !/lib/**
!/historical_data/**

# このファイル(.gitignore)と同階層以下の「??？_a」というフォルダ階層以降を許可
# !**/*_a/**

# このファイル(.gitignore)と同階層のファイルだけ許可
# .gitignoreにファイル名やフォルダ名を書くと、
# 階層関係なくマッチする名前のファイルを無視できる。
# 先頭に「/（スラッシュ）」を付けると、.gitignoreが置かれてあるディレクトリを
# 基準としてファイルを無視できる。

# !/README.md
!/.gitignore
!/*.ipynb
!/*.md

# ------------------------------------------------
# 【3】 常に除外するファイルやフォルダを禁止
# OSが自動で作るファイル
.DS_Store
Thumbs.db
# アプリが自動で作るファイル
.ipynb_checkpoints/

# その他
/archive/
/csv/
/fonts/

{{< / highlight >}}
