<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>你的脸，正在偷偷垮掉吗？</title>
<style>
body{font-family:'微软雅黑',sans-serif;background:#fffbe8;color:#333;margin:0;padding:0;}
.container{max-width:600px;margin:0 auto;padding:20px;}
h1,h2{color:#ff4081;text-align:center;}
button{background:#ff4081;color:white;border:none;padding:10px 20px;margin-top:10px;border-radius:5px;cursor:pointer;}
.option{margin:10px 0;}
.result{background:#fff0f6;padding:20px;margin-top:20px;border-radius:10px;display:none;}
</style>
</head>
<body>
<div class="container">
<h1>你的脸，正在偷偷垮掉吗？</h1>
<h2>7道题，1分钟找到你的皮肤真相</h2>
<div id="quiz"></div>
<div id="result" class="result"></div>
</div>
<script>
const questions = [
  {q:'最近照镜子时，你最不想面对哪里？',options:['黑头毛孔越来越明显','脸干到开始卡粉','脸又黄没气色','黑眼圈重','感觉脸开始挂不住肉','动不动泛红敏感']},
  {q:'熬夜后的你，更像哪种状态？',options:['满脸油到能反光','干得像被吸走水分','一脸疲惫','眼睛肿得像刚哭完','法令纹越来越明显','脸又红又痒']},
  {q:'化妆/洗脸时，最容易让你崩溃的是？',options:['黑头怎么清都还有','上妆永远卡粉','化妆了还是没气色','遮瑕盖不住黑眼圈','拍照感觉脸变垮','护肤品总容易刺激']},
  {q:'朋友帮你拍照时，你最常吐槽的是？',options:['我鼻子怎么这么油','我脸怎么这么干','我今天气色也太差','黑眼圈好重','我脸是不是松了','我脸又红了']},
  {q:'你的皮肤最像哪种“受害者”？',options:['熬夜爆油受害者','空调房干尸','熬夜黄脸怪','手机党熊猫眼','地心引力受害者','敏感脆皮大学生']},
  {q:'如果只能先改善一个问题，你最想解决？',options:['毛孔黑头','干燥粗糙','暗沉没气色','黑眼圈眼袋','松弛下垂','泛红敏感']},
  {q:'你现在的皮肤状态更接近哪句话？',options:['控油已经控累了','补水像无底洞','脸像没睡醒','眼睛比人还累','以前拍照没这么垮','皮肤动不动就闹情绪']}
];
const scores = [1,2,3,4,5,6];
const resultTexts=[
  {range:[7,11],title:'毛孔堵塞型皮肤',text:'黑头反复出现，鼻头和下巴油光明显，皮肤像洗不干净。推荐【孔夫仔泡冲洗脸】深层清洁毛孔、软化黑头、调节水油平衡。'},
  {range:[12,17],title:'缺水屏障型皮肤',text:'容易卡粉、干燥紧绷，空调房久待脸会不舒服。推荐【好多水泡冲洗脸】深层补水、修护屏障、增强锁水能力。'},
  {range:[18,23],title:'熬夜工伤型皮肤',text:'脸色暗黄、没气色，熬夜后状态差。推荐【告白泡冲洗脸】提亮肤色、改善暗沉、提升通透感。'},
  {range:[24,29],title:'熊猫眼工伤型皮肤',text:'黑眼圈明显、眼周浮肿细纹增加。推荐【微笑PASTA泡冲洗脸】温感按摩、射频导入、消水肿护理。'},
  {range:[30,35],title:'地心引力受害者型皮肤',text:'法令纹明显、脸轮廓松，拍照显垮。推荐【普拉提泡冲洗脸】提拉紧致、激活胶原、改善轮廓松弛。'},
  {range:[36,42],title:'脆皮敏感型皮肤',text:'容易泛红、刺痛、换季状态不稳定。推荐【告白修护护理】舒缓泛红、修护屏障、提升稳定性。'}
];

let currentQ=0,totalScore=0;
const quizDiv=document.getElementById('quiz');
function showQuestion(){
  if(currentQ>=questions.length){showResult();return;}
  quizDiv.innerHTML='';
  const q=questions[currentQ];
  const h3=document.createElement('h3');h3.textContent=`Q${currentQ+1}. ${q.q}`;quizDiv.appendChild(h3);
  q.options.forEach((opt,i)=>{
    const btn=document.createElement('button');btn.textContent=opt;
    btn.className='option';
    btn.onclick=()=>{totalScore+=scores[i];currentQ++;showQuestion();};
    quizDiv.appendChild(btn);
  });
}
function showResult(){
  quizDiv.style.display='none';
  const resDiv=document.getElementById('result');
  for(let r of resultTexts){if(totalScore>=r.range[0]&&totalScore<=r.range[1]){resDiv.innerHTML=`<h2>📋 ${r.title}</h2><p>${r.text}</p>`;resDiv.style.display='block';break;}}
}
showQuestion();
</script>
</body>
</html>
