# Squeelに関するナレッジ

### ActiveRecordの検索を更に書きやすくしてくれるgem

[github](https://github.com/activerecord-hackery/squeel)

#### ポイント
- or条件がArelを使わなくても簡単にかける
- 括弧ではなくブロックを利用する
- 黒魔術過ぎる

#### Badポイント
- 謎なSQLが発行されるケースがある
 - 必ずではないが、ARとsqueelを組み合わせるとwhere句の値に0が入る事がある

```
# bad
scope :admin, -> { where { type == :admin } }
scope :update_date_by, ->(date) { where(updated_at: date) } # 括弧(AR)を使っている

user.admin.update_date_by(Date.today)

-> select * from users where type = 'admin' and updated_at = 0

# good
scope :admin, -> { where { type == :admin } }
scope :update_date_by, ->(date) { where { updated_at == date } } # ブロックを使っている

user.admin.update_date_by(Date.today)

-> select * from users where type = 'admin' and updated_at = '2015-01-01'
```
