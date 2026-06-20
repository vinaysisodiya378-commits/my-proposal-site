<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Proposal Game 💖</title>

<style>
body{
    margin:0;
    height:100vh;
    display:flex;
    justify-content:center;
    align-items:center;
    background:linear-gradient(135deg,#ff9ecf,#ffc7de);
    font-family:Arial;
    overflow:hidden;
}

.screen{
    display:none;
    text-align:center;
    background:white;
    padding:25px;
    border-radius:20px;
    width:85%;
    max-width:400px;
    box-shadow:0 0 20px rgba(255,0,100,0.3);
}

.active{display:block;}

button{
    padding:12px 20px;
    margin:10px;
    border:none;
    border-radius:25px;
    font-size:18px;
    cursor:pointer;
}

#yes{
    background:#ff4d8d;
    color:white;
}

#no{
    background:#ddd;
    position:fixed;
}

h1,h2{color:#ff2f75;}

p{color:#555;}

/* 🦋 butterfly */
.butterfly{
    position:fixed;
    font-size:20px;
    animation:flyUp 4s linear forwards;
    pointer-events:none;
}

@keyframes flyUp{
    0%{transform:translateY(0);opacity:1;}
    100%{transform:translateY(-120vh) translateX(50px);opacity:0;}
}
</style>
</head>

<body>

<!-- SCREEN 1 -->
<div class="screen active" id="s1">
    <h1>💖 Hey You 💖</h1>
    <p>Ek chhoti si journey 💕</p>
    <button onclick="next(2)">Start 🚀</button>
</div>

<!-- SCREEN 2 -->
<div class="screen" id="s2">
    <h2>💫 Special Moment</h2>
    <p>Tum special ho ❤️</p>
    <button onclick="next(3)">Next 💕</button>
</div>

<!-- SCREEN 3 -->
<div class="screen" id="s3">
    <h2>💖 Final Question 💖</h2>

    <p>Ab sach bolna 😊</p>
    <h3>Will you be mine? 💍</h3>

    <button id="yes" onclick="yesClick()">Yes ❤️</button>
    <button id="no" onclick="moveNo()">No 😅</button>
</div>

<!-- SCREEN 4 -->
<div class="screen" id="s4">
    <h1>🎉 Thank you 🎉</h1>
    <p>You made my day 💖</p>
</div>

<script>

function next(n){
    document.querySelectorAll(".screen").forEach(s=>s.classList.remove("active"));
    document.getElementById("s"+n).classList.add("active");
}

// No button escape
function moveNo(){
    let btn=document.getElementById("no");

    let maxX=window.innerWidth-120;
    let maxY=window.innerHeight-80;

    btn.style.position="fixed";
    btn.style.left=Math.random()*maxX+"px";
    btn.style.top=Math.random()*maxY+"px";
}

// Yes click
function yesClick(){
    next(4);

    for(let i=0;i<25;i++){
        setTimeout(createButterfly, i*200);
    }
}

// 🦋 butterflies
function createButterfly(){
    let b=document.createElement("div");
    b.className="butterfly";
    b.innerHTML="🦋";

    b.style.left=Math.random()*100+"vw";
    b.style.bottom="-20px";
    b.style.fontSize=(18+Math.random()*25)+"px";

    document.body.appendChild(b);

    setTimeout(()=>b.remove(),4000);
}

/* BACK LOCK */
history.replaceState(null,null,location.href);

window.onpopstate=function(){
    history.pushState(null,null,location.href);
    next(3);
};

</script>

</body>
</html>
