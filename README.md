<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>SixSeven UHC | Official Server</title>
  <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@500;700;800;900&family=Poppins:wght@400;500;600;700&display=swap" rel="stylesheet">  <style>
    *{margin:0;padding:0;box-sizing:border-box}
    html{scroll-behavior:smooth}
    body{background:#070910;color:#fff;font-family:Poppins,Arial,sans-serif;overflow-x:hidden}

    .hero{
      min-height:100vh;padding:20px;position:relative;overflow:hidden;
      background:
        linear-gradient(rgba(5,7,15,.72),rgba(5,7,15,.96)),
        url("https://images.unsplash.com/photo-1511512578047-dfb367046420?auto=format&fit=crop&w=1200&q=70") center/cover;
    }

    .hero:before{
      content:"";position:absolute;inset:-40%;pointer-events:none;
      background:radial-gradient(circle,rgba(255,20,20,.23),transparent 42%);
      animation:glowMove 8s ease-in-out infinite alternate;
    }

    .hero:after{
      content:"";position:absolute;inset:0;pointer-events:none;opacity:.35;
      background-image:linear-gradient(rgba(255,60,60,.12) 1px,transparent 1px),linear-gradient(90deg,rgba(255,60,60,.12) 1px,transparent 1px);
      background-size:45px 45px;
      mask-image:linear-gradient(to bottom,black,transparent 75%);
      animation:gridMove 10s linear infinite;
    }

    @keyframes glowMove{from{transform:translate(-8%,-5%) scale(1)}to{transform:translate(10%,8%) scale(1.25)}}
    @keyframes gridMove{from{background-position:0 0}to{background-position:45px 45px}}

    nav{
      max-width:1100px;margin:auto;padding:12px 15px;display:flex;justify-content:space-between;align-items:center;
      position:relative;z-index:5;border:1px solid rgba(255,80,80,.35);border-radius:15px;background:rgba(8,10,18,.92);
      animation:navEnter .7s ease both;
    }
    @keyframes navEnter{from{opacity:0;transform:translateY(-25px)}to{opacity:1;transform:translateY(0)}}

    .logo{font-family:Orbitron,Arial;font-size:28px;font-weight:900;letter-spacing:3px;text-shadow:0 0 10px #ff2525,0 0 25px #f00;animation:logoPulse 2s ease-in-out infinite alternate}
    .logo span,.hero-content h1 span,.section-title span{color:#ff3434}
    @keyframes logoPulse{to{text-shadow:0 0 18px #ff5656,0 0 42px #f00}}

    .menu-button{width:48px;height:48px;border:1px solid #ff5a5a;border-radius:12px;background:#151827;cursor:pointer;display:flex;flex-direction:column;justify-content:center;align-items:center;gap:6px;transition:.25s}
    .menu-button:hover{transform:rotate(4deg) scale(1.06);box-shadow:0 0 18px rgba(255,30,30,.55)}
    .menu-button span{width:22px;height:3px;border-radius:10px;background:#fff;transition:.25s}
    .menu-button.active span:nth-child(1){transform:translateY(9px) rotate(45deg)}
    .menu-button.active span:nth-child(2){opacity:0}
    .menu-button.active span:nth-child(3){transform:translateY(-9px) rotate(-45deg)}

    .menu{display:none;position:absolute;top:62px;right:0;width:225px;padding:10px;border-radius:14px;background:#121624;border:1px solid #ff4a4a;z-index:20}
    .menu.show{display:block;animation:menuOpen .25s ease both}
    @keyframes menuOpen{from{opacity:0;transform:translateY(-12px) scale(.92)}to{opacity:1;transform:translateY(0) scale(1)}}
    .menu a{display:block;padding:12px;margin:4px 0;border-radius:8px;color:#fff;text-decoration:none;font-weight:bold;transition:.2s}
    .menu a:hover{background:#b60000;transform:translateX(5px)}

    .hero-content{max-width:900px;text-align:center;margin:120px auto 0;position:relative;z-index:2;animation:heroEnter 1s ease both}
    @keyframes heroEnter{from{opacity:0;transform:translateY(35px)}to{opacity:1;transform:translateY(0)}}
    .hero-content h1{font-family:Orbitron,Arial;font-size:clamp(45px,8vw,85px);letter-spacing:5px;text-shadow:0 0 12px #ff2a2a,0 0 35px #f00;animation:titleFloat 3s ease-in-out infinite}
    @keyframes titleFloat{50%{transform:translateY(-7px) scale(1.02)}}
    .hero-content p{max-width:700px;margin:20px auto;color:#d1d1d1;font-size:16px;line-height:1.7}

    .server-box{max-width:580px;margin:30px auto 0;padding:24px;border-radius:16px;position:relative;overflow:hidden;background:rgba(13,16,28,.95);border:1px solid #ff5555;box-shadow:0 0 25px rgba(255,20,20,.22);animation:boxFloat 3.5s ease-in-out infinite}
    .server-box:before{content:"";position:absolute;width:80%;height:100%;top:0;left:-120%;background:linear-gradient(90deg,transparent,rgba(255,255,255,.15),transparent);transform:skewX(-20deg);animation:shine 5s ease-in-out infinite}
    @keyframes boxFloat{50%{transform:translateY(-8px)}}
    @keyframes shine{0%,55%{left:-120%}100%{left:150%}}
    .server-box h2{font-family:Orbitron,Arial;color:#ff4545;margin-bottom:12px;font-size:19px}
    .ip{font-size:20px;font-weight:bold;word-break:break-word}.port{margin-top:7px;color:#b8b8b8}.status{margin-top:16px;font-weight:bold}.online{color:#54ff85;animation:onlinePulse 1.2s ease-in-out infinite alternate}
    @keyframes onlinePulse{to{opacity:.45;text-shadow:0 0 15px #54ff85}}

    .buttons{margin-top:25px;display:flex;justify-content:center;flex-wrap:wrap;gap:12px}
    .btn{padding:14px 20px;border-radius:11px;color:#fff;text-decoration:none;font-weight:bold;position:relative;overflow:hidden;transition:.25s}
    .btn:before{content:"";position:absolute;inset:0;left:-120%;background:linear-gradient(90deg,transparent,rgba(255,255,255,.25),transparent);transition:.55s}
    .btn:hover:before{left:120%}.btn:hover{transform:translateY(-5px) scale(1.04)}
    .join-btn,.youtube-btn{background:#c40000;border:1px solid #ff6666}.discord-btn{background:#4c5bd4;border:1px solid #8995ff}

    section{padding:75px 20px;text-align:center}.dark-section{background:#0d101a}
    .section-title{font-family:Orbitron,Arial;font-size:clamp(27px,5vw,40px);letter-spacing:2px;text-shadow:0 0 12px rgba(255,30,30,.55)}
    .section-text{max-width:760px;margin:18px auto 38px;color:#bdbdbd;line-height:1.7}
    .features{max-width:1100px;margin:auto;display:grid;grid-template-columns:repeat(auto-fit,minmax(220px,1fr));gap:16px}
    .feature-card,.rule-card{padding:24px 18px;border-radius:14px;background:#131827;border:1px solid #282f46;transition:.25s}
    .feature-card:hover,.rule-card:hover{transform:translateY(-7px);border-color:#ff4444;box-shadow:0 0 20px rgba(255,35,35,.18)}
    .feature-card h3,.rule-card h3{color:#ff4a4a;margin-bottom:11px;font-size:18px}.feature-card p,.rule-card p{color:#c4c4c4;font-size:14px;line-height:1.6}

    .owner-card{max-width:760px;margin:auto;padding:32px 22px;border-radius:18px;background:#131827;border:1px solid #ff4a4a;box-shadow:0 0 25px rgba(255,30,30,.12)}
    .owner-profile{width:115px;height:115px;object-fit:cover;border-radius:50%;border:4px solid #ff4040;margin-bottom:14px;animation:profileFloat 3s ease-in-out infinite}
    @keyframes profileFloat{50%{transform:translateY(-8px)}}
    .owner-card h3{font-family:Orbitron,Arial;font-size:27px}.owner-role{color:#ff4848;font-weight:bold;margin:8px 0 15px}.owner-card p{max-width:580px;margin:auto;color:#c9c9c9;line-height:1.7}

    .player-count{margin-top:25px;font-family:Orbitron,Arial;font-size:58px;color:#58ff87;text-shadow:0 0 16px rgba(88,255,135,.5);animation:countPulse 1.5s ease-in-out infinite alternate}
    @keyframes countPulse{to{transform:scale(1.1)}}
    .leaderboard{max-width:720px;margin:30px auto 0;overflow:hidden;border-radius:15px;border:1px solid #2a3148;background:#131827}.leaderboard h3{padding:19px;color:#ff4747;background:#191f31;font-family:Orbitron,Arial}.leader-row{display:flex;justify-content:space-between;padding:16px 18px;border-top:1px solid #2a3148;color:#d8d8d8;transition:.2s}.leader-row:hover{background:rgba(255,50,50,.08);padding-left:25px}.rank-number{color:#ff4c4c;font-weight:bold}
    .reveal{opacity:0;transform:translateY(28px);transition:.6s ease}.reveal.active{opacity:1;transform:translateY(0)}
    footer{background:#05060a;padding:26px;text-align:center;color:#929292;font-size:14px}

    @media(max-width:600px){.hero-content{margin-top:90px}.logo{font-size:22px}.server-box{padding:20px 14px}.btn{width:100%;max-width:290px}.hero:after{animation:none}}
  </style></head>
<body>
  <div class="hero" id="home">
    <nav>
      <div class="logo">SIX<span>SEVEN</span></div>
      <div>
        <button class="menu-button" onclick="toggleMenu()" aria-label="Open menu"><span></span><span></span><span></span></button>
        <div class="menu" id="menu">
          <a href="#home" onclick="closeMenu()">🏠 Home</a>
          <a href="#information" onclick="closeMenu()">⚔ Information</a>
          <a href="#owner" onclick="closeMenu()">👑 Owner</a>
          <a href="#players" onclick="closeMenu()">👥 Players</a>
          <a href="#leaderboards" onclick="closeMenu()">🏆 Leaderboards</a>
          <a href="#rules" onclick="closeMenu()">📜 Server Rules</a>
          <a href="https://discord.gg/pjp23ub8" target="_blank">💬 Join Discord</a>
          <a href="https://youtube.com/@zeusduff" target="_blank">▶ YouTube</a>
        </div>
      </div>
    </nav><div class="hero-content">
  <h1>SIX<span>SEVEN</span></h1>
  <p>The competitive Minecraft Bedrock UHC server. Survive, fight, rank up, and become a SixSeven legend.</p>
  <div class="server-box">
    <h2>⚔ SERVER ADDRESS</h2>
    <div class="ip">SixSevenUHCs.ddns.net</div>
    <div class="port">Port: 19134</div>
    <div class="status">Server Status: <span class="online">● Online</span></div>
  </div>
  <div class="buttons">
    <a class="btn join-btn" href="#information">⚔ Explore Server</a>
    <a class="btn discord-btn" href="https://discord.gg/pjp23ub8" target="_blank">💬 Join Discord</a>
    <a class="btn youtube-btn" href="https://youtube.com/@zeusduff" target="_blank">▶ YouTube</a>
  </div>
</div>

  </div>  <section id="information" class="reveal">
    <h2 class="section-title">SERVER <span>INFORMATION</span></h2>
    <p class="section-text">SixSeven is a competitive server for players who enjoy UHC battles, ranked matches, events, rewards, and a strong community.</p>
    <div class="features">
      <div class="feature-card"><h3>⚔ UHC Mode</h3><p>Fight intense UHC battles, gather resources, and survive until you are the last player standing.</p></div>
      <div class="feature-card"><h3>💬 Friendly Staff</h3><p>Helpful staff members keep the server fair, active, and enjoyable for everyone.</p></div>
      <div class="feature-card"><h3>🏆 Ranked Matches</h3><p>Prove your skills, climb the ranks, and earn respect in competitive PvP.</p></div>
      <div class="feature-card"><h3>📊 Leaderboards</h3><p>See the top players, strongest fighters, and biggest winners of SixSeven.</p></div>
      <div class="feature-card"><h3>🎁 Giveaways</h3><p>Join Discord for giveaways, rewards, updates, and announcements.</p></div>
      <div class="feature-card"><h3>📅 Frequent Events</h3><p>Enjoy tournaments, challenges, community events, and more exciting updates.</p></div>
    </div>
  </section>  <section class="dark-section reveal" id="owner">
    <h2 class="section-title">SERVER <span>OWNER</span></h2>
    <p class="section-text">Meet the owner behind SixSeven.</p>
    <div class="owner-card">
      <img class="owner-profile" src="https://i.imgur.com/6VBx3io.png" alt="Zyuuu Profile Picture">
      <h3>Zyuuu</h3>
      <div class="owner-role">👑 Owner of SixSeven Server</div>
      <p>Zyuuu is the owner and creator of SixSeven. The goal is to build a fun, competitive, and active Minecraft Bedrock community.</p>
    </div>
  </section>  <section id="players" class="reveal">
    <h2 class="section-title">ONLINE <span>PLAYERS</span></h2>
    <p class="section-text">Players currently connected to SixSeven Server.</p>
    <div class="player-count">0</div>
    <p style="color:#bdbdbd;margin-top:8px;">Players Online</p>
  </section>  <section class="dark-section reveal" id="leaderboards">
    <h2 class="section-title">TOP <span>LEADERBOARDS</span></h2>
    <p class="section-text">Fight your way to the top and make your name known.</p>
    <div class="leaderboard">
      <h3>⚔ TOP UHC PLAYERS</h3>
      <div class="leader-row"><span><span class="rank-number">#1</span> Coming Soon</span><span>0 Wins</span></div>
      <div class="leader-row"><span><span class="rank-number">#2</span> Coming Soon</span><span>0 Wins</span></div>
      <div class="leader-row"><span><span class="rank-number">#3</span> Coming Soon</span><span>0 Wins</span></div>
    </div>
  </section>  <section id="rules" class="reveal">
    <h2 class="section-title">SERVER <span>RULES</span></h2>
    <p class="section-text">Follow these rules to keep SixSeven fair, fun, and active for everyone.</p>
    <div class="features">
      <div class="rule-card"><h3>1. Respect Everyone</h3><p>Do not insult, bully, threaten, or harass other players or staff members.</p></div>
      <div class="rule-card"><h3>2. No Cheating</h3><p>Hacks, clients, auto-clickers, exploits, and unfair advantages are not allowed.</p></div>
      <div class="rule-card"><h3>3. No Teaming</h3><p>Do not team in solo UHC matches unless the event allows it.</p></div>
      <div class="rule-card"><h3>4. No Spam</h3><p>Do not spam chat, flood messages, or repeatedly advertise anything.</p></div>
      <div class="rule-card"><h3>5. No Advertising</h3><p>Do not advertise other Minecraft servers or Discord servers.</p></div>
      <div class="rule-card"><h3>6. Do Not Abuse Bugs</h3><p>Report bugs or glitches to staff instead of using them.</p></div>
      <div class="rule-card"><h3>7. Listen to Staff</h3><p>Respect staff decisions and contact them calmly on Discord.</p></div>
      <div class="rule-card"><h3>8. No Inappropriate Names</h3><p>Keep your Minecraft username and skin appropriate.</p></div>
      <div class="rule-card"><h3>9. Keep Chat Clean</h3><p>Avoid excessive caps, toxic messages, and inappropriate content.</p></div>
      <div class="rule-card"><h3>10. Have Fun</h3><p>Play fair and help make SixSeven better.</p></div>
    </div>
  </section>  <footer>© 2026 SixSeven Server • Not affiliated with Mojang or Microsoft.</footer>  <script>
    const menu=document.getElementById("menu");
    const menuButton=document.querySelector(".menu-button");

    function toggleMenu(){
      menu.classList.toggle("show");
      menuButton.classList.toggle("active");
    }

    function closeMenu(){
      menu.classList.remove("show");
      menuButton.classList.remove("active");
    }

    window.addEventListener("click",function(event){
      if(!menu.contains(event.target)&&!menuButton.contains(event.target)){closeMenu();}
    });

    const reveals=document.querySelectorAll(".reveal");
    function revealOnScroll(){
      reveals.forEach(function(item){
        if(item.getBoundingClientRect().top<window.innerHeight-80){
          item.classList.add("active");
        }
      });
    }

    window.addEventListener("scroll",revealOnScroll);
    revealOnScroll();
  </script></body>
</html>
