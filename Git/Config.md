# Git Config

```
[user]
	name = 
	email = 
	signingkey = 
[core]
	excludesFile = ~/.gitignore
	ignorecase = false
[commit]
	gpgsign = true
```

```shell
git config --global gpg.program "$(which gpg)"
```