以下は、競プロで実用的な std::views（C++20/23）の主なアダプタと活用例です。パイプ演算子でつなぐと読みやすくなります。

基本
- 遅延評価で軽量に連結可能。コピーを作らないため高速。
- 元データの寿命に注意（ビューは参照）。必要なら vector などに materialize する。
- 多くのオンラインジャッジは C++20。C++23 追加のものは環境依存です。

C++20でほぼ使えるもの
- 生成
  - views::iota(a, b): 半開区間 [a, b)。整数ループの置き換え
  - views::single(x): 要素1つのレンジ
  - views::empty<T>: 空レンジ
  - views::counted(ptr, n): ポインタと長さからレンジ
  - views::istream<T>(cin): ストリームから要素列を読む
- 要素操作
  - views::transform(f): 写像
  - views::filter(pred): フィルタ
- スライス
  - views::take(n), drop(n)
  - views::take_while(pred), drop_while(pred)
- 並べ替え
  - views::reverse
- 平坦化・分割
  - views::join: 2次元を平坦化
  - views::split(delim or predicate): デリミタで分割（得られるのはサブレンジ）
- 補助
  - views::all: レンジ化（コンテナ/配列/ビューを統一）
  - views::common: イテレータ型を揃える
  - views::as_const, views::as_rvalue
  - views::elements<N>: pair/tuple から N 番目要素を取り出す

C++23 で増えた便利アダプタ（使えるかは環境次第）
- views::zip, views::zip_transform: 複数レンジを同期走査
- views::keys, views::values: pair 系から第一/第二要素
- views::chunk(n): 長さ n ごとの塊
- views::chunk_by(eq): 隣接要素が eq を満たす区間に分割（ランレングスなど）
- views::slide(n): 長さ n の連続部分列（滑らせる窓）
- views::adjacent<N>, views::pairwise: 隣接 N タプル/隣接2要素
- views::join_with(delim): 平坦化しつつ間に区切り要素
- std::ranges::to<Container>: ビューをコンテナに変換

競プロ向けレシピ集

- 0..n-1 のループ（添字）:
````cpp
for (int i : std::views::iota(0, n)) { /* use i */ }
````

- 条件付き変換＋合計:
````cpp
long long ans =
  std::accumulate(v.begin(), v.end(), 0LL, [](long long s, int x){
    if (x % 2 == 0) s += x * x;
    return s;
  });
// ranges 流で:
long long ans2 =
  std::accumulate((v | std::views::filter([](int x){return x%2==0;})
                     | std::views::transform([](int x){return 1LL*x*x;})).begin(),
                  (v | std::views::filter([](int x){return x%2==0;})
                     | std::views::transform([](int x){return 1LL*x*x;})).end(),
                  0LL);
````

- 先頭 k 個/末尾を捨てる:
````cpp
for (int x : v | std::views::take(k)) { /* ... */ }
for (int x : v | std::views::drop(k)) { /* ... */ }
````

- 隣接差分（C++20で添字、C++23なら pairwise/zip）:
````cpp
// C++20: 添字
for (int i : std::views::iota(0, n-1)) {
  int d = v[i+1] - v[i];
}
// C++23: pairwise
for (auto [a, b] : v | std::views::pairwise) {
  int d = b - a;
}
````

- 2D を平坦化（grid の全要素を一気に走査）:
````cpp
for (int x : grid | std::views::join) { /* ... */ } // grid: vector<vector<int>>
````

- 文字列分割（スペース/カンマ等）:
````cpp
std::string s; std::getline(cin, s);
for (auto token_rng : s | std::views::split(' ')) {
  std::string token(token_rng.begin(), token_rng.end()); // materialize
}
````

- map のキー/値だけ走査（C++23）:
````cpp
for (auto k : mp | std::views::keys) { /* ... */ }
for (auto v : mp | std::views::values) { /* ... */ }
````

- ランレングス圧縮（要ソート、C++23: chunk_by）:
````cpp
// C++23
std::ranges::sort(a);
for (auto group : a | std::views::chunk_by(std::ranges::equal_to{})) {
  int val = *group.begin();
  int cnt = std::ranges::distance(group);
}
// C++20 代替: 手書きで区切る
````

- スライディングウィンドウ（C++23: slide、C++20: 手書き）:
````cpp
// C++23
for (auto win : v | std::views::slide(k)) {
  long long sum = std::accumulate(win.begin(), win.end(), 0LL);
}
// C++20 代替
long long sum = std::accumulate(v.begin(), v.begin()+k, 0LL);
for (int i=0; i+k<n; ++i) {
  // use sum on [i, i+k)
  if (i+k<n) sum += v[i+k] - v[i];
}
````

- 2 本の配列を同時に走査（C++23: zip）:
````cpp
// C++23
for (auto [x, y] : std::views::zip(a, b)) { /* ... */ }
````

- 入力を EOF まで読む（速い一括読み不要のとき）:
````cpp
long long s = 0;
for (int x : std::views::istream<int>(cin)) s += x;
````

注意点
- ビューは基本的に非所有。元コンテナ/文字列の寿命に注意。split の各トークンは元文字列のビューなので、使い回すなら文字列にコピーする。
- 一部アダプタはランダムアクセスでないと計算量が悪化することがある（reverse, take/drop の複合など）。大半は O(1) 追加コスト。
- C++23 の可用性はコンパイラ/ジャッジ依存。使うならローカルで -std=gnu++23 を確認し、ジャッジ仕様をチェック。