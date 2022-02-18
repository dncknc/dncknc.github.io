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
## 既存のカラムを index に設定する。
## drop=False で既存のインデックスがカラムに退避される。

df = df.set_index(['timestamp'], drop=False)

## index の番号を振りなおす。dropna()した時などに使う。
# drop=True で既存のインデックスを退避せず上書きする(デフォルトでFalse?)
df = df.reset_index(drop=True) 
df.index.name= 'index'

## 既存のインデックスを連番に変更し、既存のインデックスはカラムに退避する
df = df.reset_index()
df.index.name = 'index'

# 統計量を表示する
df.describe()

{{< / highlight >}}
