<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<style>
/* ===== General Styles ===== */
body {
    margin: 0;
    font-family: 'Segoe UI', sans-serif;
    background: linear-gradient(135deg, #f2e9ff, #d6c7ff);
    color: #3a2d5c;
}

.container {
    max-width: 480px;
    margin: auto;
    width: 100%;
}

.card {
    background: #ffffffcc;
    border-radius: 20px;
    padding: 30px;
    margin-bottom: 30px;
    box-shadow: 0 10px 25px rgba(90, 60, 150, 0.15);
    width: 100%;
    box-sizing: border-box;
}

h1, h2 {
    text-align: center;
    color: #5a3ea1;
}

h1 { font-size: 2.8rem; }
h2 { font-size: 1.6rem; }

p {
    line-height: 1.7;
    font-size: 1.05rem;
    white-space: pre-line;
}

.button {
    background: #c9b8ff;
    border: none;
    border-radius: 30px;
    padding: 12px 24px;
    font-size: 1rem;
    cursor: pointer;
    color: #3a2d5c;
    transition: all 0.3s ease;
    margin: 8px auto;
    display: block;
}

.button:hover {
    background: #b19cff;
    transform: scale(1.05);
}

.hidden {
    max-height: 0;
    opacity: 0;
    transform: translateY(10px);
    overflow: hidden;
    margin-top: 15px;
    font-style: italic;
    transition: max-height 0.8s ease, opacity 0.5s ease, transform 0.5s ease;
}

.hidden.show {
    max-height: none; /* prevents cutoff */
    opacity: 1;
    transform: translateY(0);
}

.duck {
    font-size: 3rem;
    cursor: pointer;
    display: block;
    margin: 0 auto 10px;
    text-align: center;
}

footer {
    text-align: center;
    opacity: 0.7;
    margin-top: 40px;
    font-style: italic;
}

/* ===== Responsive ===== */
@media (max-width: 600px) {
    .container {
        padding: 20px 10px;
    }

    h1 { font-size: 2rem; }
    h2 { font-size: 1.3rem; }

    .button {
        padding: 10px 20px;
        font-size: 0.9rem;
    }

    #hazbinDuck {
        width: 40%;
        max-width: 120px;
    }

    .card {
        padding: 20px;
    }

    #lastMessage {
        text-align: center;
        padding: 0 10px;
        word-wrap: break-word;
    }
}

/* ===== Images ===== */
img {
    max-width: 100%;
    height: auto;
}
</style>

<script>
// Toggle open-when messages
function toggleMessage(id) {
    const el = document.getElementById(id);
    if (!el) return;
    el.classList.toggle('show');
    el.dataset.opened = 'true';
    checkAllOpened();
    duckReact();
}

// Check if all messages are opened
function checkAllOpened() {
    const messages = document.querySelectorAll('[id^="msg"]');
    const opened = Array.from(messages).every(m => m.dataset.opened === 'true');

    if (opened) {
        const final = document.getElementById('finalMessage');
        const last = document.getElementById('lastMessage');
        if (final) final.classList.add('show');
        if (last) last.classList.add('show');
    }
}

// Duck animation reaction
function duckReact() {
    const duck = document.getElementById('hazbinDuck');
    if (!duck) return;
    duck.style.transform = 'scale(1.1) rotate(-3deg)';
    setTimeout(() => { duck.style.transform = 'scale(1) rotate(0deg)'; }, 300);
}

// Duck click handler
function duckClick() {
    const audio = document.getElementById('duckSound');
    const text = document.getElementById('duckText');
    if (audio) {
        audio.currentTime = 0;
        audio.play();
    }
    if (text) {
        text.style.opacity = '1';
        setTimeout(() => text.style.opacity = '0.6', 800);
    }
    duckReact();
}
</script>
</head>

<body>
<div class="container">

    <!-- Duck Section -->
    <div class="card">
        <h1>heyyy babiiii!</h1>
        <p style="text-align:center;">I've been cooking this up for a few days along with the dictionary, I hope you didn't guess that I'm making you a website but there's still a message here.</p>
        <div style="text-align:center;">
            <img id="hazbinDuck" src="https://media.tenor.com/7hZ5dZKp2JQAAAAC/hazbin-hotel-duck.gif" alt="Hazbin Duck">
            <span class="duck" onclick="duckClick()">🦆</span>
            <p id="duckText" style="font-size:0.9rem; opacity:0.6;">click me</p>
            <audio id="duckSound">
                <source src="https://www.myinstants.com/media/sounds/duck-quack.mp3" type="audio/mpeg">
            </audio>
        </div>
    </div>

    <!-- Open When Messages -->
    <div class="card">
        <h2>A few things I like about you</h2>
        <div style="text-align:center;">
            <button class="button" onclick="toggleMessage('msg1')">uno</button>
            <p id="msg1" class="hidden">How you always make me laugh when I’m sad...</p>

            <button class="button" onclick="toggleMessage('msg2')">dos</button>
            <p id="msg2" class="hidden">How you reassure me when I overthink over little things...</p>

            <button class="button" onclick="toggleMessage('msg3')">tre</button>
            <p id="msg3" class="hidden">How patient and understanding you are with me lalo na...</p>

            <button class="button" onclick="toggleMessage('msg4')">quattro</button>
            <p id="msg4" class="hidden">Your kindness, even from the very start...</p>

            <button class="button" onclick="toggleMessage('msg5')">lima</button>
            <p id="msg5" class="hidden">The way you get excited about the most mundane things...</p>

            <button class="button" onclick="toggleMessage('msg6')">zes</button>
            <p id="msg6" class="hidden">How thoughtful you are. You do such small sweet things...</p>

            <button class="button" onclick="toggleMessage('msg7')">siete</button>
            <p id="msg7" class="hidden">For simply being you, you don't try to fit in with any trend...</p>
        </div>
    </div>

    <!-- Original Final Message -->
    <div class="card">
        <h2 id="finalMessage" class="hidden">Waittt, there's more !!!</h2>
    </div>

    <!-- Last Message -->
    <div class="card">
        <h2>READ IT POOOOO</h2>
        <div id="lastMessage" class="hidden" style="text-align:center;">
            <p>hallooooo!</p>
            <p>all i want to say is thank you for making me feel happy, safe, and loved on days i didn’t...</p>
            <p>i didn’t plan for you, i didn’t expect us to be anything other than being friends...</p>
            <p>thank you for loving me the way you do softly, patiently, consistently...</p>
            <p>loving you feels chaotic in the best way...</p>
            <p>i don’t know where this will take us, maybe I'll sagot you na to be my boyfriend...</p>
            <p>im ending this message with a kiss and a hug ＼(^o^)／</p>
        </div>
    </div>

    <footer>I love you, always my mataray na dabe :P</footer>
</div>
</body>
