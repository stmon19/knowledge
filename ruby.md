# Rubyに関するナレッジ

#### メソッド内でオブジェクトを生成し、処理をしたあと、そのオブジェクトを返したい場合
tapメソッドが綺麗

#### ポイント
- 無駄な初期化が不要
- 最後に無駄な１行が不要
- 行数は同じ

```
# not good
def xxxx_attributes
  ret = {}
  ret.store(xxx, yyy)
  ret.store(zzz, www)
  ret.store(ddd, ttt)
  ret
end

# like it
def xxxx_attributes
  {}.tap do |hash|
    hash.store(xxx, yyy)
    hash.store(zzz, www)
    hash.store(ddd, ttt)
  end
end
```