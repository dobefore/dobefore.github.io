---
title: git常用命令
readmore: true
date: 2022-04-01 09:57:58
tags: git
---

### config user

```none
git config --global user.name "dobefore"
git config --global user.email 1432338032@qq.com
```



### Tag

create local tag
`git tag 0.1.2`
push tag to remote
`git push origin 0.1.2`

### fetch and checkout to other people’s pull request

```none
#To fetch a remote PR into your local repo,
git fetch origin pull/PRID/head:BRANCHNAME

git checkout BRANCHNAME
```