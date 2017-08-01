# Emacs Lisp についてメモ

## 変数

### `defvar` vs `setq`

`defvar`は再入不可
`setq`は再代入可

## ファイル

### ファイル出力

```lisp
(with-temp-buffer
  (insert "test")
  (write-region (point-min) (point-max) "hogehoge.txt"))
```

### ファイル削除

```list
(delete-file "hogehoge.txt")
```


## org

### clockinしたタスク

```
org-clock-heading
```


### clockinした時間

```
org-clock-start-time
```

### clockin-hook, clockout-hook

```lisp
  (add-hook 'org-clock-in-hook 'write-clockin-task-file)
  (add-hook 'org-clock-out-hook 'delete-clockin-task-file)
  (add-hook 'org-clock-cancel-hook 'delete-clockin-task-file)
```