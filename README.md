<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Raasi Unlock Magic ✨</title>

<style>
body{
  font-family:Poppins,sans-serif;
  background:#0f0f4a;
  color:white;
  display:flex;
  justify-content:center;
  align-items:center;
  flex-direction:column;
  min-height:100vh;
  padding:20px;
}
.card{
  background:rgba(255,255,255,0.1);
  backdrop-filter:blur(8px);
  padding:22px;
  width:350px;
  border-radius:18px;
  box-shadow:0 8px 30px rgba(0,0,0,0.5);
  text-align:center;
  margin-bottom:20px;
}
select,button{
  padding:12px 18px;
  border-radius:10px;
  border:none;
  margin:10px 0;
  cursor:pointer;
  font-weight:bold;
}
button:hover:not(:disabled){
  transform:scale(1.07);
  box-shadow:0 0 15px rgba(255,255,255,0.7);
}
#goInstagramBtn{
  background:#e1306c;
  color:white;
}
#unlockPredictionBtn{
  background:#ffdb4d;
  color:black;
}
#progressBar{
  width:0%;
  height:6px;
  background:#00ff9d;
  border-radius:6px;
  margin-top:6px;
}
#fullPrediction{
  display:none;
  margin-top:15px;
}
#socialModal{
  display:none;
  background:rgba(0,0,0,0.85);
  padding:20px;
  border-radius:12px;
  text-align:center;
  position:fixed;
  top:50%;
  left:50%;
  transform:translate(-50%,-50%);
  width:260px;
}
</style>
</head>

<body>

<div class="card">
<h2>🔮 Choose Your Raasi</h2>
<select id="raasiSelect">
  <option value="">-- Select Raasi --</option>
</select>
<p id="teaser">Pick your Raasi to see a hint!</p>
<button id="readMoreBtn">Read More</button>

<div id="unlockSection" style="display:none;">
  <button id="goInstagramBtn">Open Instagram</button>
  <div id="progressBar"></div>
  <button id="unlockPredictionBtn" disabled>Unlock Full Prediction</button>
</div>
</div>

<div id="fullPrediction" class="card">
<h2>✨ Your Result</h2>
<pre id="predictionContent"></pre>
</div>

<div id="socialModal">
<p>👍 Like / 💬 Comment / 🔁 Share on Instagram</p>
<button id="modalDoneBtn">Done</button>
</div>

<!-- Instagram follow button -->
<div style="margin-top:25px;text-align:center;">
  <a href="https://www.instagram.com/auronest_designs?igsh=bnNxOHdjaWppeGFj" 
     target="_blank"
     style="background:#e1306c;color:white;padding:12px 20px;border-radius:25px;
     text-decoration:none;font-weight:bold;font-size:15px;">
     📸 Follow @auronest_designs
  </a>
</div>

<script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>

<script>
const raasiData={
"Mesham":{short:"First in zodiac 🐏",full:"Mesham (Aries)\nFire sign 🔥\nBold and energetic",element:"fire"},
"Rishabham":{short:"Calm but stubborn 😤",full:"Rishabham (Taurus)\nEarth sign 🌍\nLoyal and practical",element:"earth"},
"Mithunam":{short:"Two minds 😵",full:"Mithunam (Gemini)\nAir sign\nTalkative and curious",element:"air"},
"Karkatakam":{short:"Emotional crab 🦀",full:"Cancer\nWater sign 🌊",element:"water"},
"Simham":{short:"Lion energy 🦁",full:"Leo\nConfident and bold",element:"fire"},
"Kanni":{short:"Perfectionist 🧹",full:"Virgo\nHard working",element:"earth"},
"Thulam":{short:"Balance ⚖️",full:"Libra\nFriendly and charming",element:"air"},
"Vrischikam":{short:"Intense 🦂",full:"Scorpio\nPassionate",element:"water"},
"Dhanusu":{short:"Adventurer 🏹",full:"Sagittarius\nFreedom lover",element:"fire"},
"Makaram":{short:"Hard worker 🐐",full:"Capricorn\nGoal driven",element:"earth"},
"Kumbham":{short:"Unique thinker 💡",full:"Aquarius\nCreative ideas",element:"air"},
"Meenam":{short:"Dreamy fish 🐟",full:"Pisces\nEmotional and artistic",element:"water"},
"Human":{short:"Special human 😏",full:"Avlothaaa.. emanthute irukiye kumaruuu 😂",element:"fire"}
};

const girlNames=[
"Priya","Anjali","Divya","Kavya","Sneha","Nivetha","Harini","Pooja","Swathi","Meena","Riya","Keerthana"
];

const colors={fire:"#ff4b1f",earth:"#2b8a3e",air:"#4b7bfc",water:"#9b2aff"};

const select=document.getElementById("raasiSelect");
for(let key in raasiData){
  let opt=document.createElement("option");
  opt.value=key;
  opt.textContent=key;
  select.appendChild(opt);
}

const teaser=document.getElementById("teaser");
select.onchange=()=>{
  const v=select.value;
  if(v){
    teaser.textContent=raasiData[v].short;
    teaser.style.color=colors[raasiData[v].element];
  }
};

document.getElementById("readMoreBtn").onclick=()=>{
  if(!select.value) return alert("Choose your Raasi first!");
  document.getElementById("unlockSection").style.display="block";
};

const instagramBtn=document.getElementById("goInstagramBtn");
const progressBar=document.getElementById("progressBar");

instagramBtn.onclick=()=>{
  window.open("https://www.instagram.com/auronest_designs?igsh=bnNxOHdjaWppeGFj","_blank");
  instagramBtn.disabled=true;
  const modal=document.getElementById("socialModal");
  modal.style.display="block";

  document.getElementById("modalDoneBtn").onclick=()=>{
    modal.style.display="none";
    let p=0;
    let timer=setInterval(()=>{
      p+=10;
      progressBar.style.width=p+"%";
      if(p>=100){
        clearInterval(timer);
        document.getElementById("unlockPredictionBtn").disabled=false;
        instagramBtn.textContent="Done 🎉";
      }
    },500);
  };
};

document.getElementById("unlockPredictionBtn").onclick=()=>{
  const sel=select.value;
  const randomGirl=girlNames[Math.floor(Math.random()*girlNames.length)];
  document.getElementById("fullPrediction").style.display="block";
  document.getElementById("predictionContent").textContent=
    raasiData[sel].full+
    "\n\n❤️ The girl secretly thinking about you:\n👉 "+randomGirl+" 😉";
  document.getElementById("predictionContent").style.color=colors[raasiData[sel].element];
  confetti({particleCount:150,spread:90,origin:{y:0.6}});
};
</script>

</body>
</html>
