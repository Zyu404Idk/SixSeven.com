<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>SixSeven UHC | Official Server</title>  <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@500;700;800;900&family=Poppins:wght@400;500;600;700&display=swap" rel="stylesheet">  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    html {
      scroll-behavior: smooth;
    }

    body {
      background: #080a12;
      color: #ffffff;
      font-family: "Poppins", sans-serif;
      overflow-x: hidden;
    }

    .hero {
      min-height: 100vh;
      padding: 25px;
      position: relative;
      overflow: hidden;
      background:
        radial-gradient(circle at top, rgba(255, 43, 43, 0.22), transparent 45%),
        linear-gradient(rgba(5, 7, 15, 0.78), rgba(5, 7, 15, 0.96)),
        url("https://images.unsplash.com/photo-1511512578047-dfb367046420?auto=format&fit=crop&w=1800&q=90");
      background-size: cover;
      background-position: center;
    }

    .hero::before {
      content: "";
      position: absolute;
      inset: -50%;
      background: radial-gradient(circle, rgba(255, 30, 30, 0.13), transparent 45%);
      animation: backgroundGlow 7s ease-in-out infinite alternate;
      pointer-events: none;
    }

    @keyframes backgroundGlow {
      from {
        transform: translate(-8%, -5%) scale(1);
      }
      to {
        transform: translate(10%, 8%) scale(1.25);
      }
    }

    nav {
      max-width: 1200px;
      margin: auto;
      display: flex;
      justify-content: space-between;
      align-items: center;
      position: relative;
      z-index: 10;
      animation: fadeDown 0.8s ease both;
    }

    @keyframes fadeDown {
      from {
        opacity: 0;
        transform: translateY(-25px);
      }
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }

    .logo {
      font-family: "Orbitron", sans-serif;
      font-size: 30px;
      font-weight: 900;
      letter-spacing: 3px;
      color: #ffffff;
      text-shadow: 0 0 10px #ff2525, 0 0 25px #ff0000;
      animation: logoGlow 2.2s ease-in-out infinite alternate;
    }

    @keyframes logoGlow {
      from {
        text-shadow: 0 0 10px #ff2525, 0 0 25px #ff0000;
      }
      to {
        text-shadow: 0 0 15px #ff5656, 0 0 42px #ff0000, 0 0 70px rgba(255, 0, 0, 0.6);
      }
    }

    .logo span,
    .hero-content h1 span,
    .section-title span {
      color: #ff3434;
    }

    .menu-button {
      width: 52px;
      height: 52px;
      border: 1px solid rgba(255, 75, 75, 0.7);
      border-radius: 13px;
      background: rgba(17, 20, 34, 0.88);
      cursor: pointer;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      gap: 6px;
      transition: 0.25s;
    }

    .menu-button:hover {
      transform: scale(1.08) rotate(3deg);
      box-shadow: 0 0 24px rgba(255, 40, 40, 0.7);
    }

    .menu-button span {
      width: 23px;
      height: 3px;
      border-radius: 20px;
      background: #ffffff;
      transition: 0.25s;
    }

    .menu {
      display: none;
      position: absolute;
      top: 68px;
      right: 0;
      width: 230px;
      padding: 12px;
      border-radius: 15px;
      background: rgba(14, 17, 29, 0.98);
      border: 1px solid rgba(255, 60, 60, 0.55);
      box-shadow: 0 0 25px rgba(255, 30, 30, 0.22);
      transform-origin: top right;
    }

    .menu.show {
      display: block;
      animation: menuOpen 0.28s ease both;
    }

    @keyframes menuOpen {
      from {
        opacity: 0;
        transform: scale(0.88) translateY(-15px);
      }
      to {
        opacity: 1;
        transform: scale(1) translateY(0);
      }
    }

    .menu a {
      display: block;
      padding: 12px 14px;
      margin: 4px 0;
      border-radius: 9px;
      color: #ffffff;
      text-decoration: none;
      font-weight: 600;
      transition: 0.2s;
    }

    .menu a:hover {
      background: linear-gradient(135deg, #ff3636, #a90000);
      transform: translateX(7px);
      box-shadow: 0 0 16px rgba(255, 45, 45, 0.35);
    }

    .hero-content {
      max-width: 900px;
      text-align: center;
      margin: 145px auto 0;
      position: relative;
      z-index: 2;
      animation: heroEnter 1s ease both;
    }

    @keyframes heroEnter {
      from {
        opacity: 0;
        transform: translateY(35px);
      }
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }

    .hero-content h1 {
      font-family: "Orbitron", sans-serif;
      font-size: clamp(45px, 8vw, 92px);
      font-weight: 900;
      letter-spacing: 5px;
      color: #ffffff;
      text-shadow: 0 0 10px #ff2a2a, 0 0 30px #ff0000, 0 0 55px rgba(255, 0, 0, 0.55);
      animation: titlePulse 2.4s ease-in-out infinite alternate;
    }

    @keyframes titlePulse {
      from {
        transform: scale(1);
      }
      to {
        transform: scale(1.025);
      }
    }

    .hero-content p {
      max-width: 700px;
      margin: 22px auto;
      color: #d1d1d1;
      font-size: 17px;
      line-height: 1.7;
    }

    .server-box {
      max-width: 580px;
      margin: 35px auto 0;
      padding: 25px;
      border-radius: 18px;
      background: rgba(13, 16, 28, 0.86);
      border: 1px solid rgba(255, 64, 64, 0.65);
      box-shadow: 0 0 30px rgba(255, 35, 35, 0.2);
      backdrop-filter: blur(8px);
      animation: floatingBox 3.5s ease-in-out infinite;
    }

    @keyframes floatingBox {
      0%, 100% {
        transform: translateY(0);
      }
      50% {
        transform: translateY(-8px);
      }
    }

    .server-box h2 {
      font-family: "Orbitron", sans-serif;
      color: #ff4545;
      margin-bottom: 12px;
      font-size: 20px;
    }

    .ip {
      font-size: 20px;
      font-weight: 700;
      word-break: break-word;
    }

    .port {
      margin-top: 7px;
      color: #b8b8b8;
    }

    .status {
      margin-top: 16px;
      font-weight: 600;
    }

    .online {
      color: #54ff85;
      text-shadow: 0 0 10px rgba(84, 255, 133, 0.6);
      animation: onlinePulse 1.2s ease-in-out infinite alternate;
    }

    @keyframes onlinePulse {
      from {
        opacity: 0.55;
      }
      to {
        opacity: 1;
      }
    }

    .buttons {
      margin-top: 28px;
      display: flex;
      justify-content: center;
      flex-wrap: wrap;
      gap: 12px;
    }

    .btn {
      padding: 14px 21px;
      border-radius: 12px;
      color: #ffffff;
      text-decoration: none;
      font-weight: 700;
      border: 1px solid transparent;
      transition: 0.25s;
      box-shadow: 0 8px 20px rgba(0, 0, 0, 0.3);
    }

    .btn:hover {
      transform: translateY(-5px) scale(1.05);
    }

    .join-btn {
      background: linear-gradient(135deg, #ff2020, #b60000);
      border-color: #ff6464;
      animation: buttonGlow 2.2s ease-in-out infinite alternate;
    }

    .discord-btn {
      background: linear-gradient(135deg, #6875ff, #3d48c7);
      border-color: #8b95ff;
    }

    .youtube-btn {
      background: linear-gradient(135deg, #ff2020, #a90000);
      border-color: #ff7777;
    }

    @keyframes buttonGlow {
      from {
        box-shadow: 0 0 12px rgba(255, 35, 35, 0.25);
      }
      to {
        box-shadow: 0 0 30px rgba(255, 35, 35, 0.65);
      }
    }

    section {
      padding: 90px 25px;
      text-align: center;
    }

    .dark-section {
      background: #0d101a;
    }

    .section-title {
      font-family: "Orbitron", sans-serif;
      font-size: clamp(28px, 5vw, 42px);
      color: #ffffff;
      letter-spacing: 2px;
      text-shadow: 0 0 14px rgba(255, 45, 45, 0.65);
    }

    .section-text {
      max-width: 760px;
      margin: 18px auto 42px;
      color: #bdbdbd;
      line-height: 1.7;
    }

    .features {
      max-width: 1150px;
      margin: auto;
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(225px, 1fr));
      gap: 20px;
    }

    .feature-card,
    .rule-card {
      padding: 27px 20px;
      border-radius: 16px;
      background: #131827;
      border: 1px solid #282f46;
      transition: 0.25s;
    }

    .feature-card:hover,
    .rule-card:hover {
      transform: translateY(-8px) scale(1.02);
      border-color: #ff4444;
      box-shadow: 0 0 25px rgba(255, 35, 35, 0.18);
    }

    .feature-card h3,
    .rule-card h3 {
      color: #ff4a4a;
      margin-bottom: 12px;
      font-size: 19px;
    }

    .feature-card p,
    .rule-card p {
      color: #c4c4c4;
      font-size: 14px;
      line-height: 1.6;
    }

    .owner-card {
      max-width: 780px;
      margin: auto;
      padding: 35px 25px;
      border-radius: 20px;
      background: linear-gradient(145deg, #151a2b, #0d101b);
      border: 1px solid rgba(255, 61, 61, 0.55);
      box-shadow: 0 0 35px rgba(255, 30, 30, 0.17);
    }

    .owner-profile {
      width: 120px;
      height: 120px;
      object-fit: cover;
      border-radius: 50%;
      border: 4px solid #ff4040;
      box-shadow: 0 0 22px rgba(255, 40, 40, 0.7);
      margin-bottom: 15px;
      animation: profileFloat 3s ease-in-out infinite;
    }

    @keyframes profileFloat {
      0%, 100% {
        transform: translateY(0);
      }
      50% {
        transform: translateY(-7px);
      }
    }

    .owner-card h3 {
      font-family: "Orbitron", sans-serif;
      font-size: 28px;
    }

    .owner-role {
      color: #ff4848;
      font-weight: 700;
      margin: 8px 0 15px;
    }

    .owner-card p {
      max-width: 580px;
      margin: auto;
      color: #c9c9c9;
      line-height: 1.7;
    }

    .player-count {
      margin-top: 28px;
      font-family: "Orbitron", sans-serif;
      font-size: 62px;
      color: #58ff87;
      text-shadow: 0 0 18px rgba(88, 255, 135, 0.55);
      animation: countPulse 1.8s ease-in-out infinite alternate;
    }

    @keyframes countPulse {
      from {
        transform: scale(1);
      }
      to {
        transform: scale(1.12);
      }
    }

    .leaderboard {
      max-width: 720px;
      margin: 35px auto 0;
      overflow: hidden;
      border-radius: 16px;
      border: 1px solid #2a3148;
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
      padding: 16px 20px;
      border-top: 1px solid #2a3148;
      color: #d8d8d8;
      transition: 0.2s;
    }

    .leader-row:hover {
      background: rgba(255, 50, 50, 0.08);
      padding-left: 28px;
    }

    .rank-number {
      color: #ff4c4c;
      font-weight: bold;
    }

    .reveal {
      opacity: 0;
      transform: translateY(35px);
      transition: 0.7s ease;
    }

    .reveal.active {
      opacity: 1;
      transform: translateY(0);
    }

    footer {
      background: #05060a;
      padding: 28px;
      text-align: center;
      color: #929292;
      font-size: 14px;
    }

    @media (max-width: 600px) {
      .hero-content {
        margin-top: 110px;
      }

      .logo {
        font-size: 23px;
      }

      .server-box {
        padding: 20px 15px;
      }
    }
  </style></head><body>
  <div class="hero" id="home">
    <nav>
      <div class="logo">SIX<span>SEVEN</span></div>  <div>
    <button class="menu-button" onclick="toggleMenu()" aria-label="Open menu">
      <span></span>
      <span></span>
      <span></span>
    </button>

    <div class="menu" id="menu">
      <a href="#home" onclick="closeMenu()">🏠 Home</a>
      <a href="#information" onclick="closeMenu()">⚔ Information</a>
      <a href="#owner" onclick="closeMenu()">👑 Owner</a>
      <a href="#players" onclick="closeMenu()">👥 Players</a>
      <a href="#leaderboards" onclick="closeMenu()">🏆 Leaderboards</a>
      <a href="#rules" onclick="closeMenu()">📜 Server Rules</a>
      <a href="https://discord.gg/pjp23ub8cand" target="_blank">💬 Join Discord</a>
      <a href="https://youtube.com/@zeusduff?si=MY8Q24IPUKt_ip_H" target="_blank">▶ YouTube</a>
    </div>
  </div>
</nav>

<div class="hero-content">
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
    <a class="btn discord-btn" href="https://discord.gg/pjp23ub8cand" target="_blank">💬 Join Discord</a>
    <a class="btn youtube-btn" href="https://youtube.com/@zeusduff?si=MY8Q24IPUKt_ip_H" target="_blank">▶ YouTube</a>
  </div>
</div>

  </div>  <section id="information" class="reveal">
    <h2 class="section-title">SERVER <span>INFORMATION</span></h2>
    <p class="section-text">SixSeven is a competitive server for players who enjoy UHC battles, ranked matches, events, rewards, and a strong community.</p><div class="features">
  <div class="feature-card"><h3>⚔ UHC Mode</h3><p>Fight intense UHC battles, gather resources, and survive until you are the last player standing.</p></div>
  <div class="feature-card"><h3>💬 Friendly Staff</h3><p>Helpful staff members keep the server fair, active, and enjoyable for everyone.</p></div>
  <div class="feature-card"><h3>🏆 Ranked Matches</h3><p>Prove your skills, climb the ranks, and earn respect in competitive PvP.</p></div>
  <div class="feature-card"><h3>📊 Leaderboards</h3><p>See the top players, strongest fighters, and biggest winners of SixSeven.</p></div>
  <div class="feature-card"><h3>🎁 Giveaways</h3><p>Join our Discord server for giveaways, rewards, updates, and announcements.</p></div>
  <div class="feature-card"><h3>📅 Frequent Events</h3><p>Enjoy tournaments, challenges, community events, and more exciting updates.</p></div>
</div>

  </section>  <section class="dark-section reveal" id="owner">
    <h2 class="section-title">SERVER <span>OWNER</span></h2>
    <p class="section-text">Meet the owner behind SixSeven.</p><div class="owner-card">
  <img class="owner-profile" src="https://i.imgur.com/6VBx3io.png" alt="Zyuuu Profile Picture">
  <h3>Zyuuu</h3>
  <div class="owner-role">👑 Owner of SixSeven Server</div>
  <p>Zyuuu is the owner and creator of SixSeven. The goal of SixSeven is to build a fun, competitive, and active Minecraft Bedrock community where players can enjoy UHC, ranked PvP, leaderboards, giveaways, and frequent events.</p>
</div>

  </section>  <section id="players" class="reveal">
    <h2 class="section-title">ONLINE <span>PLAYERS</span></h2>
    <p class="section-text">Players currently connected to SixSeven Server.</p>
    <div class="player-count">0</div>
    <p style="color:#bdbdbd; margin-top:8px;">Players Online</p>
  </section>  <section class="dark-section reveal" id="leaderboards">
    <h2 class="section-title">TOP <span>LEADERBOARDS</span></h2>
    <p class="section-text">Fight your way to the top and make your name known.</p><div class="leaderboard">
  <h3>⚔ TOP UHC PLAYERS</h3>
  <div class="leader-row"><span><span class="rank-number">#1</span> Coming Soon</span><span>0 Wins</span></div>
  <div class="leader-row"><span><span class="rank-number">#2</span> Coming Soon</span><span>0 Wins</span></div>
  <div class="leader-row"><span><span class="rank-number">#3</span> Coming Soon</span><span>0 Wins</span></div>
</div>

  </section>  <section id="rules" class="reveal">
    <h2 class="section-title">SERVER <span>RULES</span></h2>
    <p class="section-text">Follow these rules to keep SixSeven fair, fun, and active for everyone.</p><div class="features">
  <div class="rule-card"><h3>1. Respect Everyone</h3><p>Do not insult, bully, threaten, or harass other players or staff members.</p></div>
  <div class="rule-card"><h3>2. No Cheating</h3><p>Hacks, clients, auto-clickers, exploits, and unfair advantages are not allowed.</p></div>
  <div class="rule-card"><h3>3. No Teaming</h3><p>Do not team with other players in solo UHC matches unless the event allows it.</p></div>
  <div class="rule-card"><h3>4. No Spam</h3><p>Do not spam chat, flood messages, or repeatedly advertise anything.</p></div>
  <div class="rule-card"><h3>5. No Advertising</h3><p>Do not advertise other Minecraft servers, Discord servers, channels, or social media.</p></div>
  <div class="rule-card"><h3>6. Do Not Abuse Bugs</h3><p>If you find a bug or glitch, report it to staff instead of using it for an advantage.</p></div>
  <div class="rule-card"><h3>7. Listen to Staff</h3><p>Respect staff decisions. If you disagree, calmly contact staff through Discord.</p></div>
  <div class="rule-card"><h3>8. No Inappropriate Names</h3><p>Keep your Minecraft username and skin appropriate for all players.</p></div>
  <div class="rule-card"><h3>9. Keep Chat Clean</h3><p>Avoid excessive caps, toxic messages, and inappropriate content in public chat.</p></div>
  <div class="rule-card"><h3>10. Have Fun</h3><p>Play fair, enjoy the competition, meet players, and help make SixSeven better.</p></div>
</div>

  </section>  <footer>© 2026 SixSeven Server • Not affiliated with Mojang or Microsoft.</footer>  <script>
    function toggleMenu() {
      document.getElementById("menu").classList.toggle("show");
    }

    function closeMenu() {
      document.getElementById("menu").classList.remove("show");
    }

    window.onclick = function(event) {
      const menu = document.getElementById("menu");
      const button = document.querySelector(".menu-button");

      if (!menu.contains(event.target) && !button.contains(event.target)) {
        menu.classList.remove("show");
      }
    };

    const reveals = document.querySelectorAll(".reveal");

    function revealOnScroll() {
      reveals.forEach((element) => {
        const windowHeight = window.innerHeight;
        const elementTop = element.getBoundingClientRect().top;

        if (elementTop < windowHeight - 100) {
          element.classList.add("active");
        }
      });
    }

    window.addEventListener("scroll", revealOnScroll);
    revealOnScroll();
  </script></body>
</html>
