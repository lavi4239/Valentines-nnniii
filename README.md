# Valentines-nnniii
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>NNI ❤️ BEEBO</title>

<style>
    body {
        margin: 0;
        font-family: "Segoe UI", Roboto, sans-serif;
        background: radial-gradient(circle at center, #ff8da1, #ff4f81);
        color: white;
        height: 100vh;
        overflow: hidden;
        display: flex;
        justify-content: center;
        align-items: center;
        perspective: 1000px; /* Essential for 3D */
    }

    /* Extraordinary 3D Heart */
    .scene {
        width: 120px;
        height: 120px;
        margin: 20px auto;
        perspective: 600px;
    }

    .heart-3d {
        width: 100%;
        height: 100%;
        position: relative;
        transform-style: preserve-3d;
        animation: rotate3d 5s infinite linear;
        cursor: pointer;
    }

    .heart-3d div {
        position: absolute;
        width: 100px;
        height: 100px;
        background: #ff2e63;
        border-radius: 50% 50% 0 0;
        transform-origin: bottom center;
        box-shadow: 0 0 20px rgba(255,46,99,0.5);
    }

    /* Simple 3D Emoji styling */
    .big-emoji {
        font-size: 80px;
        filter: drop-shadow(0 10px 20px rgba(0,0,0,0.3));
        animation: float 3s ease-in-out infinite;
        display: block;
        margin-bottom: 10px;
    }

    .card {
        background: rgba(255, 255, 255, 0.15);
        padding: 40px;
        border-radius: 40px;
        width: 85%;
        max-width: 400px;
        backdrop-filter: blur(20px);
        border: 1px solid rgba(255,255,255,0.3);
        box-shadow: 0 25px 50px rgba(0,0,0,0.2);
        z-index: 10;
    }

    .typing { font-size: 19px; min-height: 50px; font-weight: 500; }

    /* Interactive Love Meter */
    .meter-container {
        width: 100%;
        height: 12px;
        background: rgba(255,255,255,0.3);
        border-radius: 10px;
        margin: 20px 0;
        display: none;
    }
    .meter-fill {
        width: 0%;
        height: 100%;
        background: #fff;
        border-radius: 10px;
        transition: width 0.4s ease;
        box-shadow: 0 0 10px #fff;
    }

    button {
        padding: 14px 28px;
        border: none;
        border-radius: 50px;
        background: white;
        color: #ff4f81;
        font-weight: bold;
        cursor: pointer;
        transition: 0.4s;
        box-shadow: 0 10px 20px rgba(0,0,0,0.1);
    }
    button:hover { transform: translateY(-3px) scale(1.05); box-shadow: 0 15px 25px rgba(0,0,0,0.2); }

    .hidden { display: none; }
    
    .sparkle {
        position: absolute;
        width: 5px;
        height: 5px;
        background: white;
        border-radius: 50%;
        pointer-events: none;
        z-index: 100;
    }

    @keyframes rotate3d {
        from { transform: rotateY(0deg) rotateX(10deg); }
        to { transform: rotateY(360deg) rotateX(10deg); }
    }
    @keyframes float {
        0%, 100% { transform: translateY(0) rotate(0deg); }
        50% { transform: translateY(-15px) rotate(5deg); }
    }
</style>
</head>
<body>

<div class="card">
    <span class="big-emoji">💝</span>
    <h1>NNI ❤️</h1>
    <div class="typing" id="typing"></div>

    <div id="countdown-box">
        <p style="margin-bottom: 5px; opacity: 0.9;">Days until our date:</p>
        <h2 id="timer" style="margin-top: 0; letter-spacing: 1px;"></h2>
    </div>

    <button id="startBtn" onclick="showProposal()">Open My Message 💌</button>

    <div id="proposal" class="hidden">
        <h3>Will you be BEEBO’s Valentine?</h3>
        <div style="height: 100px; position: relative;">
            <button id="yesBtn" onclick="showQuiz()">YES! ✨</button>
            <button id="noBtn" onmouseover="dodge()">No 🙈</button>
        </div>
    </div>

    <div id="quiz" class="hidden">
        <p>Love Meter: <span id="percent">0</span>%</p>
        <div class="meter-container" id="meterBox" style="display: block;">
            <div class="meter-fill" id="meterFill"></div>
        </div>
        <p>Who is BEEBO's favorite person?</p>
        <button onclick="fillMeter()">Obviously NNI! 💖</button>
    </div>

    <div id="final" class="hidden">
        <h2 style="font-size: 30px;">YAYYY! 🥰</h2>
        <div class="big-emoji" style="font-size: 100px;">💍</div>
        <p>You have made me the happiest BEEBO in the world!<br><b>NNI + BEEBO = Forever</b></p>
    </div>
</div>

<script>
// 1. Typewriter Effect
const text = "You are my sunshine, my moonlight, and my favorite person in the whole universe... ✨";
let charIndex = 0;
function type() {
    if (charIndex < text.length) {
        document.getElementById("typing").innerHTML += text.charAt(charIndex);
        charIndex++;
        setTimeout(type, 50);
    }
}
type();

// 2. Countdown Logic (Feb 25, 2026)
const target = new Date("Feb 25, 2026 00:00:00").getTime();
setInterval(() => {
    const now = new Date().getTime();
    const d = target - now;
    const days = Math.floor(d / (1000 * 60 * 60 * 24));
    const hours = Math.floor((d % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
    const mins = Math.floor((d % (1000 * 60 * 60)) / (1000 * 60));
    const secs = Math.floor((d % (1000 * 60)) / 1000);
    document.getElementById("timer").innerHTML = `${days}d ${hours}h ${mins}m ${secs}s`;
}, 1000);

// 3. Interactive Mechanics
function showProposal() {
    document.getElementById("startBtn").classList.add("hidden");
    document.getElementById("proposal").classList.remove("hidden");
}

function dodge() {
    const btn = document.getElementById("noBtn");
    btn.style.position = 'absolute';
    btn.style.left = Math.random() * 80 + "%";
    btn.style.top = Math.random() * 80 + "%";
}

let progress = 0;
function showQuiz() {
    document.getElementById("proposal").classList.add("hidden");
    document.getElementById("quiz").classList.remove("hidden");
}

function fillMeter() {
    progress += 34;
    if(progress > 100) progress = 100;
    document.getElementById("meterFill").style.width = progress + "%";
    document.getElementById("percent").innerText = progress;
    if(progress >= 100) {
        setTimeout(() => {
            document.getElementById("quiz").classList.add("hidden");
            document.getElementById("final").classList.remove("hidden");
            confetti();
        }, 600);
    }
}

// 4. Sparkle Trail
document.addEventListener('mousemove', (e) => {
    const s = document.createElement('div');
    s.className = 'sparkle';
    s.style.left = e.pageX + 'px';
    s.style.top = e.pageY + 'px';
    document.body.appendChild(s);
    setTimeout(() => s.remove(), 800);
});

// 5. Bonus: Confetti Effect
function confetti() {
    for(let i=0; i<50; i++) {
        const heart = document.createElement('div');
        heart.innerHTML = "❤️";
        heart.style.position = "fixed";
        heart.style.left = Math.random() * 100 + "vw";
        heart.style.top = "100vh";
        heart.style.fontSize = Math.random() * 30 + 10 + "px";
        heart.style.transition = "transform " + (Math.random() * 3 + 2) + "s linear, opacity 2s";
        document.body.appendChild(heart);
        
        setTimeout(() => {
            heart.style.transform = `translateY(-110vh) translateX(${Math.random() * 100 - 50}px) rotate(${Math.random() * 360}deg)`;
            heart.style.opacity = "0";
        }, 100);
    }
}
</script>
</body>
</html>
