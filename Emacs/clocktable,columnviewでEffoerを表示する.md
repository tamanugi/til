# clocktable,columnviewでEffoerを表示する

## Clock Table

`:properties ("Effort")` を追加する

```
#+BEGIN: clocktable :tstart "<2015-06-10>" :tend "<now>" :scope file :maxlevel 6 :tags ""  :properties ("Effort")
```

## Column View

`Effort(Estimated Effort)`を追加する

```
#+COLUMNS: %40ITEM(Task) %17Effort(Estimated Effort){:}
```
