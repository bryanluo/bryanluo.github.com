---
layout: category
title: "git branch 管理"
categories:
  - Linux
tags:
  - git
last_modified_at: 2020-10-18 17:06
---

git branch 常用命令管理

---

### 创建分支

> git branch branch-name

```bash
(base) shijiang@Server shij-note % git branch shij-note-cli-1.0
(base) shijiang@Server shij-note % git branch
* master
  shij-note-cli-1.0
  vue-code
```

### 切换分支

> git checkout branch-name

```bash
(base) shijiang@Server shij-note % git checkout shij-note-cli-1.0
Switched to branch 'shij-note-cli-1.0'
```

### 同步远程分支

>  git push --set-upstream origin develop

### 创建新分支并且切换到该分支

> git checkout -b new-branch-name

```bash
(base) shijiang@Server shij-note % git checkout -b test
Switched to a new branch 'test'
```

### 删除分支

> git branch -d branch-name

### 合并

> git merge branch-name

```bash
(base) shijiang@Server test % git branch 
  master
* test
(base) shijiang@Server test % git checkout master
Switched to branch 'master'
Your branch is up to date with 'origin/master'.
(base) shijiang@Server test % git branch
* master
  test
(base) shijiang@Server test % git merge test
Updating 9bc3e4f..3c13656
Fast-forward
 t/t.txt  | 1 +
 test.txt | 1 +
 2 files changed, 2 insertions(+)
 create mode 100644 t/t.txt
 create mode 100644 test.txt
(base) shijiang@Server test % git push
Total 0 (delta 0), reused 0 (delta 0)
To github.com:timesJ/test.git
   9bc3e4f..3c13656  master -> master
(base) shijiang@Server test % 
```


### 删除分支

```bash
  git branch -D test-shijiang
  
  git push upstream --delete test-shijiang
```
