~/.gitconfigに以下を追加

```
[includeIf "gitdir:~/.ghq/github.com/"]
  path = ~/.gitconfig-private
```

以下のように `gitconfig-private` を作成

```
[user]
  name = hoge
  email = hoge@gmail.com
```
