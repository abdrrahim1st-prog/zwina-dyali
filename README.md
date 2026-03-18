<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>DOUAU ❤️</title>

<!-- Google Font -->
<link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@400;700&display=swap" rel="stylesheet">

<style>
*{margin:0;padding:0;box-sizing:border-box;font-family:'Dancing Script', cursive;}

body{
  height:100vh;
  overflow:hidden;
  background:black;
  display:flex;
  justify-content:center;
  align-items:center;
}

/* PHONE FRAME */
.phone{
  width:320px;
  height:640px;
  border-radius:40px;
  overflow:hidden;
  position:relative;
  background:rgba(255,255,255,0.05);
  backdrop-filter:blur(20px);
  box-shadow:0 0 40px rgba(255,0,100,0.6);
}

/* STARS */
.star{
  position:absolute;
  width:2px;height:2px;
  background:white;
  animation:twinkle 2s infinite alternate;
}
@keyframes twinkle{
  from{opacity:0.2;}
  to{opacity:1;}
}

/* PAGES */
.page{
  position:absolute;
  width:100%;
  height:100%;
  display:flex;
  justify-content:center;
  align-items:center;
  flex-direction:column;
  transition:1s;
}

/* NAME */
.name{
  font-size:50px;
  font-weight:700;
  color:white;
  text-align:center;
  animation:rainbowGlow 3s infinite, pulse 1.5s infinite alternate;
}

@keyframes rainbowGlow{
  0%{text-shadow:0 0 5px red;}
  14%{text-shadow:0 0 5px orange;}
  28%{text-shadow:0 0 5px yellow;}
  42%{text-shadow:0 0 5px green;}
  57%{text-shadow:0 0 5px blue;}
  71%{text-shadow:0 0 5px indigo;}
  85%{text-shadow:0 0 5px violet;}
  100%{text-shadow:0 0 5px red;}
}
@keyframes pulse{
  0%{transform:scale(1);}
  50%{transform:scale(1.1);}
  100%{transform:scale(1);}
}

/* BUTTONS */
button{
  margin-top:20px;
  padding:10px 25px;
  border:none;
  border-radius:30px;
  background:white;
  color:#ff4b7d;
  font-size:18px;
  cursor:pointer;
  transition:0.3s;
  position:relative;
  font-family:'Dancing Script', cursive;
  font-weight:700;
}
button:hover{ transform:scale(1.1); }
button:active{
  transform: scale(0.9) rotate(-5deg);
  box-shadow:0 0 20px #ff4b7d;
}

/* HIDDEN PAGE */
.hidden{opacity:0;pointer-events:none;}

/* TEXT */
.text{
  color:white;
  text-align:center;
  padding:20px;
  font-size:20px;
  line-height:1.6;
}

/* HEARTS */
.heart{
  position:absolute;
  width:15px;height:15px;
  background:red;
  transform:rotate(45deg);
  animation:float 5s linear infinite;
}
.heart::before,.heart::after{
  content:'';position:absolute;width:15px;height:15px;background:red;border-radius:50%;
}
.heart::before{top:-7px;}
.heart::after{left:-7px;}

@keyframes float{
  0%{transform:translateY(100%) rotate(45deg);opacity:1;}
  100%{transform:translateY(-10%) rotate(45deg);opacity:0;}
}

/* CONFETTI */
.confetti{
  position:absolute;
  width:8px;height:8px;
  background:yellow;
  animation:fall 3s linear infinite;
}
@keyframes fall{
  0%{transform:translateY(-10px);}
  100%{transform:translateY(700px);}
}
</style>
</head>

<body>

<div class="phone" id="phone">

<!-- PAGE 1 -->
<div class="page" id="p1">
  <div class="name">DOUAA ❤️</div>
  <button onclick="next1()">Start 💌</button>
</div>

<!-- PAGE 2 -->
<div class="page hidden" id="p2">
  <div class="text" id="typing"></div>
  <button onclick="next2()">Next ➡️</button>
</div>

<!-- PAGE 3 -->
<div class="page hidden" id="p3">
  <div class="name">I Love You ❤️</div>
  <button onclick="secret()">Secret 💎</button>
</div>

<!-- SECRET PAGE -->
<div class="page hidden" id="p4">
  <div class="name">Forever ♾️</div>
  <div class="text">nta ahsan haja f 7yati 💖</div>
</div>

</div>

<script>
// STARS
for(let i=0;i<80;i++){
  let s=document.createElement("div");
  s.classList.add("star");
  s.style.left=Math.random()*100+"%";
  s.style.top=Math.random()*100+"%";
  document.body.appendChild(s);
}

// TRANSITIONS
function next1(){
  let btn = document.querySelector("#p1 button");
  btn.style.transform = "scale(1.5)";
  btn.style.opacity = "0";
  setTimeout(()=>{
    hide("p1");
    show("p2");
    typing();
    hearts();
    btn.style.transform = "";
    btn.style.opacity = "";
  }, 300);
}
function next2(){
  hide("p2"); show("p3");
}
function secret(){
  hide("p3"); show("p4");
  confetti();
}

function hide(id){document.getElementById(id).classList.add("hidden");}
function show(id){document.getElementById(id).classList.remove("hidden");}

// TYPING
let msg=`Douaa, mn nhar li 3REFTK w ana 3reft blli sa3ada hiya nty ❤️  
kol nhar kanchouf fik haja katzid tkhllini kanbghik aktar 😍  

nty machi ghi wa7da f 7yati... nty 7yati kamla 💖  
nty da7kati, ra7ti, w ahla haja w9a3at lia 🥺  

ila 3tawni n5tar mra okhra, ghan5tarek nti mara wra mara ❤️  
7it bghit nb9a m3ak dima, f kol wa9t w f ay makan ♾️  

kanbghik a l'infini...  
w ghanb9a kanbghik 7ta l akhir nhar f7yati azin  💕`;  

kanbghik bzaaaaf w ma3rft kifach n3abr 3la hadchi kaml 🥺  
o inchaa allah nb9aw m3a ba3dyatna dima ❤️`;
let i=0;
function typing(){
  let el=document.getElementById("typing");
  el.innerHTML="";
  i=0;
  function t(){
    if(i<msg.length){
      el.innerHTML+=msg.charAt(i);
      i++;
      setTimeout(t,40);
    }
  }
  t();
}

// HEARTS
function hearts(){
  setInterval(()=>{
    let h=document.createElement("div");
    h.classList.add("heart");
    h.style.left=Math.random()*100+"%";
    document.getElementById("phone").appendChild(h);
    setTimeout(()=>h.remove(),5000);
  },300);
}

// CONFETTI
function confetti(){
  setInterval(()=>{
    let c=document.createElement("div");
    c.classList.add("confetti");
    c.style.left=Math.random()*100+"%";
    document.getElementById("phone").appendChild(c);
    setTimeout(()=>c.remove(),3000);
  },200);
}

</script>

</body>
</html>
