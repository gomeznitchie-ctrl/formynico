<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>For My Love</title>
<style>
body {
    margin: 0;
    font-family: Arial, sans-serif;
    background-color: #0A1A2F;
    color: #F6F1EA;
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
    flex-direction: column;
}

#login-page { text-align: center; }
#login-page input {
    padding: 10px;
    margin: 10px 0;
    border: none;
    border-radius: 5px;
    width: 200px;
}
#login-page button {
    padding: 10px 20px;
    border: none;
    border-radius: 5px;
    background-color: #C48B9F;
    color: #F6F1EA;
    font-weight: bold;
    cursor: pointer;
}

#main-page {
    display: none;
    flex-direction: column;
    align-items: center;
    padding: 20px;
    max-width: 900px;
    width: 90%;
}

#header { width: 100%; margin-bottom: 15px; border-radius: 15px; overflow: hidden; }
#header-video { width: 100%; max-height: 400px; object-fit: cover; border-radius: 15px; }
#header p { text-align: center; margin-top: 10px; font-size: 1.1em; line-height: 1.4em; color: #F6F1EA; }

@media (max-width: 768px) {
    #header-video { max-height: 300px; }
    #header p { font-size: 1em; }
}

.emotion-button {
    background-color: #C48B9F;
    color: #F6F1EA;
    border: none;
    padding: 12px 20px;
    margin: 8px;
    border-radius: 8px;
    font-size: 1em;
    cursor: pointer;
    transition: all 0.3s;
}
.emotion-button:hover { background-color: #D1A3B3; }

#message-box {
    margin-top: 20px;
    text-align: center;
    background-color: #0B1F3B;
    padding: 20px;
    border-radius: 10px;
    width: 100%;
}

#message-box img, #message-box video, #message-box audio { max-width: 100%; margin-top: 10px; border-radius: 10px; }
</style>
</head>
<body>

<!-- LOGIN PAGE -->
<div id="login-page">
    <h1>Welcome My Big Animal 💙</h1>
    <p>Sorry for all the late replies and naps 😅 I was busy making this for weeks!</p>
    <p>And I wanted to show this to you now, before Christmas week starts… and before you chug a ton of beers 😜… so you’ll actually be sober enough to read it 💙</p>
    <input type="text" id="username" placeholder="Username"><br>
    <input type="password" id="password" placeholder="Password"><br>
    <button onclick="checkLogin()">Enter</button>
    <p id="login-error" style="color: #FFAAAA;"></p>
</div>

<!-- MAIN PAGE -->
<div id="main-page">
    <!-- HEADER VIDEO -->
    <div id="header">
        <video id="header-video" playsinline controls>
            <source src="assets/videos/header.mp4" type="video/mp4">
        </video>
        <p>To my biggest Atay, I made this special for you. This space holds my heart, our memories, and everything I feel for you. Merry Christmas! 🎄💙</p>
    </div>

    <!-- BUTTONS -->
    <div id="buttons">
        <button class="emotion-button" onclick="showMessage('miss')">I just want you</button>
        <button class="emotion-button" onclick="showMessage('love')">Why I love you</button>
        <button class="emotion-button" onclick="showMessage('happy')">Why I’m happy to have you</button>
        <button class="emotion-button" onclick="showMessage('mad')">If you are mad with me</button>
        <button class="emotion-button" onclick="showMessage('doubt')">Our favorite memory of us</button>
        <button class="emotion-button" onclick="showMessage('lucky')">Why I'm lucky to have you</button>
    </div>

    <!-- MESSAGE BOX -->
    <div id="message-box">
        <p>Click a button to see my message 💌</p>
    </div>
</div>

<script>
function checkLogin() {
    const username = document.getElementById('username').value;
    const password = document.getElementById('password').value;
    const error = document.getElementById('login-error');
    const video = document.getElementById('header-video');

    if(username === 'hinico' && password === 'iloveyou') {
        document.getElementById('login-page').style.display = 'none';
        document.getElementById('main-page').style.display = 'flex';
        video.muted = false;
        video.play().catch(() => console.log("Autoplay blocked"));
    } else {
        error.textContent = 'Incorrect username or password 💔';
    }
}

function showMessage(type) {
    const box = document.getElementById('message-box');
    box.innerHTML = '';

    switch(type) {
        case 'miss':
            box.innerHTML = `
<p>I just want you.. my stupid, stubborn animal above anyone else. You are everything I want and need, and you balance me perfectly.</p>
<p>Above all else, I just want Nicolas Pleithner… the one with a little more white hair 😜 but somehow hotter than ever. I want to be with you everywhere and every time 🥺.</p>
<p>I hope this long distance only shapes us back together so we can spend more time side by side, sleep together, and wake up together 💙</p>
<video controls autoplay playsinline>
<source src="assets/videos/memory1.mp4" type="video/mp4">
</video>
            `;
            break;

        case 'love':
            box.innerHTML = `
<button class="emotion-button" id="revealLoveBtn">
Oh why did you click this? Do you really wanna know why I love you?
</button>`;
            document.getElementById('revealLoveBtn').addEventListener('click', () => {
                box.innerHTML = `
<p>Hi Nico,</p>
<p>I don’t really know where to start, but I know I want to start with you...</p>
<p>I truly believe I was meant to find you again, and I feel lucky to have met someone who makes me happy just by being you.</p>
<img src="assets/images/love.jpg" alt="Much love, Chi 😘">
                `;
            });
            break;

        case 'happy':
            box.innerHTML = `
<p>Every moment with you makes me happy 💙</p>
<img src="assets/images/happy.jpg" alt="Happy">
<video controls autoplay playsinline>
<source src="assets/videos/happy.mp4" type="video/mp4">
</video>
            `;
            break;

        case 'mad':
            box.innerHTML = `
<p>If you're mad with me, watch this...🤣😝</p>
<video controls autoplay playsinline>
<source src="assets/videos/sorry1.mp4" type="video/mp4">
</video>
            `;
            break;

        case 'doubt':
            box.innerHTML = `
<p>Of all the trips we’ve been on, of all the photos we’ve taken… this is my favorite memory. Just seeing it makes me feel connected to you, and even months later, I still get butterflies.</p>
<img src="assets/images/stronger.jpg" alt="Stronger">
            `;
            break;

        case 'lucky':
            box.innerHTML = `
<p>You know the first reason why I’m lucky to have you? Because you’re insanely handsome! I can’t stop taking pictures of you, and sometimes even when you sleep 😍</p>
<video controls autoplay playsinline>
<source src="assets/videos/lucky.mp4" type="video/mp4">
</video>
<video controls autoplay playsinline>
<source src="assets/videos/sorry2.mp4" type="video/mp4">
</video>
            `;
            break;

        default:
            box.innerHTML = `<p>Click a button to see my message 💌</p>`;
    }
}
</script>
</body>
</html>
