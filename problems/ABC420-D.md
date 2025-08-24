---
title: ABC420 D - Toggle Maze
oj: atcoder
contest: ABC420
problem: D
url: https://atcoder.jp/contests/abc420/tasks/abc420_d
submission_url: https://atcoder.jp/contests/abc420/submissions/68759274
date: 2025-08-24
tags:
  - BFS
  - 頂点倍化
  - Grid
difficulty: "699"
status: solved
revisit:
tries:
time_spent: 10 min
---

# Statement
スタートとゴールと障害物とドアとスイッチが存在するグリッド上を最短で歩きたい.
ドアには開閉の二種がある. スイッチの上に立つと全ドアの状態が反転する.
# Key Idea
頂点倍化してスイッチを押した押してないに対応付け、BFS.
# Approach
スイッチを押したか押していないかの状態によって通れるマスが変わってくるので、ここは区別して考えたい気持ちになる.
このスイッチの状態は2種類しかないから、それぞれを独立に保持しても2HWとなってサイズとしては問題ない. 俗に**頂点倍化**と呼ばれるテクだと思う.
あとはまぁ、丁寧にBFSをやればよい. スイッチの状態と位置(y,x)とで特に工夫せずに持つと3変数あるので、データの持ち方にだけ注意. 自分はstructを作った.
# Complexity
Time: $O(HW)$
Memory: $O(HW)$

# Implementation Notes

# Pitfalls
queueに{start}を突っ込んだのにdist\[0]\[0]\[0]と初期化してて終わった. ペナ合わせて17分ロス.
手癖に任せて無思考で書くのは高速になるのでいいが、あまりにも無思考すぎた. 12分かけて発見してるのも遅すぎてやばいな…

# Similar / Links

# Afterthought
