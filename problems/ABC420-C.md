---
title: ABC420 C - Sum of Min Query
oj: atcoder
contest: ABC420
problem: C
url: https://atcoder.jp/contests/ABC420/tasks/ABC420_c
date: 2025-08-24
tags:
  - 差分管理
difficulty: "169"
status: solved
revisit:
tries:
time_spent:
---

# TL;DR
https://atcoder.jp/contests/abc420/submissions/68747157
操作毎の差分を考えて高速化.

# Statement
N要素の数列A,Bがある. Q回クエリを処理せよ:
A[x]かB[x] (指定される) をvに置き換える. その後、$\sum_{k=1}^N \min(A[k],B[k])$ を出力せよ.
# Key Idea
差分
# Approach
一点変更なので、変更された部分だけ再計算して寄与の差分を考えればよい.
具体的には、$\min(v,B[x] - \min(A[x],B[x])$ を寄与として加算すればよい. Bが変更される場合もほぼ同様.
# Complexity
Time: $O(N+Q)$
Memory: $O(N)$

# Implementation Notes

# Pitfalls
変更前がmin側だったときにだけ処理するようにしていた. 改めて考えたらだいぶよくわからんミスに思う.
丁寧に変更操作が及ぼす影響について考察すれば、こうならない気がする.
# Similar / Links

# Afterthought
