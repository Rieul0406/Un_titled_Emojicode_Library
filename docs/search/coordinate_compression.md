# 座標圧縮

### 概要

配列をソート・重複削除し、座標圧縮を行う。
圧縮後のインデックスは二分探索等によって取得する。

### 仕様

##### 引数

|項目|内容|Emojicode|
|---|---|---|
|引数|整数型配列|🍨🐚🔢🍆|

#### メソッド 

##### 📍

圧縮後インデックスを返す

|項目|内容|Emojicode|
|---|---|---|
|引数 1|整数値|🔢|
|引数 2|closure|🍇🍨🐚🔢🍆 🔢 ➡️ 🔢🍉|
|戻り値|整数値|🔢|

引数2には、 [lower_bound](lower_bound.md) もしくは [upper_bound](upper_bound.md) を渡すことを想定しています。

### Pythonでの実装例

```python
class Compress:
    def init(self, vec):
        self.list = []
        v = sorted(vec)
        for x in v:
            if len(self.list) == 0:
                self.list.append(x)
            elif self.list[-1] != x:
                self.list.append(x)
    def pos(self, val, func):
        return func(self.list, val)
```

### 使い方

```txt
💭 宣言
🗜️🆕 v❗️➡️ comp

💭 圧縮後の value のインデックス取得
📍 comp value lower_bound❓
```

### 注意点

特になし
