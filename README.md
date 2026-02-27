# Select your Raasi
done
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Raasi Reel Viral 🌟</title>
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.7.1/jquery.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>
<style>
body{font-family:Arial,sans-serif;background:linear-gradient(135deg,#fefefe,#dbefff);text-align:center;padding:30px;overflow-x:hidden;}
h1,h2{color:#333;margin-bottom:20px;}
button, select{padding:10px 20px;margin:10px;font-size:16px;border-radius:10px;border:1px solid #ccc;cursor:pointer;transition:0.3s;}
button:hover{transform:scale(1.1);}
.card{max-width:500px;margin:20px auto;padding:25px;border-radius:15px;box-shadow:0 8px 20px rgba(0,0,0,0.2);text-align:left;position:relative;transition:0.3s;}
.fire{background:#ff6f61;color:#fff;}
.earth{background:#8fbc8f;color:#fff;}
.air{background:#87cefa;color:#333;}
.water{background:#1e90ff;color:#fff;}
.human{background:#ffb347;color:#333;}
#overlay{display:none;position:fixed;top:0;left:0;width:100%;height:100%;background:rgba(0,0,0,0.9);color:#fff;padding:20px;box-sizing:border-box;overflow-y:auto;z-index:1000;display:flex;align-items:center;justify-content:center;}
#overlay .content{background:#222;padding:25px;border-radius:15px;max-width:700px;text-align:center;position:relative;}
#closeOverlay{position:absolute;top:10px;right:10px;background:#ff4500;border:none;padding:5px 10px;border-radius:5px;cursor:pointer;color:#fff;}
#closeOverlay:hover{background:#e03e00;}
.sparkle{position:absolute;width:10px;height:10px;background:#fff;border-radius:50%;opacity:0.8;animation:sparkleAnim 1s linear infinite;}
@keyframes sparkleAnim{0%{transform:translate(0,0) scale(1);opacity:0.8;}50%{transform:translate(20px,-20px) scale(1.5);opacity:0;}100%{transform:translate(0,0) scale(1);opacity:0.8;}}
.bounce{animation:bounceAnim 0.8s infinite alternate;}
@keyframes bounceAnim{0%{transform:translateY(0);}100%{transform:translateY(-15px);}}
</style>
</head>
<body>
<audio id="bgMusic" src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" loop></audio>

<h1>✨ Discover Your Raasi Reel 🌟</h1>

<div id="readyDiv">
  <h2>🎉 Are you ready to discover your Raasi? 🎉</h2>
  <button id="readyBtn" class="bounce">Yes! I’m Ready 🚀</button>
</div>

<div id="raasiSection" style="display:none;">
  <select id="raasi">
    <option value="">--Select Your Raasi--</option>
    <option value="Mesham">Mesham</option>
    <option value="Rishabham">Rishabham</option>
    <option value="Mithunam">Mithunam</option>
    <option value="Karkatakam">Karkatakam</option>
    <option value="Simham">Simham</option>
    <option value="Kanni">Kanni</option>
    <option value="Thulam">Thulam</option>
    <option value="Vrischikam">Vrischikam</option>
    <option value="Dhanusu">Dhanusu</option>
    <option value="Makaram">Makaram</option>
    <option value="Kumbham">Kumbham</option>
    <option value="Meenam">Meenam</option>
    <option value="Human">Human</option>
  </select>

  <div id="shortContent" class="card" style="display:none;">
    <p id="twoLines"></p>
    <button id="readMore">Read More</button>
  </div>

  <div id="followPrompt" class="card" style="display:none;">
    <h3>🔒 Unlock Full Prediction</h3>
    <p>Complete below steps:</p>
    <ul>
      <li>✅ Follow <b>@auronest_designs</b></li>
      <li>❤️ Like our latest Reel</li>
      <li>💬 Comment your Raasi</li>
    </ul>
    <button id="engagementConfirm">I Did All Steps ✅</button>
  </div>
</div>

<div id="overlay">
  <div class="content">
    <button id="closeOverlay">Close ✖</button>
    <p id="fullText" style="font-size:1.2em; line-height:1.6em;"></p>
  </div>
</div>

<script>
const raasiData = {
"Mesham": { short:"First in zodiac – “I go first!” 🏃‍♂️", full:`Mesham (Aries / மேஷம்)... Motto: Life is short, run fast & roar loud! 🏆`, element:'fire' },
"Rishabham": { short:"Chill but stubborn 😤", full:`Rishabham (Taurus / ரிஷபம்)... Motto: Slow & steady 🐌`, element:'earth' },
"Mithunam": { short:"Twins – two minds 😵", full:`Mithunam (Gemini / மிதுனம்)... Motto: Life = try everything once! 🎉`, element:'air' },
"Karkatakam": { short:"Crab vibes 🦀", full:`Karkatakam (Cancer / கடகம்)... Motto: Home is where my heart & snacks are`, element:'water' },
"Simham": { short:"Lion – roar first 🦁", full:`Simham (Leo / சிம்மம்)... Motto: If life is a stage, I own it! 🎤`, element:'fire' },
"Kanni": { short:"Maiden – neat freak 🧹", full:`Kanni (Virgo / கன்னி)... Motto: Chaos? Not in my house! 🏠`, element:'earth' },
"Thulam": { short:"Scales – balancing ⚖️", full:`Thulam (Libra / துலாம்)... Motto: Life is too short for bad vibes! 🌈`, element:'air' },
"Vrischikam": { short:"Scorpion – intense 🦂", full:`Vrischikam (Scorpio / விருச்சிகம்)... Motto: Trust, but verify everything! 🔍`, element:'water' },
"Dhanusu": { short:"Archer – aims high 🏹", full:`Dhanusu (Sagittarius / தனுசு)... Motto: Life is adventure, let’s go! 🚀`, element:'fire' },
"Makaram": { short:"Goat – climbs everything 🐐", full:`Makaram (Capricorn / மகரம்)... Motto: Slow & steady wins everything 🐢`, element:'earth' },
"Kumbham": { short:"Water-bearer – ideas 🌊", full:`Kumbham (Aquarius / கும்பம்)... Motto: Be original or go home! 🏠`, element:'air' },
"Meenam": { short:"Fish – swims in dreams 🐟", full:`Meenam (Pisces / மீனம்)... Artistic & dreamy 🎨`, element:'water' },
"Human": { short:"Hmm… curious human 😏", full:`Avlothaaa.. emanthute irukiye kumaruuu 😎😂`, element:'human' }
};

const elementMap = {
"Mesham":"fire","Simham":"fire","Dhanusu":"fire",
"Rishabham":"earth","Kanni":"earth","Makaram":"earth",
"Mithunam":"air","Thulam":"air","Kumbham":"air",
"Karkatakam":"water","Vrischikam":"water","Meenam":"water",
"Human":"human"
};

function createSparkles(card){for(let i=0;i<15;i++){const s=$('<div class="sparkle"></div>');s.css({top:Math.random()*card.height(), left:Math.random()*card.width()});card.append(s);setTimeout(()=>s.remove(),1200);}}

// Auto reel flow
function startReelFlow(){
  $("#bgMusic")[0].play();
  $("#readyBtn").click();
  setTimeout(()=>{
    const raasis = Object.keys(raasiData);
    const randomRaasi = raasis[Math.floor(Math.random()*raasis.length)];
    $("#raasi").val(randomRaasi).change();
    setTimeout(()=>{ $("#readMore").click();
      setTimeout(()=>{ $("#engagementConfirm").click(); },1200);
    },1200);
  },1000);
}

$("#readyBtn").click(function(){
  $("#readyDiv").fadeOut(500);
  $("#raasiSection").fadeIn(500);
});

$("#raasi").change(function(){
  const raasi = $(this).val();
  const card = $("#shortContent");
  card.removeClass('fire earth air water human').addClass(elementMap[raasi]);
  $("#twoLines").text(raasiData[raasi].short);
  card.show();
  createSparkles(card);
  $("#followPrompt").hide();
  $("#overlay").hide();
});

$("#readMore").click(function(){ $("#followPrompt").fadeIn(500); });

$("#engagementConfirm").click(function(){
  const raasi = $("#raasi").val();
  $("#fullText").text(raasiData[raasi].full);
  $("#overlay").fadeIn(500);
  $("#followPrompt").hide();
  confetti({particleCount:200,spread:120,origin:{y:0.6}});
});

$("#closeOverlay").click(function(){ $("#overlay").fadeOut(500); });

$(document).ready(function(){ setTimeout(startReelFlow,1500); });
</script>
</body>
</html>
