---
title: ABC403 E - Forbidden Prefix
oj: atcoder
contest: ABC403
problem: E
url: https://atcoder.jp/contests/abc403/tasks/abc403_e
submission_url: https://atcoder.jp/contests/abc403/submissions/69221632
date: 2025-09-11
tags:
  - Trie
  - RollingHash
  - String
difficulty: "1447"
status: solved
revisit:
tries:
time_spent:
---

# Statement

# Key Idea
Trieを改造する
# Approach
XもYも同じTrie上で管理する.
Trieの構造に思いを馳せると、X側の要素 (禁止接頭辞) であることを示すbool値を頂点に持たせて、それ以降は立入禁止という感じにすると解けそうとわかる. 実際それでよい.
X側、Y側でinsert操作の勝手が異なることもあり、そこそこ実装が面倒かも.
ちゃんとTrieの構造体を作って、内部を改造するほうが楽だと思う.
# Complexity
Time: $O()$
Memory: $O()$

# Implementation Notes

# Pitfalls

# Similar / Links

# Afterthought
