---
title: PAST004 M - 筆塗り
oj: atcoder
contest: PAST004
problem: M
url: https://atcoder.jp/contests/past202010-open/tasks/past202010_m
date: 2025-08-23
tags:
  - DSU
  - LCA
  - Tree
  - Data-Structure
rating:
status: solved
revisit:
tries:
time_spent: 2 day?
---

# TL;DR
LCA+DSU+クエリ逆読み。
https://atcoder.jp/contests/past202010-open/submissions/68720914

# Statement
N頂点の木がある.
(u,v)間のパスに含まれる辺をc色に染めるクエリがたくさん飛んでくるので、全操作終了後の各辺の色を答えよ.

# Key Idea
* 更新操作なので、逆から見ると各辺高々一回で済む
* LCAを用いて操作を単純化する
* DSUで更新操作を高速化

# Approach
各辺の色を更新なので、クエリ逆読みすると各辺への更新は高々一回で済む.
また、u,vのパスを辿る操作をしようと思うと複雑なので、LCAを用いて言い換えする:
	u,vそれぞれを始点に、LCAまで辿っていく. その過程で通った辺に色を塗る.
これだけでは結局、各辺を愚直に辿っているので最悪計算量がクエリあたり$O(N)$になり、まずい.

既に色が塗られている辺は見る必要がないから、そのような辺たちは飛ばしたい.
ここで、既に色を塗った辺の端点同士をDSUでmergeしてやっておき、各成分の代表元を最も根に近いものとする.
すると、既に塗られている部分に来たらDSU.rootで一気にスキップできるので、全体的には高速化できる.

と、ここまでのアイデアのうち、DSUを使う部分以外は割と自然に出てくる部分だとは思う.
問題は実装で、DSUの代表元を根に近い側にmergeできるようにしたり (Union by Sizeをする実装、例えば`atcoder:⁠:dsu`だと不可能)、頂点ではなく辺を管理する必要があるためLCAで辺も管理しておかなければならない.

# Complexity
Time: $O(NlogN + Q)$
Memory: $O(NlogN)$

# Implementation Notes
LCAもDSUも所持していたが、どっちも微妙に対応してない感じだったので

# Pitfalls / WA Cause

# Similar / Links

# Afterthought
復習で気づいた改善。