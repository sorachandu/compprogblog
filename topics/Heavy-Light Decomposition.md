https://info.atcoder.jp/entry/algorithm_lectures/heavy_light_decomposition
これを読んで、書いた

#### 1点加算 + 総和クエリ
https://judge.yosupo.jp/submission/376399
```cpp
HeavyLightDecomposition HLD(G);
atcoder::fenwick_tree<long> fw(N);
for(int i=0;i<N;i++) fw.add(HLD.toSeq(i),A[i]);
while(Q--){
	int type;
	cin>>type;
	if(type==0){
		int p,x;
		cin>>p>>x;
		fw.add(HLD.toSeq(p),x);
	}else{
		int u,v;
		cin>>u>>v;
		long val{};
		while(!HLD.same(u,v)){
			if(HLD.toSeq(u)>HLD.toSeq(v)) swap(u,v);
			const int vr=HLD.heavyR(v);
			val+=fw.sum(HLD.toSeq(vr),HLD.toSeq(v)+1);
			v=HLD.parent(vr);
		}
		if(HLD.toSeq(u)>HLD.toSeq(v)) swap(u,v);
		val+=fw.sum(HLD.toSeq(u),HLD.toSeq(v)+1);
		cout<<val<<"\n";
	}
}
```

#### 1点変更 + 区間最大値クエリ
https://cses.fi/problemset/result/17398393/
```cpp
HeavyLightDecomposition HLD(G);
vector<int> ini(N);
for(int i=0;i<N;i++) ini[HLD.toSeq(i)]=V[i];
atcoder::segtree<int,
	[](int a,int b){ return max(a,b); },
	[]{ return -1<<30; }> seg(ini);
vector<int> ans;
while(Q--){
int type;
cin>>type;
if(type==1){
	int s,x;
	cin>>s>>x;
	seg.set(HLD.toSeq(s-1),x);
}else{
	int a,b;
	cin>>a>>b;
	a--,b--;
	int val=-1<<30;
	// LCAを求めるときと同様のノリで辿ればs-tパスが得られる
	while(!HLD.same(a,b)){
		if(HLD.toSeq(a)>HLD.toSeq(b)) swap(a,b);
		const int br=HLD.heavyR(b);
		val=max(val,seg.prod(HLD.toSeq(br),HLD.toSeq(b)+1));
		b=HLD.parent(br);
	}
	if(HLD.toSeq(a)>HLD.toSeq(b)) swap(a,b);
		val=max(val,seg.prod(HLD.toSeq(a),HLD.toSeq(b)+1));
		ans.emplace_back(val);
	}
}
for(int i=0;i<ssize(ans);i++) cout<<ans[i]<<" \n"[i+1==ssize(ans)];
```