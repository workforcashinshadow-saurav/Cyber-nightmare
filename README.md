# Cyber-nightmare
A website 

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>CYBER NIGHTMARE | Security Simulation</title>

<style>
*{margin:0;padding:0;box-sizing:border-box}

body{
  min-height:100vh;
  background:#030405;
  color:white;
  font-family:monospace;
  display:flex;
  justify-content:center;
  align-items:center;
  padding:15px;
  overflow-x:hidden;
}

body.flash{animation:flash .35s 2}

@keyframes flash{
  0%,100%{background:#030405}
  50%{background:#500000}
}

.container{
  width:100%;
  max-width:430px;
  padding:28px 22px;
  background:#0b0e11;
  border:1px solid #343434;
  border-radius:12px;
  text-align:center;
  box-shadow:0 0 45px #ff000020;
}

.logo{
  color:#ff3333;
  font-size:42px;
  font-weight:bold;
  margin-bottom:12px;
}

h1{font-size:22px;letter-spacing:3px}

.subtitle{
  color:#777;
  margin:12px 0 28px;
  font-size:11px;
}

input{
  width:100%;
  padding:16px;
  background:#050607;
  border:1px solid #393939;
  color:white;
  border-radius:7px;
  margin-bottom:15px;
  outline:none;
}

button{
  width:100%;
  padding:15px;
  background:#c32222;
  border:0;
  color:white;
  font-weight:bold;
  border-radius:6px;
  cursor:pointer;
}

button:disabled{opacity:.5}

.hidden{display:none!important}

.spinner{
  height:36px;
  width:36px;
  border:3px solid #333;
  border-top-color:red;
  border-radius:50%;
  animation:spin .7s linear infinite;
  margin:20px auto;
}

@keyframes spin{to{transform:rotate(360deg)}}

#terminal{
  text-align:left;
  color:#40ff83;
  background:#020604;
  border:1px solid #164b2a;
  padding:15px;
  min-height:130px;
  margin-top:20px;
  font-size:11px;
  line-height:1.9;
  overflow-wrap:anywhere;
}

.red{color:#ff3434}
.green{color:#50ff8a}

.popup{
  position:fixed;
  z-index:10;
  top:50%;
  left:50%;
  transform:translate(-50%,-50%);
  width:min(90%,350px);
  background:#151515;
  border:2px solid #ff3030;
  padding:25px 20px;
  text-align:center;
  box-shadow:0 0 40px #ff000080;
  animation:popupIn .3s ease;
}

@keyframes popupIn{
  from{opacity:0;transform:translate(-50%,-45%) scale(.8)}
  to{opacity:1;transform:translate(-50%,-50%) scale(1)}
}

.popup h2{
  color:#ff3434;
  margin-bottom:15px;
  font-size:21px;
}

.popup p{
  color:#ddd;
  font-size:13px;
  line-height:1.7;
  margin-bottom:20px;
}

.overlay{
  position:fixed;
  inset:0;
  background:#000d;
  z-index:9;
}

.warning{
  background:#260909;
  border:1px solid #a62a2a;
  padding:20px 12px;
  border-radius:8px;
  margin-top:20px;
}

.warning h2{
  color:#ff3838;
  font-size:23px;
  margin-bottom:13px;
}

.warning p{
  color:#ffc0c0;
  font-size:13px;
  line-height:1.7;
}

.countdown{
  color:#ff3939;
  font-size:40px;
  font-weight:bold;
  margin:20px;
}

.footer{
  margin-top:25px;
  color:#555;
  font-size:9px;
  letter-spacing:1px;
}

#finalScreen h2{
  color:#4dff98;
  margin:20px;
}

#finalScreen p{
  color:#bbb;
  line-height:1.8;
  font-size:13px;
  margin-bottom:20px;
}

.scanline{
  position:fixed;
  inset:0;
  pointer-events:none;
  z-index:2;
  background:repeating-linear-gradient(
    transparent 0px,
    transparent 3px,
    #ffffff08 4px
  );
}

</style>
</head>

<body>

<div class="scanline"></div>

<div class="container">

  <div class="logo">CN://</div>
  <h1>CYBER NIGHTMARE</h1>
  <p class="subtitle">SECURITY SIMULATION TERMINAL</p>

  <div id="loginScreen">
    <input id="demoId"
      type="text"
      placeholder="Enter a demo username"
      autocomplete="off">

    <button onclick="startSimulation()">
      INITIATE SIMULATION
    </button>

    <p class="footer">DEMO ONLY • NO REAL LOGIN</p>
  </div>

  <div id="loading" class="hidden">
    <div class="spinner"></div>
    <p style="color:#aaa">Initializing simulation...</p>
    <div id="terminal"></div>
  </div>

  <div id="countdownScreen" class="hidden">
    <div class="warning">
      <h2>⚠ SYSTEM WARNING</h2>
      <p>Security awareness simulation in progress.</p>
    </div>
    <div class="countdown" id="countdown">03</div>
    <p style="color:#aaa;font-size:11px">
      DEMONSTRATION COUNTDOWN
    </p>
  </div>

  <div id="finalScreen" class="hidden">
    <div style="font-size:55px">🛡️</div>
    <h2>YOU ARE SAFE.</h2>
    <p>
      This was a cybersecurity awareness simulation.
      No device was accessed, no accounts were hacked,
      and no personal information was collected.
      <br><br>
      Never share passwords, OTPs or private information
      with unknown websites.
    </p>
    <button onclick="location.reload()">RESTART EXPERIENCE</button>
  </div>

  <p class="footer">CYBER AWARENESS PROJECT • V2.0</p>

</div>

<div id="overlay" class="overlay hidden"></div>

<div id="popup1" class="popup hidden">
  <div style="font-size:42px">⚠️</div>
  <h2>UNUSUAL ACTIVITY</h2>
  <p>
    This is a simulated security warning.
    Continue to view the awareness demonstration.
  </p>
  <button onclick="nextPopup()">CONTINUE</button>
</div>

<div id="popup2" class="popup hidden">
  <div style="font-size:42px">🚨</div>
  <h2>SECURITY ALERT</h2>
  <p>
    NEVER TRUST UNKNOWN LOGIN PAGES.
    <br><br>
    Your private information deserves protection.
  </p>
  <button onclick="startCountdown()">VIEW FINAL MESSAGE</button>
</div>

<script>

let audioContext;
let timers = [];

function later(fn,delay){
  const t=setTimeout(fn,delay);
  timers.push(t);
}

function sound(frequency,duration,type="square"){
  try{
    if(!audioContext){
      audioContext=new(
        window.AudioContext||window.webkitAudioContext
      )();
    }

    if(audioContext.state==="suspended"){
      audioContext.resume();
    }

    const osc=audioContext.createOscillator();
    const gain=audioContext.createGain();

    osc.type=type;
    osc.frequency.value=frequency;

    gain.gain.setValueAtTime(
      0.12,audioContext.currentTime
    );

    gain.gain.exponentialRampToValueAtTime(
      0.001,audioContext.currentTime+duration
    );

    osc.connect(gain);
    gain.connect(audioContext.destination);

    osc.start();
    osc.stop(audioContext.currentTime+duration);

  }catch(e){
    console.log("Audio unavailable");
  }
}

function show(id){
  document.getElementById(id).classList.remove("hidden");
}

function hide(id){
  document.getElementById(id).classList.add("hidden");
}

function startSimulation(){

  const input=document.getElementById("demoId");

  if(!input.value.trim()){
    alert("Enter a demo username first.");
    return;
  }

  audioContext=new(
    window.AudioContext||window.webkitAudioContext
  )();

  audioContext.resume();

  hide("loginScreen");
  show("loading");

  const terminal=document.getElementById("terminal");

  const lines=[
    "[SIMULATION] Starting demonstration...",
    "[SYSTEM] Loading visual effects...",
    "[CHECK] No real device access requested.",
    "[CHECK] No credentials collected.",
    "[WARNING] Unknown websites can be risky.",
    "[STATUS] Preparing security awareness alert..."
  ];

  let i=0;

  function typeLine(){
    if(i>=lines.length){
      later(()=>{
        hide("loading");
        show("overlay");
        show("popup1");
        document.body.classList.add("flash");
        sound(850,.4);
        later(()=>document.body.classList.remove("flash"),700);
      },400);
      return;
    }

    terminal.innerHTML+=
      '<div>'+lines[i]+'</div>';

    i++;
    later(typeLine,450);
  }

  typeLine();
}

function nextPopup(){

  hide("popup1");
  show("popup2");

  document.body.classList.add("flash");
  sound(1100,.3);

  later(()=>{
    document.body.classList.remove("flash");
  },700);
}

function startCountdown(){

  hide("popup2");
  hide("overlay");
  show("countdownScreen");

  let count=3;

  const display=document.getElementById("countdown");

  display.textContent=count;

  sound(700,.2);

  const interval=setInterval(()=>{

    count--;

    if(count>0){
      display.textContent=count;
      sound(700,.2);
    }else{
      clearInterval(interval);
      display.textContent="GO";
      sound(1000,.5);

      later(()=>{
        hide("countdownScreen");
        show("finalScreen");
      },1000);
    }

  },1000);

  timers.push(interval);
}

</script>

</body>
</html>
