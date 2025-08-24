<%*

/*

期待パス:

problems/{oj}/{contest_genre}/{contest_id}/{problem_id}.md

例: problems/atcoder/abc/420/C.md

*/

const rel = tp.file.path(true);          // 例: problems/atcoder/abc/420/C.md

const m = rel.match(/^problems\/([^\/]+)\/([^\/]+)\/([^\/]+)\/([^\/]+)\.md$/);

let oj='', genre='', cid='', pid='';

if(m){

  oj    = m[1];

  genre = m[2].toUpper;

  cid   = m[3];

  pid   = m[4];

} else {

  // 想定外 → 最低限タイトルから

  pid = tp.file.title;

}

const contest = genre + cid;

const url = (oj === 'atcoder' && contest && pid)

  ? `https://atcoder.jp/contests/${contest}/tasks/${contest}_${pid.toLowerCase()}`

  : '';

  

const today = tp.date.now("YYYY-MM-DD");

  

tR += `---\n`;

tR += `title: "${contest} ${pid} - "`; // ← 問題名を - の後ろに手入力

tR += `\noj: ${oj}`;

tR += `\ncontest: ${contest}`;

tR += `\ncontest_genre: ${genre}`;

tR += `\ncontest_id: ${cid}`;

tR += `\nproblem: ${pid}`;

tR += `\nurl: ${url}`;

tR += `\ndate: ${today}`;

tR += `\ntags: []`;

tR += `\nrating:`;

tR += `\nstatus: solved`;

tR += `\nrevisit:`;

tR += `\ntries:`;

tR += `\ntime_spent:`;

tR += `\n---\n\n`;

  

tR += `# TL;DR\n(核心一文)\n\n`;

tR += `# Statement (要約)\n\n`;

tR += `# Key Idea\n\n`;

tR += `# Approach\n\n`;

tR += `# Complexity\n\n`;

tR += `# Implementation Notes\n\n`;

tR += `# Pitfalls\n\n`;

tR += `# Similar / Links\n\n`;

tR += `# Afterthought\n`;

%>