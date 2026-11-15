# lower_bound

### 概要

昇順の整数型配列 `list` について、 `val` 以上の値となる最小のインデックスを返す

### 仕様

|項目|内容|Emojicode|
|---|---|---|
|引数 1|整数型配列|🍨🐚🔢🍆|
|引数 2|整数型|🔢|
|戻り値|整数型|🔢|

### Pythonでの実装例

```python
def lower_bound(lst, val):
    left = -1
    right = len(lst)
    while right - left > 1:
        mid = (right + left) // 2
        if lst[mid - 1] >= val:
            right = mid
        else:
            left = mid
            
    return right
```

### 注意点

昇順のリストを引数に渡してください