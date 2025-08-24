<%*
/*
Path pattern:
problems/{contest}-{problem}.md
例:
  problems/ABC420-C.md
  problems/PAST004-M.md
*/
const rel = tp.file.path(true);
const m = rel.match(/^problems\/([^\/]+)\.md$/);
let contest='', problem='', oj='';
if(m){
  const fname = m[1];
  const dash = fname.lastIndexOf('-');
  if(dash !== -1){
    contest = fname.slice(0,dash);
    problem = fname.slice(dash+1);
  } else {
    contest = fname;
    problem = '';
  }
}
// OJ 推定 (必要なら後で手で修正)
if(/^(ABC|ARC|AGC|AHC|PAST)\d+$/i.test(contest)) oj = 'atcoder';

const contestSlug = contest.toLowerCase();
const problemSlug = problem.toLowerCase();
let url='';
if(oj === 'atcoder' && contest && problem){
  url = `https://atcoder.jp/contests/${contestSlug}/tasks/${contestSlug}_${problemSlug}`;
}

const today = tp.date.now("YYYY-MM-DD");
tR += `---\n`;
tR += `title: "${contest} ${problem} - "`;
tR += `\noj: ${oj}`;
tR += `\ncontest: ${contest}`;
tR += `\nproblem: ${problem}`;
tR += `\nurl: ${url}`;
tR += `\nsubmission_url:`;
tR += `\ndate: ${today}`;
tR += `\ntags: []`;
tR += `\ndifficulty:`;
tR += `\nstatus: solved`;
tR += `\nrevisit:`;
tR += `\ntries:`;
tR += `\ntime_spent:`;
tR += `\n---\n\n`;

tR += `# Statement\n\n`;
tR += `# Key Idea\n\n`;
tR += `# Approach\n\n`;
tR += `# Complexity\nTime: $O()$\nMemory: $O()$\n\n`;
tR += `# Implementation Notes\n\n`;
tR += `# Pitfalls\n\n`;
tR += `# Similar / Links\n\n`;
tR += `# Afterthought\n`;

%>