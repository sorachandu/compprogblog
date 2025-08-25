---
title: PAST004 I - ピザ
oj: atcoder
contest: PAST004
problem: I
url: https://atcoder.jp/contests/past202010-open/tasks/past202010_i
submission_url: https://atcoder.jp/contests/past202010-open/submissions/68795380
date: 2025-08-25
tags:
  - 尺取り法
  - 円環
difficulty:
status: solved
revisit:
tries:
time_spent:
---

# Statement

# Key Idea
- 尺取り法
# Approach
円環上で処理させられるので、2N要素にしておくと楽なやつ.
ある区間を取ったときの値を考える問題だし、とりあえず区間の左端を固定してみる.
すると右端も全探索すると$O(N^2)$でやばいが、明らかに最適な右端はもっと賢く見つかるだろという直感(?)が働く.

総和だし二分探索で見つかる…というわけではなく、目的関数は$|X-Y|$であるから、単調性がないことがわかる.
ざっくりとグラフを考えると、ある地点を境に
# Complexity
Time: $O()$
Memory: $O()$

# Implementation Notes

# Pitfalls

# Similar / Links

# Afterthought
