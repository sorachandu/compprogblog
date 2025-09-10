---
title: ABC422 E - Colinear
oj: atcoder
contest: ABC422
problem: E
url: https://atcoder.jp/contests/abc422/tasks/abc422_e
submission_url: https://atcoder.jp/contests/abc422/submissions/69191170
date: 2025-09-10
tags:
  - 幾何
  - 乱択
difficulty:
status: solved
revisit:
tries:
time_spent:
---

# Statement
二次元平面上にN個の点がある. 過半数の点を通る直線があるか判定し、あればax+by+c=0の形でのa,b,cを出力.
# Key Idea
条件を満たす直線があるなら適当にやってもすぐ見つかる
# Approach
ざっくりいえば、条件を満たす直線が存在する場合、無作為に選んだ一点が答えの直線に含まれる確率は $\frac{1}{2}$ 以上.
よって無作為に2点選んでも、低くとも $\frac{1}{4}$ で2点とも答えの直線に含まれることになる.
これを逆手に取ると、適当に選んだ2点を結んで得られる直線が条件を満たす確率は25%以上ということになる.
25%で成功する試行は32回程度行えば99.99%以上の確率で1回は成功するので、無作為に選出した2点から得られる直線を調べ続けるのはほぼ確定的アルゴリズムとみなせる.

2点から直線の方程式を得る公式はこの通り. [参考文献](https://manabitimes.jp/math/894)
$$(x_2-x_1)(y-y_1)=(y_2-y_1)(x-x_1)$$
…数弱なのでこれだけでは残念ながらピンとこない. 紙上で手を動かすとわかると思う.
$dx=x_2-x_1, dy=y_2-y_1$ として、
$$a=-dy, b=dx, c=-dx*y_1+dy*x_1$$
という感じに求まる.

あとはこの式をN個の点で代入して\==0となる個数を調べればok.
一回の試行で $O(N)$ かかり、100回も実行すれば十分正解できるので、解けた.
# Complexity
Time: $O()$
Memory: $O()$

# Implementation Notes

# Pitfalls

# Similar / Links

# Afterthought
ABC、それも450点のE問題で乱択想定が出てくるんだなぁという感想.
こどふぉで見たことはあったし、ちゃんと考えてたら解けてたかもかなぁ…
とりあえず直線の方程式を求めるパートで苦戦しすぎでワロタ