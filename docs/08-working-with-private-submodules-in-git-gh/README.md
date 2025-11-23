# Configuring git and gh for use with private submodules (aka files repo)

> This guide is how to work with private submodules in git on github when working with a windows computer that’s limited in permissions.
>
> We’ll be building the files repo from scratch in this doc.

---

## Make sure that sync has run

This includes installing `git`, `gh` with `scoop`.

## Make sure you gitconfig is correct.

I ideally want my git config being read from: `~/.config/git/config`. 

If it’s being read from: `~/.gitconfig` this is the wrong file.

---

## Make sure that the submodule settings in the the gitconfig are correct

*More on this later!!*

## Config `gh` auth login

```powershell
gh config set -h github.com git_protocol https
```

or just

```
gh auth login
```

and follow the prompts.

## 







