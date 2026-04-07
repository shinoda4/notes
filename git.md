
```shell
git commit
git checkout
git switch -c new_branch

git merge
git rebase

cat .git/HEAD
git symbolic-ref HEAD

git switch main^
git switch HEAD^^
git switch HEAD~4

# 这条命令会将 main 分支强制指向 HEAD 的第 3 级 parent 提交
git branch -f main HEAD~3

git reset HEAD^
git revert HEAD

git cherry-pick C2 C4
```
