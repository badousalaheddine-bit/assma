<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>مفاجأة لأسماء ♡</title>
<link href="https://fonts.googleapis.com/css2?family=Pixelify+Sans:wght@500;700&family=Poppins:wght@400;600&family=Cairo:wght@600;700&display=swap" rel="stylesheet">
<style>
:root{
  color-scheme: light;
  --bg1:#ffe3ec; --bg2:#fff6f9; --pink:#f4a7bb; --pink-d:#e07a95; --pink-l:#fbd5e0;
  --ink:#9b3a5a; --card:#f9cfdb; --ease:cubic-bezier(.2,.8,.2,1);
  box-sizing:border-box;
  padding-top:env(safe-area-inset-top,0px); padding-bottom:env(safe-area-inset-bottom,0px);
}
*{box-sizing:border-box}
html,body{height:100%;margin:0}
body{background:linear-gradient(135deg,var(--bg1),var(--bg2));font-family:'Cairo','Poppins',sans-serif;color:var(--ink);overflow:hidden;position:relative}
.stage{position:absolute;inset:0;display:flex;align-items:center;justify-content:center;flex-direction:column;overflow-y:auto;padding:16px;transition:opacity .5s ease,transform .5s ease}
.stage .win{margin:auto;flex-shrink:0}
.hide{opacity:0;pointer-events:none;transform:scale(.9)}
.fx{position:fixed;inset:0;pointer-events:none;overflow:hidden;z-index:5}
.fx span{position:absolute;bottom:-30px;color:var(--pink);opacity:.5;animation:rise linear forwards}
@keyframes rise{to{transform:translateY(-110vh) rotate(25deg);opacity:0}}

/* envelope */
.env{position:relative;width:min(240px,64vw);aspect-ratio:3/2;cursor:pointer;animation:bob 3s ease-in-out infinite}
@keyframes bob{50%{transform:translateY(-8px)}}
.env .body{position:absolute;inset:0;background:#fff4f6;border:3px solid var(--pink);border-radius:8px;overflow:hidden}
.env .body::before,.env .body::after{content:"";position:absolute;bottom:0;width:50%;height:100%;background:#ffe3ea}
.env .body::before{left:0;clip-path:polygon(0 0,100% 100%,0 100%)}
.env .body::after{right:0;clip-path:polygon(100% 0,100% 100%,0 100%)}
.flap{position:absolute;left:0;top:0;width:100%;height:58%;background:var(--pink-l);border:3px solid var(--pink);border-radius:8px 8px 0 0;clip-path:polygon(0 0,100% 0,50% 100%);transform-origin:top;transition:transform .7s var(--ease);z-index:2}
.seal{position:absolute;left:50%;top:50%;transform:translate(-50%,-50%);font-size:34px;color:var(--pink-d);z-index:3;transition:opacity .3s}
.env.open .flap{transform:rotateX(180deg)}
.env.open .seal{opacity:0}
.env.open{animation:none;transform:scale(1.1);transition:transform .6s}
.cap{margin-top:26px;font-family:'Cairo','Pixelify Sans',sans-serif;font-size:20px;letter-spacing:1px}
.hint{margin-top:10px;font-size:12px;opacity:.6;animation:pulse 1.8s ease-in-out infinite}
@keyframes pulse{50%{opacity:.25}}

/* window */
.win{position:relative;width:min(300px,84vw);background:#fff;border:3px solid var(--pink-d);border-radius:6px;box-shadow:6px 6px 0 rgba(224,122,149,.35);font-family:'Cairo','Pixelify Sans',sans-serif}
.bar{display:flex;justify-content:space-between;align-items:center;background:var(--pink-d);color:#fff;font-size:12px;padding:4px 8px;letter-spacing:1px}
.bar i{display:inline-block;width:9px;height:9px;border:2px solid #fff;margin-left:4px}
.deco{background:var(--pink-l);color:var(--pink-d);text-align:center;font-size:12px;padding:2px;border-bottom:3px solid var(--pink-d);letter-spacing:6px}
.content{position:relative;min-height:340px;padding:16px 14px 70px;text-align:center;
  background-color:var(--card);
  background-image:linear-gradient(45deg,rgba(255,255,255,.35) 25%,transparent 25%,transparent 75%,rgba(255,255,255,.35) 75%),linear-gradient(45deg,rgba(255,255,255,.35) 25%,transparent 25%,transparent 75%,rgba(255,255,255,.35) 75%);
  background-size:16px 16px;background-position:0 0,8px 8px}
.letter{font-size:14px;line-height:1.9;font-weight:600;color:var(--ink);margin-bottom:12px}
.msg{font-size:19px;line-height:1.4;font-weight:700;color:var(--ink);text-shadow:1px 1px 0 #fff}
.cat{display:block;width:100px;margin:12px auto 0;image-rendering:pixelated}
.btn{font-family:inherit;font-size:15px;font-weight:700;color:var(--pink-d);background:#fff;border:2px solid var(--pink-d);padding:6px 16px;cursor:pointer;box-shadow:2px 2px 0 var(--pink-d)}
.btn:active{transform:translate(2px,2px);box-shadow:none}
#yes{position:absolute;left:50%;bottom:14px;transform-origin:center;translate:-50% 0;transition:scale .3s}
#no{position:absolute;right:12px;bottom:18px;font-size:12px;padding:3px 10px;transition:left .25s var(--ease),top .25s var(--ease),right .25s}
.cat .h{transform-box:fill-box;transform-origin:center}
.won .cat .h{animation:beat 1s ease-in-out infinite}
@keyframes beat{50%{transform:scale(1.3)}}
.won #yes,.won #no{display:none}
.won .cat{animation:hop .8s ease-in-out infinite}
@keyframes hop{50%{transform:translateY(-10px)}}
@media (prefers-reduced-motion:reduce){*{animation:none!important}}
</style>
</head>
<body>
<div class="fx" id="fx"></div>

<div class="stage" id="s1">
  <div class="env" id="env" role="button" aria-label="افتحي الرسالة">
    <div class="body"></div><div class="flap"></div><div class="seal">♥</div>
  </div>
  <div class="cap">♥ مفاجأة صغيرة لكِ يا أسماء ♥</div>
  <div class="hint">اضغطي لفتح الرسالة</div>
</div>

<div class="stage hide" id="s2">
  <div class="win" id="win">
    <div class="bar"><span>حُب</span><span><i></i><i></i><i></i></span></div>
    <div class="deco">♥ ♥ ♥</div>
    <div class="content" id="content">
      <div class="letter" id="letter">منذ أن عرفتكِ، أدركت أن بعض اللقاءات لا تأتي عبثاً، وأن بعض الأسماء لا تمرّ على القلب مروراً عابراً. جئتِ كصدفة جميلة، فصرتِ حكاية تستحق أن تُروى، ووجهاً يترك في الأيام أثراً جميلاً. لا أعلم ماذا تخبئ لنا الأيام، لكنني أعلم أن تعرّفي عليكِ كان من أجمل تفاصيلها، فشكراً لأنكِ أصبحتِ اسماً له في خاطري مكانة لا تشبه سواها.</div><div class="msg" id="msg">هل أنتِ مبسوطة لأنني موجود في حياتك؟</div>
      <svg class="cat" id="cat" viewBox="0 0 16 15" shape-rendering="crispEdges"></svg>
      
      <button class="btn" id="yes">نعم مبسوطة</button>
    </div>
  </div>
</div>

<script>
// ✏️ Edit the texts here
var TEXT_ASK = "هل أنتِ مبسوطة لأنني موجود في حياتك؟";
var TEXT_WIN = "ياااي! سعادتكِ تسعدني ♡";

var $ = function(id){return document.getElementById(id)};
var fx = $('fx');

// floating hearts
function heart(x, size, dur, op){
  var s = document.createElement('span');
  s.textContent = '♥';
  s.style.left = x + 'vw';
  s.style.fontSize = size + 'px';
  s.style.animationDuration = dur + 's';
  if(op) s.style.opacity = op;
  fx.appendChild(s);
  setTimeout(function(){s.remove()}, dur*1000);
}
setInterval(function(){ heart(Math.random()*100, 8+Math.random()*10, 8+Math.random()*6, .3) }, 700);

// pixel cat
var map = [
"..kk........kk..",
".kkkk......kkkk.",
".kkkkkkkkkkkkkk.",
".kkkkkkkkkkkkkk.",
".kkkwwkkkkwwkkk.",
".kkkwwkkkkwwkkk.",
".kkkkkknnkkkkkk.",
".kkkkkkkkkkkkkk.",
"..kkkkkkkkkkkk..",
"...kkhhkkhhkkk..",
"..kkhhhhhhhhkk..",
"..kkhhhhhhhhkk..",
"...kkhhhhhhkk...",
"....kkhhhhkk....",
".....kkhhkk....."
];
var col = {k:'#2b2230', w:'#fff', n:'#f4a7bb', h:'#f06b8e'};
var svg = '';
map.forEach(function(row, y){
  for(var x=0; x<row.length; x++){
    var c = row[x]; if(c === '.') continue;
    svg += '<rect x="'+x+'" y="'+y+'" width="1.02" height="1.02" fill="'+col[c]+'"'+(c==='h'?' class="h"':'')+'/>';
  }
});
$('cat').innerHTML = svg;

// open envelope
var opened = false;
$('env').addEventListener('click', function(){
  if(opened) return; opened = true;
  $('env').classList.add('open');
  setTimeout(function(){
    $('s1').classList.add('hide');
    $('s2').classList.remove('hide');
  }, 1000);
});

// NO button dodges
var no = null, content = $('content');
function dodge(e){
  if(e) e.preventDefault();
  var w = content.clientWidth - no.offsetWidth - 10;
  var h = content.clientHeight - no.offsetHeight - 70;
  no.style.right = 'auto'; no.style.bottom = 'auto';
  no.style.left = Math.max(5, Math.random()*w) + 'px';
  no.style.top = Math.max(60, Math.random()*h) + 'px';
  var yes = $('yes');
  var sc = parseFloat(yes.dataset.sc || 1) + .12;
  yes.dataset.sc = sc; yes.style.scale = Math.min(sc, 1.4);
}


// YES
$('yes').addEventListener('click', function(){
  content.classList.add('won');
  $('msg').textContent = TEXT_WIN;
  $('msg').style.color = '#d65a80';
  for(var i=0;i<40;i++){
    (function(i){ setTimeout(function(){ heart(Math.random()*100, 14+Math.random()*24, 3+Math.random()*3, .85) }, i*60) })(i);
  }
  setInterval(function(){ heart(Math.random()*100, 12+Math.random()*20, 4+Math.random()*3, .7) }, 350);
});
</script>
</body>
</html>

