---
title: request
weight: 1
---

## request関連

dir() についてはこちらから。
https://docs.python.org/ja/3.9/library/functions.html#dir

{{< highlight go "linenos=true" >}}
# dir() は引数がない場合、現在のローカルスコープにある名前のリストを返します。
# 引数がある場合、そのオブジェクトの有効な属性のリストを返そうと試みます。

# response の中身を確認
dir(response)
dir(response.request)

# リクエストに使用したヘッダーを確認
response.request.headers
{{< / highlight >}}


