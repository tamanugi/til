今まで(多分)問題なく動いていたのに
急に以下のエラーがでるようになった

```
(Spacemacs) Error in dotspacemacs/user-config: Symbol’s value as variable is void: org-agenda-custom-commands
```

`org-agenda-custom-commnads`の指定の仕方が悪いっぽい

変更前

```
(add-to-list 'org-agenda-custom-commands
              '("D" agenda ""
                ( ;; 1日分だけ表示する
                 (org-agenda-span 1)
                 ;; agenda各行の行頭のスペースをなくす
                 (org-agenda-prefix-format '((agenda . "%?-12t% s")))
                 ;; グリッドを表示しない
                 (org-agenda-use-time-grid nil)
                 ;; clockを表示する
                 (org-agenda-start-with-log-mode t)
                 (org-agenda-show-log 'clockcheck)
                 ;; clockの総計を表でまとめる
                 (org-agenda-start-with-clockreport-mode t)
                 (org-agenda-clockreport-mode t))))
```

変更後

```
  (setq org-agenda-custom-commands
               '("D" agenda ""
                 ( ;; 1日分だけ表示する
                  (org-agenda-span 1)
                  ;; agenda各行の行頭のスペースをなくす
                  (org-agenda-prefix-format '((agenda . "%?-12t% s")))
                  ;; グリッドを表示しない
                  (org-agenda-use-time-grid nil)
                  ;; clockを表示する
                  (org-agenda-start-with-log-mode t)
                  (org-agenda-show-log 'clockcheck)
                  ;; clockの総計を表でまとめる
                  (org-agenda-start-with-clockreport-mode t)
                  (org-agenda-clockreport-mode t))))
```