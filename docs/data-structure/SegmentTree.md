# SegmentTree

### 概要

一点更新区間取得のセグメントツリーです。
構造体を書き換えることで、モノイドやモノイド演算を変更することができます。

デフォルトでは [区間和](SegmentTree-monoid/range-sum.md) 用の構造体が入っています。

### 仕様

#### `🍎`

ここにモノイド演算をメソッドとしてのせています。
詳細は [モノイド](SegmentTree-monoid) を参照してください。

#### `🌲`

|メソッド|内容|引数|引数の内容|返り値|返り値の内容|
|---|---|---|---|---|---|
|🌿|初期化|`🔢`|要素数|なし|なし|
|🖊|一点更新|`🔢`, `🍎`|更新位置、更新後の値|なし|なし|
|🔎|区間取得|`🔢`, `🔢`|[左端、右端)|`🍎`|取得結果|

|操作|計算量|
|---|---|
|初期化| $O(N)$ |
|一点更新| $O(\log N)$ |
|区間取得| $O(\log N)$ |

### Pythonでの実装例

```python
class Data:
    def __init__(self, x):
        self.x = x

    def __add__(self, other):
        return Data(self.x + other.x)


class SegmentTree:
    def __init__(self):
        self.data = []
        self.siz = 1
        # 単位元
        self.val = Data(0)

    def init(self, n):
        self.siz = 1
        while n > self.siz:
            self.siz *= 2

        self.data = [self.val] * (self.siz * 2)

    # 更新
    def update(self, pos, value):
        p = pos + self.siz
        self.data[p] = value

        while p >= 2:
            p //= 2
            self.data[p] = self.data[p * 2] + self.data[p * 2 + 1]

    # 区間クエリ [left, right)
    def query(self, left, right):
        l = left + self.siz
        r = right + self.siz

        ansl = self.val
        ansr = self.val

        while l < r:
            if l % 2 == 1:
                ansl = ansl + self.data[l]
                l += 1

            if r % 2 == 1:
                r -= 1
                ansr = self.data[r] + ansr

            l //= 2
            r //= 2

        return ansl + ansr
```

### 使い方

```txt
🏁 🍇
  💭 宣言
  🆕🌲❗️ ➡️ seg

  💭 初期化
  🌿 seg 5❗️

  💭 更新
  🖊 seg 0 🆕🍎 1❗️❗️

  💭 区間取得
  🔎 seg 1 4❗️ ➡️ result
🍉
```

### 注意点

特になし