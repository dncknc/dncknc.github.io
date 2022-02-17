---
title: snippet
weight: 1
---

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

######################################
# json.load() で読み込む場合

with open('./settings.json') as f:
    json_dict = json.load(f)
pprint.pprint(json_dict, width=40)
print(type(json_dict))

# dict を for ループ
for key, value in d.items():
    print(key, value)
{{< / highlight >}}

