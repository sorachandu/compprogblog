---
title: ABC420 E - Reachability Query
oj: atcoder
contest: ABC420
problem: E
url: https://atcoder.jp/contests/abc420/tasks/abc420_e
submission_url: https://atcoder.jp/contests/abc420/submissions/68764921
date: 2025-08-24
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
結局、クエリ3は頂点vと、ある黒色の頂点とが連結か判定すればよいことになる. 今黒色の頂点集合をSとしたら、$\exists a \in S, \{v,a\}\, is\, same?$ という感じだと思う.

となるとDSUの仕組みそのまま考えると、連結成分の代表元に思いを馳せたくなる. 代表元に黒色が存在するか否かの情報を持たせられるなら、答えられそう.
これは各頂点に対して、その頂点が含まれる連結成分内の黒色な頂点のcntを保持すれば答えられそう. 代表元だけを参照しながら管理すれば、十分高速.
type2のクエリでは今頂点vは黒色だったか否かの情報を基に代表元のcntをインクリメントしたりデクリメントするだけ.
type1のクエリではmerge(u,v)しつつ、新しい代表元に前の代表元から情報を移せばよい. `atcoder::dsu`ではmerge後の代表元はu,vどちらかの代表元に等しくなるから、新代表元と異なる方のleader(u)かleader(v)を見つけて、そっちから情報を吸い出せばよい.
# Complexity
Time: $O((N+Q)\, \alpha(N))$
Memory: $O(N)$
# Implementation Notes
`atcoder::dsu`においてmerge後の代表元にmerge前の選ばれなかった側の代表元からの情報を吸い出す操作、ちらほらやる場面があるけど微妙に実装面倒なんだよな…と思っていた. が、[公式解説](https://atcoder.jp/contests/abc420/editorial/13740)のコードで楽な方法が提示されていた. 天才的.
u,vがmergeする頂点(すでにu=leader(u)などでu,vは代表元にしているとする)、wがmerge後の新しい代表元として、==`u^v^w`==でよい.
uかvの片方はwと必ず一致しているので、`u^w`か`v^w`で打ち消しあって選ばれなかった側だけが残るということ.
# Pitfalls

# Similar / Links

# Afterthought
これが茶色Diffはさすがに嘘すぎるんだよな. かなり典型みは強いといえ、D含めて間違いなく緑Diffはあると思うが. 茶色コーダー時代にこんな問題解けて当たり前ですよね? と言われてたら無理すぎる.
順位表を見ても明らかにAIだろってのがそこかしこにすぐ見つかるが、彼らの影響は一体どれほどあるのかね…