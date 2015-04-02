# Railsに関するナレッジ

#### callbackの実行順序を確認したい場合

```
ap [ControllerClass]._process_action_callbacks.map(&:raw_filter)
```
