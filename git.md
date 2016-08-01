Git
===

Remotes
-------

Add remote:

```bash
git remote add remote_name url
```

List remotes:

```bash
git remote -v
```

Remove remote:

```bash
git remote rm remote_name
```

Delete local and remote branch:

```bash
# delete local branch
git branch -d local_branch
# delete remote branch
git push origin :remote_branch
```

Staging
-------

Revert file:

```bash
git checkout file
```

Unstage file:

```bash
git reset HEAD file
```

Stashing
--------

Stash current work:

```bash
git stash
```

Apply latest stash:

```bash
git stash apply
```

Apply latest stash and also drop it from stashes:

```bash
git stash pop
```

Delete all stashes:

```bash
git stash clear
```

Tagging
-------

List tags:

```bash
git tag
```

Create v1.0 tag:

```bash
git tag -a v1.0 -m "Version 1.0"
```

Delete v1.0 tag:

```bash
git tag -d v1.0
git push origin :v1.0
```
