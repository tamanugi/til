# hub コマンドについて

## インストール

```
$ brew install hub
```

## 使い方

```
$ hub {command}
```

コマンド一覧

|command|説明|
|:------|:---|
|alias|show shell instructions for wrapping git|
|browse|browse the project on GitHub|
|compare|lookup commit in GitHub Status API|
|create|create new repo on GitHub for the current project|
|fork|fork origin repo on GitHub|
|pull-request|open a pull request on GitHub|
|ci-status|display GitHub Status information for a commit|

## fish 補完

```
curl -o ~/.config/fish/completions/hub.fish https://raw.githubusercontent.com/github/hub/master/etc/hub.fish_completion
```

## その他

- 一度 hub create などでユーザ名, パスワードを入力すると `~/.config/hub` が作成される
