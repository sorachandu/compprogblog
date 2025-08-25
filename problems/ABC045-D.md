---
title: ABC045 D - Snuke's Coloring
oj: atcoder
contest: ABC045
problem: D
url: https://atcoder.jp/contests/abc045/tasks/abc045_d
submission_url: https://atcoder.jp/contests/abc045/submissions/68810780
date: 2025-08-25
tags: []
difficulty: "1682"
status: solved
revisit:
tries:
time_spent: 25 min
---

# Statement

# Key Idea
・寄与を考える
# Approach
マス範囲がデカいが、Nは普通なのでNに関する計算量なんだろうなぁと目途が立つ.
一つの黒マスに着目したとき、そのマスが含まれる3x3正方領域は高々9個. よってcnt=0でない領域の個数も高々9N個ということになって、数えられるのがわかる.
実装上は、あるマスについてそれが含まれる領域9候補を全探索(領域左上の点を固定)し、その領域がvalidか、黒色を何個含むかをcountしてやればよい.
左上の点をhashSetで管理してやれば、重複countを防げる. $O(N)$で高速. 実際は18とhashSet分の定数倍がかかっているが.
# Complexity
Time: $O(N)$
Memory: $O(N)$

# Implementation Notes
領域ベースに考えていたが、点に対するhashMapを持って「ある点に対しそれを含む正方領域左上の点を列挙し、その点にMap[点]++」でも解ける. こっちのほうが実装の楽さも計算量もよい.
# Pitfalls

# Similar / Links

# Afterthought
