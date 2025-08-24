---
title: ABC420 E - Reachability Query
oj: atcoder
contest: ABC420
problem: E
url: https://atcoder.jp/contests/abc420/tasks/abc420_e
submission_url: https://atcoder.jp/contests/abc420/submissions/68764921
date: 2025-08-25
tags:
  - DSU
difficulty: "790"
status: solved
revisit:
tries:
time_spent: 12 min
---

# Statement

# Key Idea
- 代表元だけ参照、シミュレーションすることで高速化する
# Approach
とりあえず明らかにDSUを使いましょうという顔をしているので、考えたくなる. 雑すぎるだろという感じだが、辺が最初なくて、辺追加クエリが飛んできて、答えるものが結局連結性なので、そういうところから直感でわかる.
結局、クエリ3は頂点vと、ある黒色の頂点とが連結か判定すればよいことになる. 今黒色の頂点集合をSとしたら、$S \exists a$
# Complexity
Time: $O()$
Memory: $O()$

# Implementation Notes

# Pitfalls

# Similar / Links

# Afterthought
