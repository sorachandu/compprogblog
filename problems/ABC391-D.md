---
title: ABC391 D - Gravity
oj: atcoder
contest: ABC391
problem: D
url: https://atcoder.jp/contests/abc391/tasks/abc391_d
submission_url: https://atcoder.jp/contests/abc391/submissions/69197346
date: 2025-09-10
tags:
  - 前処理
difficulty: "924"
status: solved
revisit:
tries:
time_spent:
---

# Statement

# Key Idea
クエリ先読み+時系列順に処理するのでなく、一気に前処理してやる
# Approach
ブロック総数はN個なので、削除イベントは筋の悪い方針でなければ $O(N)$ くらいで間に合うんだろな～というのが取っ掛かりポイント.
第一感としてはクエリ先読みして時刻を進めながら処理するものを思い浮かべてしまう(気がする)が、そうするとかなり処理が全体的に面倒. 実装自体もそうだし頭も壊れる
クエリ関係なく、とりあえず各ブロックが消滅する時刻をシミュレートするとよい.

各列の現在最下層にあるブロックが地上に落ちてきて出揃うまでの時間を考える. これは各列最下層ブロックの高さのmaxを取ればそれが答えになっている.
よって各列に適切な順番でブロックを詰めて、あとは $O(W)$ で各列の最下層を調べればよい. どこかで空な列があれば即終了. これなら十分高速に動作する.
最下層ブロックが消えることでその上にあったブロック達がどうなるかという話だが、よく考えてみると何も影響はしない. 面倒な時刻差分管理などの必要はない.

以上の手続きで各ブロックが消滅する時刻はわかっているので、クエリは容易に答えられる. よって解けた.
# Complexity
Time: $O()$
Memory: $O()$

# Implementation Notes

# Pitfalls

# Similar / Links

# Afterthought
だいぶ実装方針ゲーだと思う. 時系列順にシミュレートしつつクエリに答える方針をすると考えることが多くてカス.