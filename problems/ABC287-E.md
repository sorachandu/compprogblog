---
title: ABC287 E - Karuta
oj: atcoder
contest: ABC287
problem: E
url: https://atcoder.jp/contests/abc287/tasks/abc287_e
submission_url: https://atcoder.jp/contests/abc287/submissions/69219857
date: 2025-09-11
tags:
  - Trie
  - String
difficulty: "1093"
status: solved
revisit:
tries:
time_spent:
---

# Statement

# Key Idea
Trie上で辿る
# Approach
N個の文字列からTrieを構築して、そのTrieを辿って見ればよい.
Trieを辿っていくことでその文字をprefixに持つ文字列の個数が全体 $O(|S|)$ で求まる.
個数が1個以下になるような頂点まで行くと終了で、辿れた個数が答え.
Trieの実装がキモになるが、これはポインタで実装する方法のテンプレとかを学んでおくとよいかも.
# Complexity
Time: $O()$
Memory: $O()$

# Implementation Notes

# Pitfalls

# Similar / Links

# Afterthought
