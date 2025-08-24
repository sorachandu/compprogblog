---
title: ABC420 A - What month is it?
oj: atcoder
contest: ABC420
problem: A
url: https://atcoder.jp/contests/abc420/tasks/abc420_a
date: 2025-08-24
tags: []
rating: "10"
status: solved
revisit:
tries:
time_spent: 1 min
---

# TL;DR
場合分け
https://atcoder.jp/contests/abc420/submissions/68734457

# Statement
X月のY月後は何月か?

# Key Idea
* 

# Approach
X+Yすればよいが、13月以降になると困るので、その場合は12を引けばよい.

また、[解説](https://atcoder.jp/contests/abc420/editorial/13754) によると、N\%Mを1以上M以下の範囲にするには$(N-1)\%M+1$でよいらしい.
よって(x+y-1)%12+1でも解けるらしい.

# Complexity
Time: $O(1)$
Memory: $O(1)$

# Implementation Notes

# Pitfalls / WA Cause

# Similar / Links

# Afterthought
