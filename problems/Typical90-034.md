---
title: Typical90 034 - There are few tipes of elements
oj: atcoder
contest: Typical90
problem: 34
url: https://atcoder.jp/contests/typical90/tasks/typical90_ah
submission_url: https://atcoder.jp/contests/typical90/submissions/69628336
date: 2025-09-27
tags:
  - 尺取り法
difficulty: "1199"
status: solved
revisit:
tries:
time_spent:
---

# Statement

# Key Idea
A[i]の範囲がデカいので種類を固定しないんだろうな～とかで着想　連続部分列だし尺取り法でいいんじゃないですか的な
# Approach
↑の通り　連続部分列の長さなので尺取り法を検討するとして、実際種類数も一回動かすごとに高々1しか変化しないので、いい感じにシミュレーションできそうですねという話。
尺取り法であるとわかればそれ以上に言うことがない。別に実装自体も尺取り法の基本であるため特にコメントなし。尺取り法の書き方だけ困る (今回はdequeで書いた)
# Complexity
Time: $O(NlogN)$
Memory: $O()$

# Implementation Notes

# Pitfalls

# Similar / Links

# Afterthought
