# コマンドラインからBOM付に変換する方法

## BOM追加

```
nkf --overwrite --oc=UTF-8-BOM target_file
```

## BOM削除

```
nkf --overwrite --oc=UTF-8 target_file
```