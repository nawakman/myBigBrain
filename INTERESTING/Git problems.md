[[INTERESTING]]

```
git branch -d theo
git checkout -b theo
git pull --rebase origin theo
git push -u origin theo
```

Resolve merge conflict locally
```
git fetch origin
git checkout -b branchToMerge
git rebase main
git rebase -X ours target-branch //keep our files for all conflicts
OR
git checkout --ours path/to/file
OR git add path/to/file //after manually editing file
git rebase --continue
then commit and push
```