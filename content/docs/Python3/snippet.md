---
title: snippet
weight: 1
---

## ファイル関連
### 基本
{{< highlight go "linenos=true" >}}
# ファイルの存在確認
import os
if (os.path.isfile(path)):
    pass

# ファイルの読み込み
with open('./settings.json') as f:
    print(f.read())

# ファイルの書込み
data = "test"
with open(path, mode='w') as f:
    f.write(data)

# ファイルのコピー
import shutil
shutil.copy('./old.txt', './sample/new.txt')

{{< / highlight >}}

### Json
{{< highlight go "linenos=true" >}}
# json.load() で読み込む場合

with open('./settings.json') as f:
    json_dict = json.load(f)
pprint.pprint(json_dict, width=40)
print(type(json_dict))

# dict を for ループ
for key, value in dict_test.items():
    print(key, value)
{{< / highlight >}}

### ファイルパス、ファイル名関連
{{< highlight go "linenos=true" >}}
# ファイルパスからファイル名を取得
basename = os.path.basename(path)
print(basename)

# 新しいパスを作成する
import os
read_path = './aaa/bbb/ccc_ddd_eee.txt'
file_name = os.path.basename(read_path)
#'ccc_ddd_eee.txt'
dir_name = os.path.dirname(read_path)
# './aaa/bbb'
file_name_split = file_name.split('.')
new_file_name = file_name_split[0] + "_add_xxx_." + file_name_split[1]

# 文字列を正規表現で置換
import re
new_dir = re.sub('bbb$', 'zzz', dir_name)
save_path = new_dir + '/' + new_file_name
# './aaa/zzz/ccc_ddd_eee_add_xxx_.txt'

{{< / highlight >}}


## テストの書き方
{{< highlight go "linenos=true" >}}
def add(x, y):
    """
    xとyを加算した結果を返す
        >>> add(2, 3)
        5
    """
    return x + y

python -m doctest -v add.py

# Jupyter上でテストする場合
import doctest
doctest.testmod()

{{< / highlight >}}


{{< highlight go "linenos=true" >}}
dir(response.request)
{{< / highlight >}}



{{< highlight go "linenos=true" >}}
{{< / highlight >}}


