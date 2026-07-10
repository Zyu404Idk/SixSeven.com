<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>SixSeven UHC | Official Server</title>

  <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@500;700;800;900&family=Poppins:wght@400;500;600;700&display=swap" rel="stylesheet">

  <style>
    :root {
      --red: #ff3030;
      --red-dark: #9e0000;
      --bg: #080a12;
      --panel: rgba(13, 16, 30, 0.88);
      --text-muted: #b9bdc9;
    }

    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    html {
      scroll-behavior: smooth;
    }

    body {
      background: var(--bg);
      color: #fff;
      font-family: "Poppins", sans-serif;
      overflow-x: hidden;
    }

    .hero {
      min-height: 100vh;
      padding: 22px;
      position: relative;
      isolation: isolate;
      overflow: hidden;
      background:
        linear-gradient(rgba(5, 7, 15, 0.68), rgba(5, 7, 15, 0.96)),
        url("https://images.unsplash.com/photo-1511512578047-dfb367046420?auto=format&fit=crop&w=1800&q=90");
      background-size: cover;
      background-position: center;
    }

    .hero::before {
      content: "";
      position: absolute;
      z-index: -1;
      width: 720px;
      height: 720px;
      border-radius: 50%;
      top: -300px;
      left: -220px;
      background: radial-gradient(circle, rgba(255, 25, 25, 0.45), transparent 67%);
      filter: blur(10px);
      animation: orbMove 10s ease-in-out infinite alternate;
    }

    .hero::after {
      content: "";
      position: absolute;
      inset: 0;
      z-index: -1;
      pointer-events: none;
      opacity: 0.34;
      background-image:
        linear-gradient(rgba(255, 65, 65, 0.11) 1px, transparent 1px),
        linear-gradient(90deg, rgba(255, 65, 65, 0.11) 1px, transparent 1px);
      background-size: 46px 46px;
      mask-image: linear-gradient(to bottom, #000, transparent 80%);
      animation: movingGrid 16s linear infinite;
    }

    @keyframes orbMove {
      from { transform: translate(-5%, -3%) scale(1); }
      to { transform: translate(42%, 45%) scale(1.3); }
    }

    @keyframes movingGrid {
      from { background-position: 0 0; }
      to { background-position: 46px 46px; }
    }

    nav {
      max-width: 1200px;
      margin: auto;
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 12px;
      position: relative;
      z-index: 10;
      animation: fadeDown 0.75s ease both;
    }

    @keyframes fadeDown {
      from { opacity: 0; transform: translateY(-22px); }
      to { opacity: 1; transform: translateY(0); }
    }

    .nav-left,
    .nav-right {
      display: flex;
      align-items: center;
      gap: 12px;
    }

    .logo {
      font-family: "Orbitron", sans-serif;
      font-size: clamp(21px, 4vw, 31px);
      font-weight: 900;
      letter-spacing: 3px;
      white-space: nowrap;
      text-shadow: 0 0 10px #ff2525, 0 0 25px #ff0000;
      animation: logoGlow 2.4s ease-in-out infinite alternate;
    }

    .logo span,
    .hero-title span,
    .section-title span {
      color: var(--red);
    }

    @keyframes logoGlow {
      from { text-shadow: 0 0 10px #ff2525, 0 0 25px #ff0000; }
      to { text-shadow: 0 0 16px #ff5555, 0 0 40px #ff0000, 0 0 65px rgba(255, 0, 0, 0.55); }
    }

    .viewer-count {
      display: flex;
      align-items: center;
      gap: 7px;
      padding: 10px 12px;
      border: 1px solid rgba(255, 75, 75, 0.55);
      border-radius: 12px;
      background: rgba(13, 16, 30, 0.82);
      box-shadow: 0 0 18px rgba(255, 30, 30, 0.16);
      font-family: "Orbitron", sans-serif;
      font-size: 11px;
      font-weight: 800;
      letter-spacing: 1px;
      animation: viewerFloat 3s ease-in-out infinite;
    }

    .eye-icon {
      width: 21px;
      height: 13px;
      position: relative;
      display: inline-block;
      border: 2px solid #ff5555;
      border-radius: 50% / 70%;
      box-shadow: 0 0 10px rgba(255, 60, 60, 0.65);
    }

    .eye-icon::after {
      content: "";
      position: absolute;
      width: 5px;
      height: 5px;
      top: 2px;
      left: 6px;
      border-radius: 50%;
      background: #ff5555;
      box-shadow: 0 0 8px #ff2525;
    }

    #viewerNumber {
      color: #58ff8a;
      text-shadow: 0 0 10px rgba(88, 255, 138, 0.6);
    }

    .viewer-label {
      color: #e3e3e3;
      font-size: 9px;
    }

    @keyframes viewerFloat {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(-4px); }
    }

    .menu-button {
      width: 52px;
      height: 52px;
      border: 1px solid rgba(255, 75, 75, 0.7);
      border-radius: 14px;
      background: rgba(17, 20, 34, 0.9);
      cursor: pointer;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      gap: 6px;
      transition: 0.25s;
    }

    .menu-button:hover {
      transform: scale(1.07) rotate(3deg);
      box-shadow: 0 0 24px rgba(255, 40, 40, 0.65);
    }

    .menu-button span {
      width: 23px;
      height: 3px;
      border-radius: 20px;
      background: #fff;
      transition: 0.25s;
    }

    .menu-button.active span:nth-child(1) {
      transform: translateY(9px) rotate(45deg);
    }

    .menu-button.active span:nth-child(2) {
      opacity: 0;
    }

    .menu-button.active span:nth-child(3) {
      transform: translateY(-9px) rotate(-45deg);
    }

    .menu {
      position: absolute;
      top: 65px;
      right: 0;
      width: 235px;
      padding: 10px;
      border: 1px solid rgba(255, 60, 60, 0.58);
      border-radius: 16px;
      background: rgba(10, 13, 25, 0.97);
      box-shadow: 0 0 30px rgba(255, 30, 30, 0.24);
      transform: scale(0.9) translateY(-14px);
      transform-origin: top right;
      opacity: 0;
      pointer-events: none;
      transition: 0.22s ease;
    }

    .menu.show {
      opacity: 1;
      transform: scale(1) translateY(0);
      pointer-events: auto;
    }

    .menu a {
      display: block;
      padding: 11px 13px;
      margin: 3px 0;
      border-radius: 10px;
      color: #fff;
      text-decoration: none;
      font-size: 14px;
      font-weight: 600;
      transition: 0.2s;
    }

    .menu a:hover {
      transform: translateX(6px);
      background: linear-gradient(135deg, #ff3636, #990000);
      box-shadow: 0 0 16px rgba(255, 45, 45, 0.28);
    }

    .hero-content {
      max-width: 930px;
      margin: 135px auto 0;
      text-align: center;
      position: relative;
      z-index: 2;
      animation: heroEnter 1s ease both;
    }

    @keyframes heroEnter {
      from { opacity: 0; transform: translateY(35px); }
      to { opacity: 1; transform: translateY(0); }
    }

    .hero-title {
      font-family: "Orbitron", sans-serif;
      font-size: clamp(48px, 10vw, 96px);
      font-weight: 900;
      letter-spacing: 5px;
      text-shadow: 0 0 10px #ff2a2a, 0 0 30px #ff0000, 0 0 55px rgba(255, 0, 0, 0.55);
      animation: titlePulse 2.6s ease-in-out infinite alternate;
    }

    @keyframes titlePulse {
      from { transform: scale(1); }
      to { transform: scale(1.025); }
    }

    .hero-description {
      max-width: 720px;
      margin: 22px auto;
      color: #d4d6df;
      font-size: 17px;
      line-height: 1.7;
    }

    .server-box {
      max-width: 600px;
      margin: 35px auto 0;
      padding: 25px;
      border: 1px solid rgba(255, 64, 64, 0.72);
      border-radius: 20px;
      background: var(--panel);
      backdrop-filter: blur(9px);
      box-shadow: 0 0 35px rgba(255, 35, 35, 0.22);
      animation: floatingBox 3.8s ease-in-out infinite;
    }

    @keyframes floatingBox {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(-8px); }
    }

    .server-box h2 {
      font-family: "Orbitron", sans-serif;
      font-size: 20px;
      color: #ff4b4b;
      margin-bottom: 12px;
    }

    .ip {
      font-size: clamp(19px, 4vw, 24px);
      font-weight: 800;
      word-break: break-word;
    }

    .port {
      margin-top: 7px;
      color: #b8bcc8;
    }

    .status {
      margin-top: 16px;
      font-weight: 700;
    }

    .online {
      color: #58ff8a;
      text-shadow: 0 0 10px rgba(88, 255, 138, 0.65);
      animation: onlinePulse 1.2s ease-in-out infinite alternate;
    }

    @keyframes onlinePulse {
      from { opacity: 0.55; }
      to { opacity: 1; }
    }

    .buttons {
      margin-top: 28px;
      display: flex;
      justify-content: center;
      flex-wrap: wrap;
      gap: 12px;
    }

    .btn {
      padding: 14px 20px;
      border: 1px solid transparent;
      border-radius: 13px;
      color: #fff;
      text-decoration: none;
      font-weight: 700;
      transition: 0.25s;
      box-shadow: 0 8px 20px rgba(0, 0, 0, 0.3);
    }

    .btn:hover {
      transform: translateY(-5px) scale(1.04);
    }

    .join-btn {
      background: linear-gradient(135deg, #ff2020, #a90000);
      border-color: #ff6a6a;
      animation: buttonGlow 2.2s ease-in-out infinite alternate;
    }

    .discord-btn {
      background: linear-gradient(135deg, #6978ff, #3c48c9);
      border-color: #9aa2ff;
    }

    .youtube-btn {
      background: linear-gradient(135deg, #ff2020, #9f0000);
      border-color: #ff7373;
    }

    @keyframes buttonGlow {
      from { box-shadow: 0 0 13px rgba(255, 35, 35, 0.25); }
      to { box-shadow: 0 0 32px rgba(255, 35, 35, 0.68); }
    }

    section {
      padding: 88px 22px;
      text-align: center;
    }

    .dark-section {
      background: #0d101a;
    }

    .section-title {
      font-family: "Orbitron", sans-serif;
      font-size: clamp(29px, 5vw, 43px);
      letter-spacing: 2px;
      text-shadow: 0 0 14px rgba(255, 45, 45, 0.65);
    }

    .section-text {
      max-width: 760px;
      margin: 18px auto 40px;
      color: var(--text-muted);
      line-height: 1.7;
    }

    .grid {
      max-width: 1150px;
      margin: auto;
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(225px, 1fr));
      gap: 19px;
    }

    .card {
      padding: 25px 19px;
      border: 1px solid #2b334a;
      border-radius: 16px;
      background: #131827;
      transition: 0.25s;
    }

    .card:hover {
      transform: translateY(-8px) scale(1.02);
      border-color: #ff4444;
      box-shadow: 0 0 25px rgba(255, 35, 35, 0.18);
    }

    .card h3 {
      margin-bottom: 11px;
      color: #ff4a4a;
      font-size: 18px;
    }

    .card p {
      color: #c5c8d2;
      font-size: 14px;
      line-height: 1.6;
    }

    .owner-card {
      max-width: 780px;
      margin: auto;
      padding: 35px 25px;
      border: 1px solid rgba(255, 61, 61, 0.55);
      border-radius: 20px;
      background: linear-gradient(145deg, #151a2b, #0d101b);
      box-shadow: 0 0 35px rgba(255, 30, 30, 0.17);
    }

    .owner-profile {
      width: 120px;
      height: 120px;
      object-fit: cover;
      border: 4px solid #ff4040;
      border-radius: 50%;
      box-shadow: 0 0 22px rgba(255, 40, 40, 0.7);
      margin-bottom: 15px;
      animation: profileFloat 3s ease-in-out infinite;
    }

    @keyframes profileFloat {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(-7px); }
    }

    .owner-card h3 {
      font-family: "Orbitron", sans-serif;
      font-size: 28px;
    }

    .owner-role {
      margin: 8px 0 15px;
      color: #ff4848;
      font-weight: 700;
    }

    .owner-card p {
      max-width: 580px;
      margin: auto;
      color: #c9c9c9;
      line-height: 1.7;
    }

    .player-count {
      margin-top: 25px;
      font-family: "Orbitron", sans-serif;
      font-size: 64px;
      color: #58ff8a;
      text-shadow: 0 0 18px rgba(88, 255, 138, 0.55);
      animation: countPulse 1.8s ease-in-out infinite alternate;
    }

    @keyframes countPulse {
      from { transform: scale(1); }
      to { transform: scale(1.11); }
    }

    .leaderboard {
      max-width: 720px;
      margin: 35px auto 0;
      overflow: hidden;
      border: 1px solid #2a3148;
      border-radius: 16px;
      background: #131827;
    }

    .leaderboard h3 {
      padding: 20px;
      color: #ff4747;
      background: #191f31;
      font-family: "Orbitron", sans-serif;
    }

    .leader-row {
      display: flex;
      justify-content: space-between;
      gap: 12px;
      padding: 16px 20px;
      border-top: 1px solid #2a3148;
      color: #d8d8d8;
      transition: 0.2s;
    }

    .leader-row:hover {
      padding-left: 27px;
      background: rgba(255, 50, 50, 0.08);
    }

    .rank-number {
      color: #ff4c4c;
      font-weight: 800;
    }

    .reveal {
      opacity: 0;
      transform: translateY(35px);
      transition: 0.75s ease;
    }

    .reveal.active {
      opacity: 1;
      transform: translateY(0);
    }

    footer {
      padding: 28px 20px;
      background: #05060a;
      color: #929292;
      text-align: center;
      font-size: 14px;
    }

    @media (max-width: 600px) {
      .hero {
        padding: 18px;
      }

      .viewer-label {
        display: none;
      }

      .viewer-count {
        gap: 6px;
        padding: 10px;
      }

      .hero-content {
        margin-top: 110px;
      }

      .server-box {
        padding: 22px 15px;
      }

      .buttons .btn {
        width: min(100%, 280px);
      }
    }
  </style>
</head>

<body>
  <div class="hero" id="home">
    <nav>
      <div class="nav-left">
        <div class="viewer-count" title="Viewer counter">
          <span class="eye-icon"></span>
          <span id="viewerNumber">1</span>
          <span class="viewer-label">VIEWING</span>
        </div>

        <div class="logo">SIX<span>SEVEN</span></div>
      </div>

      <div class="nav-right">
        <button class="menu-button" id="menuButton" onclick="toggleMenu()" aria-label="Open menu">
          <span></span>
          <span></span>
          <span></span>
        </button>

        <div class="menu" id="menu">
          <a href="#home" onclick="closeMenu()">⌂ Home</a>
          <a href="#information" onclick="closeMenu()">⚔ Information</a>
          <a href="#owner" onclick="closeMenu()">♛ Owner</a>
          <a href="#players" onclick="closeMenu()">◉ Players</a>
          <a href="#leaderboards" onclick="closeMenu()">★ Leaderboards</a>
          <a href="#rules" onclick="closeMenu()">☰ Server Rules</a>
          <a href="https://discord.gg/pjp23ub8cand" target="_blank" rel="noopener">Join Discord</a>
          <a href="https://youtube.com/@zeusduff?si=MY8Q24IPUKt_ip_H" target="_blank" rel="noopener">YouTube</a>
        </div>
      </div>
    </nav>

    <main class="hero-content">
      <h1 class="hero-title">SIX<span>SEVEN</span></h1>
      <p class="hero-description">The competitive Minecraft Bedrock UHC server. Survive, fight, rank up, and become a SixSeven legend.</p>

      <div class="server-box">
        <h2>⚔ SERVER ADDRESS</h2>
        <div class="ip">SixSevenUHCs.ddns.net</div>
        <div class="port">Port: 19134</div>
        <div class="status">Server Status: <span class="online">● Online</span></div>
      </div>

      <div class="buttons">
        <a class="btn join-btn" href="#information">⚔ Explore Server</a>
        <a class="btn discord-btn" href="https://discord.gg/pjp23ub8cand" target="_blank" rel="noopener">💬 Join Discord</a>
        <a class="btn youtube-btn" href="https://youtube.com/@zeusduff?si=MY8Q24IPUKt_ip_H" target="_blank" rel="noopener">▶ YouTube</a>
      </div>
    </main>
  </div>

  <section id="information" class="reveal">
    <h2 class="section-title">SERVER <span>INFORMATION</span></h2>
    <p class="section-text">SixSeven is a competitive server for players who enjoy UHC battles, ranked matches, events, rewards, and a strong community.</p>

    <div class="grid">
      <article class="card"><h3>⚔ UHC Mode</h3><p>Fight intense UHC battles, gather resources, and survive until you are the last player standing.</p></article>
      <article class="card"><h3>💬 Friendly Staff</h3><p>Helpful staff members keep the server fair, active, and enjoyable for everyone.</p></article>
      <article class="card"><h3>🏆 Ranked Matches</h3><p>Prove your skills, climb the ranks, and earn respect in competitive PvP.</p></article>
      <article class="card"><h3>📊 Leaderboards</h3><p>See the top players, strongest fighters, and biggest winners of SixSeven.</p></article>
      <article class="card"><h3>🎁 Giveaways</h3><p>Join our Discord server for giveaways, rewards, updates, and announcements.</p></article>
      <article class="card"><h3>📅 Frequent Events</h3><p>Enjoy tournaments, challenges, community events, and more exciting updates.</p></article>
    </div>
  </section>

  <section class="dark-section reveal" id="owner">
    <h2 class="section-title">SERVER <span>OWNER</span></h2>
    <p class="section-text">Meet the owner behind SixSeven.</p>

    <div class="owner-card">
      <img class="owner-profile" src="https://i.imgur.com/6VBx3io.png" alt="Zyuuu profile picture">
      <h3>Zyuuu</h3>
      <div class="owner-role">👑 Owner of SixSeven Server</div>
      <p>Zyuuu is the owner and creator of SixSeven. The goal is to build a fun, competitive, and active Minecraft Bedrock community with UHC, ranked PvP, leaderboards, giveaways, and events.</p>
    </div>
  </section>

  <section id="players" class="reveal">
    <h2 class="section-title">ONLINE <span>PLAYERS</span></h2>
    <p class="section-text">Players currently connected to SixSeven Server.</p>
    <div class="player-count">0</div>
    <p style="color:#bdbdbd; margin-top:8px;">Players Online</p>
  </section>

  <section class="dark-section reveal" id="leaderboards">
    <h2 class="section-title">TOP <span>LEADERBOARDS</span></h2>
    <p class="section-text">Fight your way to the top and make your name known.</p>

    <div class="leaderboard">
      <h3>⚔ TOP UHC PLAYERS</h3>
      <div class="leader-row"><span><span class="rank-number">#1</span> Coming Soon</span><span>0 Wins</span></div>
      <div class="leader-row"><span><span class="rank-number">#2</span> Coming Soon</span><span>0 Wins</span></div>
      <div class="leader-row"><span><span class="rank-number">#3</span> Coming Soon</span><span>0 Wins</span></div>
    </div>
  </section>

  <section id="rules" class="reveal">
    <h2 class="section-title">SERVER <span>RULES</span></h2>
    <p class="section-text">Follow these rules to keep SixSeven fair, fun, and active for everyone.</p>

    <div class="grid">
      <article class="card"><h3>1. Respect Everyone</h3><p>Do not insult, bully, threaten, or harass players and staff.</p></article>
      <article class="card"><h3>2. No Cheating</h3><p>Hacks, unfair clients, auto-clickers, and exploits are not allowed.</p></article>
      <article class="card"><h3>3. No Teaming</h3><p>Do not team in solo UHC matches unless an event says it is allowed.</p></article>
      <article class="card"><h3>4. No Spam</h3><p>Do not flood chat or repeatedly send the same messages.</p></article>
      <article class="card"><h3>5. No Advertising</h3><p>Do not advertise other servers, Discords, channels, or social accounts.</p></article>
      <article class="card"><h3>6. Report Bugs</h3><p>Report bugs to staff instead of using them for an advantage.</p></article>
      <article class="card"><h3>7. Respect Staff</h3><p>Follow staff instructions. Contact staff calmly on Discord for appeals.</p></article>
      <article class="card"><h3>8. Appropriate Names</h3><p>Keep usernames and skins appropriate for the community.</p></article>
      <article class="card"><h3>9. Keep Chat Clean</h3><p>Avoid toxic messages, excessive caps, and inappropriate public chat.</p></article>
      <article class="card"><h3>10. Have Fun</h3><p>Play fair, enjoy the competition, and help make SixSeven better.</p></article>
    </div>
  </section>

  <footer>© 2026 SixSeven Server • Not affiliated with Moj
