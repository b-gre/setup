# Git stuff

## Nice diffs & more

```shell
sudo dnf install git-delta && \
git config --global core.pager delta && \
git config --global delta.navigate true && \
git config --global delta.light false && \
git config --global merge.conflictstyle diff3
```

## Easier fixing with rebase
```shell
git config --global rebase.autosquash true && \
git config --global rebase.autoStash true
```

Then
```shell
git commit --fixup=$HASH  # Fix the previous commit with $HASH
git rebase -i $BASE 
```
