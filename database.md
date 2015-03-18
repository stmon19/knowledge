# Databaseに関するナレッジ

#### Float型は使わない

#### ポイント
- floatは小数点以下の値が曖昧
 - floatは2進数管理のため、10進数では表現できても2進数で表現できない値が存在する
 - float型だと「=」での照合が出来ない

#### 対応策
- Decimalを使用する

```
# 例: 59.95でinsertした場合

# float型
# actual: 59.950000762939

select * from orders where amount = 59.95
→ not match

# decimal
# actual: 59.95

select * from orders where amount = 59.95
→ match
```
