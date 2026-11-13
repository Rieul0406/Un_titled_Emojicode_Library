# tolist

### 概要

空白区切りの文字列を、整数型のリストに変換する。

### 仕様

|項目|内容|Emojicode|
|---|---|---|
|引数|文字列|🔡|
|戻り値|リスト（整数型）|🍨🐚🔢🍆|

### Pythonでの実装例

```python
def tolist(s : str) -> list[int]:
    return list(map(int, s.split()))
```

### 注意点

整数値でない空白区切りの文字列を渡した場合、optional型のunwrapが失敗し、Runtime Errorとなります。
