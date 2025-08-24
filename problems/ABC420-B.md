---
title: ABC420 B - Most Minority
oj: atcoder
contest: ABC420
problem: B
url: https://atcoder.jp/contests/ABC420/tasks/ABC420_b
date: 2025-08-24
tags:
  - Brute-force
difficulty: "74"
status: solved
revisit:
tries:
time_spent:
---

# TL;DR
問題文通りにやる
https://atcoder.jp/contests/abc420/submissions/68741773

# Statement
N人がM回、0か1で投票した. 各回の投票で少数派側の人たちは1点加点される.
M回目の投票終了後、得点が最も高い人を昇順に出力せよ.

# Key Idea
- 二重for

# Approach
問題文に厳密なルールを与えられているので、それをさっさと実装してしまうのが楽だと思う.
データの与えられ方(縦と横の向き)にだけ注意して二重forを書けばよい.

# Complexity
Time: $O(NM)$
Memory: $O(NM)$

# Implementation Notes

# Pitfalls

# Similar / Links

# Afterthought
