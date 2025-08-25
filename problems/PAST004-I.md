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
  - 三分探索
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
ざっくりとグラフを考えると、ある地点を境に折れる形だろうと見当がつく(絶対値だし). 
また左端を右に動かすと対応する最適な右端も必ず右に行く (というか左に逆行しない).
ということで尺取り法だったり三分探索したりが通用しそう.　自分は三分探索は出てこなかったけど.
好きな方法でやればよい. 自分は嫌いな尺取り法を実装してバグり散らかして禿げました.
# Complexity
Time: $O(N)$
Memory: $O(N)$
# Implementation Notes

# Pitfalls

# Similar / Links

# Afterthought
