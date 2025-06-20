---
layout: default
title: git 中cherry pick 使用注意事项
description: git 中cherry pick 使用注意事项
---

# 如果当前分支后续需要进行merge，则需谨慎使用git 中的cherry pick

branch 1:的提交历史如下:
commit 2 (remove file) 2025:18:01
commit 1 (add  file) 2025:18:00

2025:18:02时 在 branch 2 上cherry pick branch 1 的 commit 1；
然后将branch 1 merge 到 branch 2 ，此时branch 2 会存在 file 文件 
