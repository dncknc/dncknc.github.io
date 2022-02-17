---
title: pandas
weight: 3
---

# snippet

{{< highlight go "linenos=true" >}}
import pandas as pd
df.to_pickle('df_data.pkl')
pd.read_pickle('df_data.pkl')

# 基本操作
## index を設定する。
## drop=False で既存のインデックスを退避する。

df = df.set_index(['timestamp'], drop=False)

## index の番号を振りなおす。
## 既存のインデックスを連番に変更し、既存のインデックスはカラムに退避する
df = df.reset_index()
df.index.name = 'index'

# drop=True で既存のインデックスを退避せず上書きする
df = df.reset_index(drop=True) 
df.index.name= 'index'

# 統計量を表示する
df.describe()

{{< / highlight >}}
