# Pryに関するナレッジ

### インストール必須！開発効率を上げてくれるgem

[github](https://github.com/pry/pry)

#### ポイント
- デバッグ効率3倍(binding.pryが神)
- pry-byebugと合わせるとステップ実行可能


#### ブレークポイントの作成
```
def index
  @order = Order.find_by(number: params[:order_id])
  binding.pry # ここでブレークする
end

→ pry(main)> $ ap @order
```

#### @orderの中身を確認したい
```
pry(main)> $ ap @order # 好きなようにデバッグしてみてください
→ <Order: xxxxxxxx>
```

#### ブレークしたcontextのオブジェクトの状態を確認したい
```
pry(main)> $ ls
→ # 下記のように利用可能なメソッド、includeしたmodule等確認できる
StoresController#methods: index
instance variables:
  @_action_has_layout  @_config  @_headers         @_params   @_response       @_routes  @instances                            @resource_ancestors
  @_action_name        @_env     @_lookup_context  @_request  @_response_body  @_status  @marked_for_same_origin_verification  @search
```

#### ブレークしたcontextから別のオブジェクトのcontextに移りたい
```
pry(main)> $ cd model
→pry(Order):1> # 再度lsなどが使える
```

#### ソースを確認したい
```
※「$」 は show-sourceのエイリアスです
pry(main)> $ $ [対象] # クラス名やlsで見れるもの、メソッドも可
→ # ソースが表示される
pry(main)> $ $ Order
pry(main)> $ $ BaseController#ordering
pry(Order)> $ $ find

```

#### exit
```
pry(main)> $ !!!
```

#### 詳しくはこれをみて
```
pry(main)> $ help
```