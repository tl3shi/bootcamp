### 命令列表

- git init
- git status
- git add
- git commit
- git remote
- git push
- git pull
- git log
- git diff
- git clone
- git fetch
- git checkout
- git branch
- git stash
- git merge
- git rebase
- git merge v.s git rebase
- git reset
- git tag
- git blame
- git submodule
- git revert
- git reflog
- git cherry-pick
- *hooks*
- *commit message template*

### git init

```bash
➜  github > mkdir bootcamp1
➜  github > cd bootcamp1
➜  bootcamp1 > git init
Initialized empty Git repository in /Users/TangLei/github/bootcamp1/.git/
```
### git status

```bash
➜  bootcamp1 git:(master)  > git status
# On branch master
#
# Initial commit
#
nothing to commit (create/copy files and use "git add" to track)
➜  bootcamp1 git:(master)  > echo "hello world" >> README.md
➜  bootcamp1 git:(master) ✗  > git st
# On branch master
#
# Initial commit
#
# Untracked files:
#   (use "git add <file>..." to include in what will be committed)
#
#	README.md
nothing added to commit but untracked files present (use "git add" to track)
➜  bootcamp1 git:(master) ✗  >
```
### git add

```bash
➜  bootcamp1 git:(master) ✗  > git add README.md
➜  bootcamp1 git:(master) ✗  > git st
# On branch master
#
# Initial commit
#
# Changes to be committed:
#   (use "git rm --cached <file>..." to unstage)
#
#	new file:   README.md
#
➜  bootcamp1 git:(master) ✗  > git rm --cached README.md
rm 'README.md'
➜  bootcamp1 git:(master) ✗  > git status
# On branch master
#
# Initial commit
#
# Untracked files:
#   (use "git add <file>..." to include in what will be committed)
#
#	README.md
nothing added to commit but untracked files present (use "git add" to track)
➜  bootcamp1 git:(master) ✗  >
```

### git commit

```bash
➜  bootcamp1 git:(master) ✗  > git commit
Aborting commit due to empty commit message.
➜  bootcamp1 git:(master) ✗  > git commit -m "init commit"
[master (root-commit) 0e9e0c0] init commit
 1 file changed, 1 insertion(+)
 create mode 100644 README.md
➜  bootcamp1 git:(master)  > gs
# On branch master
nothing to commit, working directory clean
➜  bootcamp1 git:(master)  >
```

### git remote

```bash
➜  bootcamp1 git:(master)  > git remote -v
➜  bootcamp1 git:(master)  > git remote add origin git@github.com:tl3shi/bootcamp.git
➜  bootcamp1 git:(master)  > git remote -v
origin	git@github.com:tl3shi/bootcamp.git (fetch)
origin	git@github.com:tl3shi/bootcamp.git (push)
```

### git push

```bash
➜  bootcamp1 git:(master)  > git push -u origin master
To git@github.com:tl3shi/bootcamp.git
 ! [rejected]        master -> master (fetch first)
error: failed to push some refs to 'git@github.com:tl3shi/bootcamp.git'
hint: Updates were rejected because the remote contains work that you do
hint: not have locally. This is usually caused by another repository pushing
hint: to the same ref. You may want to first integrate the remote changes
hint: (e.g., 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```

### git pull

类似 ` git fetch && git merge `

```bash
➜  bootcamp1 git:(master)  > git pull origin master
From github.com:tl3shi/bootcamp
 * branch            master     -> FETCH_HEAD
Merge made by the 'recursive' strategy.
➜  bootcamp1 git:(master)  > git push -u origin master
Counting objects: 6, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (4/4), done.
Writing objects: 100% (5/5), 640 bytes | 0 bytes/s, done.
Total 5 (delta 0), reused 0 (delta 0)
To git@github.com:tl3shi/bootcamp.git
   250e2c4..972d990  master -> master
Branch master set up to track remote branch master from origin.
➜  bootcamp1 git:(master)  > git log
➜  bootcamp1 git:(master)  > git log | more
commit 972d990c55707938f6a6d45be8e2d694e7818f42
Merge: e4bd620 250e2c4
Author: tanglei <mac@tanglei.name>
Date:   Sun Aug 13 19:39:39 2017 +0800

    Merge branch 'master' of github.com:tl3shi/bootcamp

commit e4bd6202e9473c82859b0083896fd8d8e7f756d2
Author: tanglei <mac@tanglei.name>
Date:   Sun Aug 13 19:33:56 2017 +0800

    ISSUE: #id-test
    Desc: template test

commit 0e9e0c030a6f10d17b0f9f61e1f839d7c3181528
```

### git log

```bash
➜  bootcamp1 git:(master)  > git log | more
commit 972d990c55707938f6a6d45be8e2d694e7818f42
Merge: e4bd620 250e2c4
Author: tanglei <mac@tanglei.name>
Date:   Sun Aug 13 19:39:39 2017 +0800

    Merge branch 'master' of github.com:tl3shi/bootcamp

commit e4bd6202e9473c82859b0083896fd8d8e7f756d2
Author: tanglei <mac@tanglei.name>
Date:   Sun Aug 13 19:33:56 2017 +0800

    ISSUE: #id-test
    Desc: template test

commit 0e9e0c030a6f10d17b0f9f61e1f839d7c3181528
Author: tanglei <mac@tanglei.name>
Date:   Sun Aug 13 19:30:29 2017 +0800

    init commit

commit 250e2c4a7bb2465f790ce24f430d1c5539e88a69
Author: tanglei <mac@tanglei.name>
Date:   Sun Aug 13 18:38:36 2017 +0800

    init commit
➜  bootcamp1 git:(master)  > git log --graph --all --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' 

*   972d990 - (HEAD, origin/master, master) Merge branch 'master' of github.com:tl3shi/bootcamp (5 minutes ago) <tanglei>
|\
| * 250e2c4 - init commit (66 minutes ago) <tanglei>
* e4bd620 - ISSUE: #id-test Desc: template test (11 minutes ago) <tanglei>
* 0e9e0c0 - init commit (15 minutes ago) <tanglei>
(END)
```

### git diff 

```bash
➜  bootcamp1 git:(master)  > cat README.md
hello world
➜  bootcamp1 git:(master)  > echo "\nHello World" >> README.md
➜  bootcamp1 git:(master) ✗  > git status
# On branch master
# Changes not staged for commit:
#   (use "git add <file>..." to update what will be committed)
#   (use "git checkout -- <file>..." to discard changes in working directory)
#
#	modified:   README.md
#
no changes added to commit (use "git add" and/or "git commit -a")
➜  bootcamp1 git:(master) ✗  > git diff | more
diff --git a/README.md b/README.md
index 3b18e51..d84806d 100644
--- a/README.md
+++ b/README.md
@@ -1 +1,3 @@
 hello world
+
+Hello World
➜  bootcamp1 git:(master) ✗  >
```

### git clone

```bash
➜  github  > mkdir bootcampclone
➜  github  > cd bootcampclone
➜  bootcampclone  > git clone https://github.com/tl3shi/bootcamp .
Cloning into '.'...
remote: Counting objects: 8, done.
remote: Compressing objects: 100% (5/5), done.
remote: Total 8 (delta 1), reused 7 (delta 0), pack-reused 0
Unpacking objects: 100% (8/8), done.
Checking connectivity... done
➜  bootcampclone git:(master)  >

```

### git fetch

```bash
➜  github  > mkdir bootcampfetch
➜  github  > cd bootcampfetch
➜  bootcampfetch  > ls
➜  bootcampfetch  > du -s
0	.
➜  bootcampfetch  > git init
Initialized empty Git repository in /Users/TangLei/github/bootcampfetch/.git/
➜  bootcampfetch git:(master)  > du -s
104	.
➜  bootcampfetch git:(master)  > ls
➜  bootcampfetch git:(master)  > git remote add origin git@github.com:tl3shi/bootcamp.git
➜  bootcampfetch git:(master)  > du -s
104	.
➜  bootcampfetch git:(master)  > git fetch origin master
remote: Counting objects: 8, done.
remote: Compressing objects: 100% (5/5), done.
remote: Total 8 (delta 1), reused 7 (delta 0), pack-reused 0
Unpacking objects: 100% (8/8), done.
From github.com:tl3shi/bootcamp
 * branch            master     -> FETCH_HEAD
 * [new branch]      master     -> origin/master
➜  bootcampfetch git:(master)  > ls
➜  bootcampfetch git:(master)  > du -s
192	.
➜  bootcampfetch git:(master)  >
```

### git checkout

```bash
git checkout -b newBranchName
git checkout existBranchName
git checkout commitHash
git checkout tagName
git checkout -- fileName
```

```bash
➜  bootcampfetch git:(master)  > ll
➜  bootcampfetch git:(master)  > git checkout master
Branch master set up to track remote branch master from origin.
Switched to a new branch 'master'
➜  bootcampfetch git:(master)  > ls
README.md              commit-template.config
```

`git checkout --fileName`: 丢弃工作区的修改, 文件回到最近一次git commit或git add时的状态
`git reset HEAD file`: 暂存区的修改撤销掉（unstage），重新放回工作区

### git branch

```bash
git branch branchName
git checkout -b newBranchName
git branch -d branchName
```

```bash
➜  bootcampfetch git:(master)  > git checkout -b master1
Switched to a new branch 'master1'
➜  bootcampfetch git:(master1)  > ls
README.md              commit-template.config
➜  bootcampfetch git:(master1)  > git branch -D master1
error: Cannot delete the branch 'master1' which you are currently on.
➜  bootcampfetch git:(master1)  > gco maseter
error: pathspec 'maseter' did not match any file(s) known to git.
➜  bootcampfetch git:(master1)  > gco master
Switched to branch 'master'
➜  bootcampfetch git:(master)  > gb
* master                972d990 Merge branch 'master' of github.com:tl3shi/bootcamp
  master1               972d990 Merge branch 'master' of github.com:tl3shi/bootcamp
  remotes/origin/master 972d990 Merge branch 'master' of github.com:tl3shi/bootcamp
➜  bootcampfetch git:(master)  >
```

### git stash

```bash
➜  bootcamp1 git:(master) ✗  > cat README.md
hello world

Hello World
➜  bootcamp1 git:(master) ✗  > sed -i "" 's|hello|world|g' README.md
➜  bootcamp1 git:(master) ✗  > cat README.md
world world

Hello World
➜  bootcamp1 git:(master) ✗  > git status
# On branch master
# Changes not staged for commit:
#   (use "git add <file>..." to update what will be committed)
#   (use "git checkout -- <file>..." to discard changes in working directory)
#
#	modified:   README.md
#
no changes added to commit (use "git add" and/or "git commit -a")
➜  bootcamp1 git:(master) ✗  > git stash
Saved working directory and index state WIP on master: 972d990 Merge branch 'master' of github.com:tl3shi/bootcamp
HEAD is now at 972d990 Merge branch 'master' of github.com:tl3shi/bootcamp
➜  bootcamp1 git:(master)  > git status
...skipping...
# On branch master
nothing to commit, working directory clean
➜  bootcamp1 git:(master)  > vi commit-template.config
➜  bootcamp1 git:(master) ✗  > git status
# On branch master
# Changes not staged for commit:
#   (use "git add <file>..." to update what will be committed)
#   (use "git checkout -- <file>..." to discard changes in working directory)
#
#	modified:   commit-template.config
#
no changes added to commit (use "git add" and/or "git commit -a")
➜  bootcamp1 git:(master) ✗  > git add .
 %                                                                                                                                                    ➜  bootcamp1 git:(master) ✗  > gc "modify"
[master c7c2174] modify
 1 file changed, 1 insertion(+)
➜  bootcamp1 git:(master)  > gp
Counting objects: 5, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 305 bytes | 0 bytes/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To git@github.com:tl3shi/bootcamp.git
   972d990..c7c2174  master -> master
➜  bootcamp1 git:(master)  > git status
# On branch master
nothing to commit, working directory clean
➜  bootcamp1 git:(master)  > git stash list
➜  bootcamp1 git:(master)  > git stash list | more
stash@{0}: WIP on master: 972d990 Merge branch 'master' of github.com:tl3shi/bootcamp
➜  bootcamp1 git:(master)  > git stash list pop
fatal: bad revision 'pop'
➜  bootcamp1 git:(master)  > git stash  pop
# On branch master
# Changes not staged for commit:
#   (use "git add <file>..." to update what will be committed)
#   (use "git checkout -- <file>..." to discard changes in working directory)
#
#	modified:   README.md
#
no changes added to commit (use "git add" and/or "git commit -a")
Dropped refs/stash@{0} (fd7a1174c02b787b92da0cffe426007d17caa628)
➜  bootcamp1 git:(master) ✗  > git status
# On branch master
# Changes not staged for commit:
#   (use "git add <file>..." to update what will be committed)
#   (use "git checkout -- <file>..." to discard changes in working directory)
#
#	modified:   README.md
#
no changes added to commit (use "git add" and/or "git commit -a")
➜  bootcamp1 git:(master) ✗  > cat README.md
world world

Hello World
➜  bootcamp1 git:(master) ✗  >
```

### git merge

```bash
➜  bootcamp git:(master)  > git checkout feature1
Switched to branch 'feature1'
➜  bootcamp git:(feature1)  > git log
➜  bootcamp git:(feature1)  > git log | more
commit 0fab9adebc0db86debdd3a074d31230099774719
Author: tanglei <mac@tanglei.name>
Date:   Sun Aug 13 22:14:06 2017 +0800

    add merge test

commit 250e2c4a7bb2465f790ce24f430d1c5539e88a69
Author: tanglei <mac@tanglei.name>
Date:   Sun Aug 13 18:38:36 2017 +0800

    init commit
➜  bootcamp git:(master)  > git merge feature1
Merge made by the 'recursive' strategy.
 feature | 1 +
 1 file changed, 1 insertion(+)
 create mode 100644 feature
➜  bootcamp git:(master)  > git log | more
commit df856a702953f8fb58190d81346d978ed17cf5d5
Merge: 7ee893b 0fab9ad
Author: tanglei <mac@tanglei.name>
Date:   Sun Aug 13 22:16:23 2017 +0800

    Merge branch 'feature1'

commit 7ee893bf233ee48dc94faa95b59e66be67d34c50
Author: tanglei <mac@tanglei.name>
Date:   Sun Aug 13 22:16:02 2017 +0800

    add main

commit 0fab9adebc0db86debdd3a074d31230099774719
Author: tanglei <mac@tanglei.name>
Date:   Sun Aug 13 22:14:06 2017 +0800

    add merge test

commit 250e2c4a7bb2465f790ce24f430d1c5539e88a69
Author: tanglei <mac@tanglei.name>
Date:   Sun Aug 13 18:38:36 2017 +0800

    init commit
```

### git rebase


```bash
git rebase branchName
git rebase -i commitHash
```

```bash
➜  bootcamp git:(feature1)  > git log | more
commit 0fab9adebc0db86debdd3a074d31230099774719
Author: tanglei <mac@tanglei.name>
Date:   Sun Aug 13 22:14:06 2017 +0800

    add merge test

commit 250e2c4a7bb2465f790ce24f430d1c5539e88a69
Author: tanglei <mac@tanglei.name>
Date:   Sun Aug 13 18:38:36 2017 +0800

    init commit
➜  bootcamp git:(feature1)  > git rebase master
First, rewinding head to replay your work on top of it...
Applying: add merge test
➜  bootcamp git:(feature1)  > gl
➜  bootcamp git:(feature1)  > git log | more
commit dc1328f61feb6055be988e03d7c9f0ecc7c757d4
Author: tanglei <mac@tanglei.name>
Date:   Sun Aug 13 22:14:06 2017 +0800

    add merge test

commit 7ee893bf233ee48dc94faa95b59e66be67d34c50
Author: tanglei <mac@tanglei.name>
Date:   Sun Aug 13 22:16:02 2017 +0800

    add main

commit 250e2c4a7bb2465f790ce24f430d1c5539e88a69
Author: tanglei <mac@tanglei.name>
Date:   Sun Aug 13 18:38:36 2017 +0800

    init commit
```

```
➜  bootcamp git:(feature1)  > git rebase -i 250e2c4a7bb2465f790ce24f430d1c5539e88a69
[detached HEAD f558895] combine: add main && add merge test
 2 files changed, 2 insertions(+)
 create mode 100644 feature
 create mode 100644 main.cpp
Successfully rebased and updated refs/heads/feature1.
➜  bootcamp git:(feature1)  > git log | more
commit f558895c4fa541479182f1a999f217607899c274
Author: tanglei <mac@tanglei.name>
Date:   Sun Aug 13 22:16:02 2017 +0800

    combine: add main && add merge test

    add main

    add merge test

commit 250e2c4a7bb2465f790ce24f430d1c5539e88a69
Author: tanglei <mac@tanglei.name>
Date:   Sun Aug 13 18:38:36 2017 +0800

    init commit
➜  bootcamp git:(feature1)  > ll
total 24
-rw-r--r--  1 tanglei  staff    12B  8 13 18:35 README.md
-rw-r--r--  1 tanglei  staff     8B  8 13 22:22 feature
-rw-r--r--  1 tanglei  staff     5B  8 13 22:22 main.cpp
➜  bootcamp git:(feature1)  >
```

### git merge v.s git rebase

- `git rebase`: Reapply commits on **top** of another base tip
- `git merge --no-ff`: 保留被合并的分支的commits, 默认 fast-forward
- `git merge`: 一次性合并, 解决完冲突后, 再 `add, commit` 会产生一个commit
- `git rebase`: 交互式的, 一个commit 一个commit的进行, 当前冲突需要解决完之后, 再 `git rebase --continue`, 直到所有commits合并完毕, 使得 commit history 美观, 缺点是可能要多次进行冲突解决. 
- `git rebase -i hash` 整理commits信息, 使得更佳美观. 重新排列, 删除, 合并

### git reset

```bash
git reset HEAD
git reset --hard 
```

Reset current HEAD to the specified state

```bash
➜  bootcamp git:(feature1)  > git status
# On branch feature1
nothing to commit, working directory clean
➜  bootcamp git:(feature1)  > git reset 250e2c4
➜  bootcamp git:(feature1) ✗  > git status
# On branch feature1
# Untracked files:
#   (use "git add <file>..." to include in what will be committed)
#
#	feature
#	main.cpp
nothing added to commit but untracked files present (use "git add" to track)
➜  bootcamp git:(feature1) ✗  > git log
➜  bootcamp git:(feature1) ✗  > git log | more
commit 250e2c4a7bb2465f790ce24f430d1c5539e88a69
Author: tanglei <mac@tanglei.name>
Date:   Sun Aug 13 18:38:36 2017 +0800

    init commit
➜  bootcamp git:(feature1) ✗  > git reflog
```

### git tag

```
➜  bootcamp git:(master)  > git tag deploy-v20160908.1
➜  bootcamp git:(master)  > git tag
deploy-v20160908.1
➜  bootcamp git:(master)  > git tag feature1
➜  bootcamp git:(master)  > git tag
deploy-v20160908.1
feature1
➜  bootcamp git:(master)  > git tag -d feature1
```

### git blame

```bash
git blame fileName
```

### git submodule

```bash
git submodule add ...
git submodule update --init --recursive
```

```bash
➜  .vimbak git:(master)  > j .vim
/Users/TangLei/.vim
➜  .vim git:(master) ✗  > git submodule
 48b7ccef76c9f15b8fc0227b5e661eb55e483459 bundle/YouCompleteMe (heads/master)
 4a0dd6e190f446e5a016b44fdaa2feafc582918e bundle/ag.vim (heads/master)
 1f0b972696faca5e8ccb412e691bd9c3c57cdabf bundle/conque-term (heads/master)
 2868678a987834563bbc384763135462c2423eb8 bundle/ctrlp.vim (1.79-282-g2868678)
 fcdd3aee6f4c0eef1a515727199ece8d6c6041b5 bundle/incsearch-easymotion.vim (heads/master)
 161c5b66542e767962ca5f6998a22e984f8d8a60 bundle/incsearch.vim (v2.0.1-29-g161c5b6)
-ced6c409c9beeb0b4142d21906606bd194411d1d bundle/matchit.zip
 ad72976ca3df4585d49aa296799f14f3b34cf953 bundle/minibufexpl.vim (v6.5.2)
 f6befdc80f3e61d0d26734e064a84e5a78ee00cc bundle/neocomplete.vim (ver.2.1-27-gf6befdc)
 b0bb781fc73ef40365e4c996a16f04368d64fc9d bundle/nerdtree (4.2.0-112-gb0bb781)
 00e1e7fcdbc6d753e0bc8043e0d2546fa81bf367 bundle/tabular (1.0.0-1-g00e1e7f)
 7b36c46d17d57db34fdb0adac9ba6382d0bb5e66 bundle/tagbar (v2.6.1-60-g7b36c46)
 11632455de8caa40f264501df8f0a3e249cf0595 bundle/vim-easymotion (v3.0.1-23-g1163245)
 b754bc2031f21a532c083dd0d072ba373bbe3a37 bundle/vim-fugitive (v2.2-74-gb754bc2)
 73710fe6964c2f366682dba3550e2dcec7831949 bundle/vim-go (v1.1-28-g73710fe)
 018298ead9d3aa9cd3b4ae222f81022a33978b09 bundle/vim-indent-guides (1.6-44-g018298e)
 09c0cea859a2e0989eea740655b35976d951a84e bundle/vim-powerline (heads/develop)
 b0608f5887e5d8d61993f20265081943c4ed6187 bundle/vim-scala (heads/master)
 e49d6c2459e0f5569ff2d533b4df995dd7f98313 bundle/vim-surround (v2.1-9-ge49d6c2)
 7190c920c29a3612d9144df4cf9527e016362cef bundle/vimproc.vim (ver.8.0-26-g7190c92)
 a1f9a2010bea4b109341f1e2411a32839a8547b3 bundle/vimshell.vim (ver.9.2-321-ga1f9a20)
-e2baded7162260e05d2527f5bca9fca81f0bc8f2 bundle/wildfire.vim
➜  .vim git:(master) ✗  > cat submodule.sh
git submodule add https://github.com/Valloric/YouCompleteMe.git	bundle/YouCompleteMe
git submodule add https://github.com/rking/ag.vim.git	bundle/ag.vim
git submodule add https://github.com/rosenfeld/conque-term.git	bundle/conque-term
git submodule add https://github.com/ctrlpvim/ctrlp.vim.git	bundle/ctrlp.vim
git submodule add https://github.com/haya14busa/incsearch-easymotion.vim.git	bundle/incsearch-easymotion.vim
git submodule add https://github.com/haya14busa/incsearch.vim.git	bundle/incsearch.vim
git submodule add https://github.com/fholgado/minibufexpl.vim.git	bundle/minibufexpl.vim
git submodule add https://github.com/Shougo/neocomplete.vim.git	bundle/neocomplete.vim
git submodule add git://github.com/scrooloose/nerdtree.git	bundle/nerdtree
git submodule add https://github.com/majutsushi/tagbar.git	bundle/tagbar
git submodule add https://github.com/easymotion/vim-easymotion.git	bundle/vim-easymotion
git submodule add https://github.com/tpope/vim-fugitive	bundle/vim-fugitive
git submodule add https://github.com/fatih/vim-go.git	bundle/vim-go
git submodule add https://github.com/nathanaelkane/vim-indent-guides	bundle/vim-indent-guides
git submodule add https://github.com/Lokaltog/vim-powerline.git	bundle/vim-powerline
git submodule add https://github.com/derekwyatt/vim-scala.git	bundle/vim-scala
git submodule add https://github.com/tpope/vim-surround.git	bundle/vim-surround
git submodule add https://github.com/Shougo/vimproc.vim.git	bundle/vimproc.vim
git submodule add git@github.com:Shougo/vimshell.vim.git	bundle/vimshell.vim
```


### git revert

```
Note: git revert is used to record some new commits to reverse the effect of some earlier commits (often only a faulty one). 
If you want to throw away all uncommitted changes in your working directory, you should see git-reset[1], particularly the --hard option. 
If you want to extract specific files as they were in another commit, you should see git-checkout[1], specifically the git checkout <commit> -- <filename> syntax. 
Take care with these alternatives as both will discard uncommitted changes in your working directory.
```

### git reflog

```
Reference logs, or "reflogs", record when the tips of branches and other references were updated in the local repository
```


### git cherry-pick 

```bash
➜  bootcamp git:(master) for i in `seq 1 10`
do
    echo $i > $i.txt; git add $i.txt && git commit -m "add $i"
done
➜  bootcamp git:(master) git log --pretty=oneline | more
8135307ff8cd20661e7d0b9e5ba77fea07c93d11 add 10
4c287a5449eb466faa1759042ed93925cc35f8b8 add 9
28123404b8d80cfe9fbf9cd44fa8bb7bfec75233 add 8
d3b44faa821fc04dce9eb6d473f666c923ad81a6 add 7
b72f5a07d7eb5a785eb1bf58fb84fd1e15b0cb57 add 6
c337597d6268c227725fe6dbc81d721a7e6460de add 5
9a7641b699b04c0cfe6d63081778977a3a5b66e8 add 4
80243f79a84681be417e505da53065ac0e0d6d7f add 3
f5857657613ecd97e3516eb599a8ff7491772294 add 2
7cc9a961271ab156d5185cd087ba85abf2851261 add 1
c7c21743846b4ebe939753b65f6e1cd4670112da modify
972d990c55707938f6a6d45be8e2d694e7818f42 Merge branch 'master' of github.com:tl3shi/bootcamp
e4bd6202e9473c82859b0083896fd8d8e7f756d2 ISSUE: #id-test Desc: template test
0e9e0c030a6f10d17b0f9f61e1f839d7c3181528 init commit
250e2c4a7bb2465f790ce24f430d1c5539e88a69 init commit

➜  bootcamp git:(master) gco feature
Switched to branch 'feature'
➜  bootcamp git:(feature) git log --pretty=oneline | more
c7c21743846b4ebe939753b65f6e1cd4670112da modify
972d990c55707938f6a6d45be8e2d694e7818f42 Merge branch 'master' of github.com:tl3shi/bootcamp
e4bd6202e9473c82859b0083896fd8d8e7f756d2 ISSUE: #id-test Desc: template test
0e9e0c030a6f10d17b0f9f61e1f839d7c3181528 init commit
250e2c4a7bb2465f790ce24f430d1c5539e88a69 init commit
➜  bootcamp git:(feature) ll
total 16
-rw-r--r--  1 tanglei  staff    12B Aug 14 11:55 README.md
-rw-r--r--  1 tanglei  staff    26B Aug 14 11:55 commit-template.config
➜  bootcamp git:(feature) git cherry-pick 28123404b8d80cfe9fbf9cd44fa8bb7bfec75233
[feature db677fe] add 8
 Date: Mon Aug 14 12:01:17 2017 +0800
 1 file changed, 1 insertion(+)
 create mode 100644 8.txt
➜  bootcamp git:(feature) git log --pretty=oneline | more
db677fe557c1403c9df92513dc907c4288c9e5da add 8
c7c21743846b4ebe939753b65f6e1cd4670112da modify
972d990c55707938f6a6d45be8e2d694e7818f42 Merge branch 'master' of github.com:tl3shi/bootcamp
e4bd6202e9473c82859b0083896fd8d8e7f756d2 ISSUE: #id-test Desc: template test
0e9e0c030a6f10d17b0f9f61e1f839d7c3181528 init commit
250e2c4a7bb2465f790ce24f430d1c5539e88a69 init commit
➜  bootcamp git:(feature) ll
total 24
-rw-r--r--  1 tanglei  staff     2B Aug 14 12:05 8.txt
-rw-r--r--  1 tanglei  staff    12B Aug 14 11:55 README.md
-rw-r--r--  1 tanglei  staff    26B Aug 14 11:55 commit-template.config
➜  bootcamp git:(master) git rebase -i 7cc9a961271ab156d5185cd087ba85abf2851261
[detached HEAD 260c381] combine 2 to 10 add 2
 Date: Mon Aug 14 12:01:17 2017 +0800
 9 files changed, 9 insertions(+)
 create mode 100644 10.txt
 create mode 100644 2.txt
 create mode 100644 3.txt
 create mode 100644 4.txt
 create mode 100644 5.txt
 create mode 100644 6.txt
 create mode 100644 7.txt
 create mode 100644 8.txt
 create mode 100644 9.txt
Successfully rebased and updated refs/heads/master.
➜  bootcamp git:(master) git status
On branch master
Your branch is ahead of 'origin/master' by 2 commits.
  (use "git push" to publish your local commits)
nothing to commit, working tree clean
➜  bootcamp git:(master) git log
➜  bootcamp git:(master) git log --pretty=oneline | more
260c38189849e692ec38acd937076a3151bccb23 combine 2 to 10 add 2
7cc9a961271ab156d5185cd087ba85abf2851261 add 1
c7c21743846b4ebe939753b65f6e1cd4670112da modify
972d990c55707938f6a6d45be8e2d694e7818f42 Merge branch 'master' of github.com:tl3shi/bootcamp
e4bd6202e9473c82859b0083896fd8d8e7f756d2 ISSUE: #id-test Desc: template test
0e9e0c030a6f10d17b0f9f61e1f839d7c3181528 init commit
250e2c4a7bb2465f790ce24f430d1c5539e88a69 init commit
➜  bootcamp git:(master)
```


### hooks

```bash
ls .git/hooks
cat .git/hooks/pre-commit
```
 
### commit message template

```bash
➜  bootcamp git:(master) > git config commit.template commit-template.config
➜  bootcamp1 git:(master)  > cat commit-template.config
ISSUE: #id
Desc:
➜  bootcamp1 git:(master) ✗  > git commit
[master e4bd620] ISSUE: #id-test Desc: template test
 1 file changed, 2 insertions(+)
 create mode 100644 commit-template.config
➜  bootcamp1 git:(master)  > git log | cat
commit e4bd6202e9473c82859b0083896fd8d8e7f756d2
Author: tanglei <mac@tanglei.name>
Date:   Sun Aug 13 19:33:56 2017 +0800

    ISSUE: #id-test
    Desc: template test

commit 0e9e0c030a6f10d17b0f9f61e1f839d7c3181528
Author: tanglei <mac@tanglei.name>
Date:   Sun Aug 13 19:30:29 2017 +0800

    init commit
➜  bootcamp1 git:(master)  >
```