<!DOCTYPE html>
<html lang="vi" data-theme="dark">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1, user-scalable=no, viewport-fit=cover">
  <meta name="theme-color" content="#070b13">
  <title>Tiến Đạt Vn • Share File</title>
  <style>
    /* ========== 1 BIẾN ẢNH DUY NHẤT ========== */
    :root {
      --img: url("https://i.ibb.co/KxS1sx4f/1791141809380-342920311908232227-5721713761588871814-bca86ff374ea9deaee325164a984efa8.jpg");
    }

    :root {
      --bg: #070b13; --bg2: #0b1320;
      --card: rgba(18, 28, 44, .85);
      --card2: rgba(23, 35, 54, .9);
      --line: rgba(255, 255, 255, .1);
      --text: #f8fbff; --muted: #96a9bf;
      --cyan: #62eaff; --blue: #4f8cff;
      --green: #45e6a8; --gold: #ffd266;
      --shadow: 0 24px 70px rgba(0, 0, 0, .42);
      --top: rgba(7, 11, 19, .8);
    }
    [data-theme=light] {
      --bg: #eef3f8; --bg2: #e5edf5;
      --card: rgba(255, 255, 255, .85);
      --card2: rgba(255, 255, 255, .94);
      --line: rgba(14, 43, 72, .1);
      --text: #101b2c; --muted: #667990;
      --cyan: #00a8bd; --blue: #2368ed;
      --green: #0aa66e; --gold: #d88c00;
      --shadow: 0 20px 60px rgba(36, 63, 95, .16);
      --top: rgba(238, 243, 248, .82);
    }
    * { box-sizing: border-box; -webkit-tap-highlight-color: transparent; }
    html, body {
      margin: 0; min-height: 100%;
      font-family: -apple-system, BlinkMacSystemFont, "SF Pro Display", "Segoe UI", Arial, sans-serif;
      color: var(--text);
      background: linear-gradient(180deg, var(--bg), var(--bg2));
      overflow-x: hidden;
    }
    button, a { font: inherit; }

    /* ========== NỀN ẢNH (dùng biến --img) ========== */
    .bg {
      position: fixed; inset: 0; z-index: -2;
      background-image: var(--img);
      background-size: cover;
      background-position: center;
      background-repeat: no-repeat;
      background-attachment: fixed;
    }
    .bg:before {
      content: ""; position: absolute; inset: 0;
      background: rgba(7, 11, 19, 0.75);
      backdrop-filter: blur(4px);
      -webkit-backdrop-filter: blur(4px);
    }
    .bg:after {
      content: ""; position: absolute; inset: 0;
      background-image:
        linear-gradient(rgba(255, 255, 255, .025) 1px, transparent 1px),
        linear-gradient(90deg, rgba(255, 255, 255, .025) 1px, transparent 1px);
      background-size: 40px 40px;
      mask-image: linear-gradient(#000, transparent 78%);
    }

    /* ========== SPLASH ========== */
    .splash {
      position: fixed; inset: 0; z-index: 9999;
      display: flex; flex-direction: column;
      align-items: center; justify-content: center;
      padding: 20px;
      background: linear-gradient(180deg, #050912, #0a1421);
      transition: .55s ease;
    }
    .splash.hide { opacity: 0; visibility: hidden; transform: scale(1.04); }
    .splash-orbit { width: 180px; height: 180px; display: grid; place-items: center; position: relative; }
    .splash-orbit:before {
      content: ""; position: absolute; inset: 0; border-radius: 50%;
      background: conic-gradient(var(--cyan), var(--blue), var(--green), var(--cyan));
      animation: spin 4s linear infinite;
    }
    .splash-orbit:after {
      content: ""; position: absolute; inset: 5px; border-radius: 50%;
      background: #07101b;
    }
    .splash-orbit img {
      width: 154px; height: 154px; border-radius: 50%;
      object-fit: cover; z-index: 2;
    }
    .splash-glow {
      position: absolute; inset: -24px; border-radius: 50%;
      background: radial-gradient(circle, rgba(98, 234, 255, .28), transparent 67%);
      animation: pulse 2s ease-in-out infinite;
    }
    .splash-brand { font-size: 30px; font-weight: 1000; margin-top: 18px; }
    .splash-sub { color: #9eb0c5; margin-top: 7px; }
    .loader {
      width: 220px; height: 5px; border-radius: 99px;
      background: rgba(255, 255, 255, .09); margin-top: 22px; overflow: hidden;
    }
    .loader span {
      display: block; width: 42%; height: 100%;
      background: linear-gradient(90deg, transparent, var(--cyan), var(--blue), transparent);
      animation: load 1.4s infinite;
    }
    @keyframes spin { to { transform: rotate(360deg); } }
    @keyframes pulse { 50% { transform: scale(1.08); opacity: .7; } }
    @keyframes load { from { transform: translateX(-120%); } to { transform: translateX(280%); } }
    @keyframes enter { from { opacity: 0; transform: translateY(12px); } to { opacity: 1; transform: none; } }
    @keyframes shine { 0%, 55% { translate: -130% 0; } 100% { translate: 330% 0; } }

    /* ========== TOPBAR ========== */
    .topbar {
      position: sticky; top: 0; z-index: 100;
      height: 66px; padding: 10px 15px;
      display: flex; align-items: center; justify-content: space-between;
      background: var(--top); border-bottom: 1px solid var(--line);
      backdrop-filter: blur(22px); -webkit-backdrop-filter: blur(22px);
    }
    .brand { display: flex; align-items: center; gap: 10px; }
    .brand img {
      width: 42px; height: 42px; border-radius: 50%;
      object-fit: cover; border: 1px solid var(--line);
    }
    .brand b, .brand small { display: block; }
    .brand b { font-size: 16px; }
    .brand small { font-size: 11px; color: var(--muted); margin-top: 2px; }
    .theme-btn {
      width: 42px; height: 42px; border-radius: 50%;
      border: 1px solid var(--line); background: var(--card);
      color: var(--text); font-size: 20px;
    }
    .wrap { width: min(720px, 100%); margin: auto; padding: 0 14px 108px; }
    .hero { text-align: center; padding: 30px 0 24px; }
    .hero-avatar { width: 116px; height: 116px; margin: auto; position: relative; }
    .hero-avatar span {
      position: absolute; inset: -6px; border-radius: 50%;
      background: conic-gradient(var(--cyan), var(--blue), var(--green), var(--cyan));
      animation: spin 7s linear infinite;
    }
    .hero-avatar span:after {
      content: ""; position: absolute; inset: 4px; border-radius: 50%; background: var(--bg);
    }
    .hero-avatar img {
      position: absolute; inset: 5px; width: 106px; height: 106px;
      border-radius: 50%; object-fit: cover;
    }
    .hero h1 {
      font-size: 34px; margin: 18px 0 7px; letter-spacing: -.8px;
      background: linear-gradient(90deg, var(--cyan), #fff, var(--green));
      -webkit-background-clip: text; color: transparent;
    }
    .hero p { margin: 0; color: var(--muted); }
    .hero-badges { display: flex; justify-content: center; flex-wrap: wrap; gap: 7px; margin-top: 14px; }
    .hero-badges span, .tag {
      padding: 6px 10px; border-radius: 999px;
      font-size: 12px; font-weight: 850;
      border: 1px solid var(--line); background: var(--card);
    }
    .page { display: none; }
    .page.active { display: block; animation: enter .35s ease both; }
    .section-title {
      display: flex; align-items: center; gap: 9px;
      font-size: 15px; font-weight: 950; color: var(--muted);
      text-transform: uppercase; letter-spacing: .5px; margin: 8px 0 13px;
    }
    .section-title span {
      width: 4px; height: 18px; border-radius: 99px;
      background: linear-gradient(var(--cyan), var(--blue));
    }
    .file-list { display: grid; gap: 16px; }
    .file-card, .admin-card {
      position: relative; padding: 18px; border-radius: 28px;
      border: 1px solid var(--line);
      background: linear-gradient(145deg, rgba(98, 234, 255, .12), rgba(79, 140, 255, .1)), var(--card);
      box-shadow: var(--shadow); overflow: hidden;
      backdrop-filter: blur(28px); -webkit-backdrop-filter: blur(28px);
    }
    .file-shine {
      position: absolute; inset: -70% auto auto -25%;
      width: 65%; height: 240%;
      background: linear-gradient(90deg, transparent, rgba(255, 255, 255, .08), transparent);
      transform: rotate(25deg); animation: shine 4.6s infinite;
    }
    .file-top { position: relative; display: flex; align-items: center; gap: 13px; }
    .file-icon {
      width: 58px; height: 58px; border-radius: 19px;
      display: grid; place-items: center; font-size: 27px;
      background: linear-gradient(135deg, rgba(98, 234, 255, .18), rgba(79, 140, 255, .17));
      border: 1px solid rgba(98, 234, 255, .24); flex: 0 0 58px;
    }
    .file-head { min-width: 0; }
    .file-head small { color: var(--muted); font-size: 10px; font-weight: 900; letter-spacing: .8px; }
    .file-head h2 { font-size: 20px; line-height: 1.25; margin: 5px 0 0; overflow-wrap: anywhere; }
    .file-desc { position: relative; color: var(--muted); font-size: 14px; line-height: 1.55; margin: 15px 0; }
    .tags { position: relative; display: flex; flex-wrap: wrap; gap: 7px; }
    .tag.blue { color: var(--cyan); background: rgba(98, 234, 255, .08); }
    .tag.green { color: var(--green); background: rgba(69, 230, 168, .08); }
    .tag.gold { color: var(--gold); background: rgba(255, 210, 102, .08); }
    .download-btn, .zalo-btn {
      position: relative; margin-top: 16px; width: 100%;
      display: flex; align-items: center; justify-content: center; gap: 9px;
      padding: 15px; border-radius: 19px;
      text-decoration: none; font-size: 15px; font-weight: 1000;
    }
    .download-btn {
      color: #00131b;
      background: linear-gradient(135deg, var(--cyan), var(--blue));
      box-shadow: 0 12px 28px rgba(79, 140, 255, .25);
    }
    .download-btn svg { width: 20px; height: 20px; }
    .file-note { text-align: center; color: var(--muted); font-size: 12px; margin-top: 11px; }
    .admin-card { text-align: center; padding-top: 102px; }
    .admin-cover {
      position: absolute; inset: 0 0 auto; height: 115px;
      background: linear-gradient(135deg, rgba(98, 234, 255, .34), rgba(79, 140, 255, .35), rgba(69, 230, 168, .24));
    }
    .admin-avatar {
      position: absolute; top: 51px; left: 50%; translate: -50%;
      width: 96px; height: 96px; border-radius: 50%; object-fit: cover;
      border: 5px solid var(--card2); box-shadow: 0 12px 30px rgba(0, 0, 0, .3);
    }
    .admin-card h2 { font-size: 25px; margin: 13px 0 6px; }
    .admin-card > p { color: var(--muted); margin: 0; }
    .admin-info { display: grid; grid-template-columns: 1fr 1fr; gap: 9px; margin-top: 17px; }
    .admin-info div {
      padding: 12px; border-radius: 17px;
      border: 1px solid var(--line); background: rgba(255, 255, 255, .035);
    }
    .admin-info span, .admin-info b { display: block; }
    .admin-info span { font-size: 11px; color: var(--muted); }
    .admin-info b { font-size: 14px; margin-top: 5px; }
    .zalo-btn { color: #fff; background: linear-gradient(135deg, #0068ff, #00a8ff); }
    .zalo-logo {
      width: 27px; height: 27px; border-radius: 8px;
      background: #fff; color: #0068ff;
      display: grid; place-items: center; font-weight: 1000;
    }
    .bottom-nav {
      position: fixed; z-index: 200; left: 50%;
      bottom: max(13px, env(safe-area-inset-bottom)); translate: -50%;
      width: min(360px, calc(100% - 28px));
      display: grid; grid-template-columns: 1fr 1fr; padding: 6px;
      border-radius: 24px; border: 1px solid var(--line);
      background: var(--top); box-shadow: 0 18px 55px rgba(0, 0, 0, .38);
      backdrop-filter: blur(24px); -webkit-backdrop-filter: blur(24px);
    }
    .nav-item {
      border: 0; border-radius: 18px; background: transparent;
      color: var(--muted); padding: 10px;
      display: grid; place-items: center; gap: 3px;
      font-size: 11px; font-weight: 900;
    }
    .nav-item svg { width: 20px; height: 20px; }
    .nav-item.active {
      color: var(--text);
      background: linear-gradient(135deg, rgba(98, 234, 255, .16), rgba(79, 140, 255, .18));
    }
    .toast {
      position: fixed; z-index: 500; left: 50%; bottom: 100px;
      translate: -50% 15px; opacity: 0; pointer-events: none;
      padding: 10px 14px; border-radius: 999px;
      background: #000; color: #fff;
      font-size: 13px; font-weight: 850; transition: .25s;
    }
    .toast.show { opacity: 1; translate: -50% 0; }
    @media (max-width: 430px) {
      .hero { padding-top: 24px; }
      .file-head h2 { font-size: 17px; }
      .admin-info { grid-template-columns: 1fr; }
      .wrap { padding-inline: 11px; }
    }
  </style>
</head>
<body>
  <div class="bg"></div>

  <!-- SPLASH -->
  <section class="splash" id="splash">
    <div class="splash-orbit">
      <div class="splash-glow"></div>
      <img data-img alt="Tiến Đạt Vn" referrerpolicy="no-referrer">
    </div>
    <div class="splash-brand">Tiến Đạt Vn</div>
    <div class="splash-sub">Share File iOS • An Toàn • Gọn Nhẹ</div>
    <div class="loader"><span></span></div>
  </section>

  <!-- TOPBAR -->
  <header class="topbar">
    <div class="brand">
      <img data-img alt="Tiến Đạt Vn">
      <div>
        <b>Tiến Đạt Vn</b>
        <small>Share File</small>
      </div>
    </div>
    <button class="theme-btn" id="themeBtn" type="button">☾</button>
  </header>

  <main class="wrap">
    <!-- HERO -->
    <section class="hero">
      <div class="hero-avatar">
        <span></span>
        <img data-img alt="Admin Tiến Đạt Vn">
      </div>
      <h1>Tiến Đạt Vn</h1>
      <p>Kho file chia sẻ chính thức từ admin</p>
      <div class="hero-badges">
        <span>✓ Chính Chủ</span>
        <span>⚡ Tải Nhanh</span>
        <span>🍎 iOS</span>
      </div>
    </section>

    <!-- PAGE FILE -->
    <section class="page active" id="page-file">
      <div class="section-title"><span></span>File Mới Nhất</div>
      <div class="file-list">

        <article class="file-card">
          <div class="file-shine"></div>
          <div class="file-top">
            <div class="file-icon">💀</div>
            <div class="file-head">
              <small>FILE SHARE • Tiến Đạt Vn</small>
              <h2>𝐍𝐄𝐔𝐑𝐎•𝐃𝐚𝐫𝐤𝐂𝐨𝐫𝐞💀</h2>
            </div>
          </div>
          <p class="file-desc">File NEURO DarkCore mới từ Tiến Đạt Vn.</p>
          <div class="tags">
            <span class="tag blue">iOS 🍎</span>
            <span class="tag green">DarkCore 💀</span>
            <span class="tag gold">New ⚡</span>
          </div>
          <a class="download-btn" href="https://www.mediafire.com/file/0dtqiyh1b5s3sh4/%25F0%259D%2590%258D%25F0%259D%2590%2584%25F0%259D%2590%2594%25F0%259D%2590%2591%25F0%259D%2590%258E%25E2%2580%25A2%25F0%259D%2590%2583%25F0%259D%2590%259A%25F0%259D%2590%25AB%25F0%259D%2590%25A4%25F0%259D%2590%2582%25F0%259D%2590%25A8%25F0%259D%2590%25AB%25F0%259D%2590%259E%25F0%259F%2592%2580.zip/file" target="_blank" rel="noopener noreferrer">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.3"><path d="M12 3v12M7 10l5 5 5-5"></path><path d="M5 20h14"></path></svg>
            TẢI FILE
          </a>
          <div class="file-note">📌 File được tải qua MediaFire</div>
        </article>

        <article class="file-card">
          <div class="file-shine"></div>
          <div class="file-top">
            <div class="file-icon">🪽</div>
            <div class="file-head">
              <small>FILE SHARE • Tiến Đạt Vn</small>
              <h2>𝙉𝙚𝙪𝙧𝙤•𝙛𝙚𝙡𝙡𝙚𝙣🪽</h2>
            </div>
          </div>
          <p class="file-desc">File Neuro Fallen mới từ Tiến Đạt Vn.</p>
          <div class="tags">
            <span class="tag blue">iOS 🍎</span>
            <span class="tag green">Fallen 🪽</span>
            <span class="tag gold">New ⚡</span>
          </div>
          <a class="download-btn" href="https://www.mediafire.com/file/jqnvv7u0uroovd9/%25F0%259D%2599%2589%25F0%259D%2599%259A%25F0%259D%2599%25AA%25F0%259D%2599%25A7%25F0%259D%2599%25A4%25E2%2580%25A2%25F0%259D%2599%259B%25F0%259D%2599%259A%25F0%259D%2599%25A1%25F0%259D%2599%25A1%25F0%259D%2599%259A%25F0%259D%2599%25A3%25F0%259F%25AA%25BD.zip/file" target="_blank" rel="noopener noreferrer">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.3"><path d="M12 3v12M7 10l5 5 5-5"></path><path d="M5 20h14"></path></svg>
            TẢI FILE
          </a>
          <div class="file-note">📌 File được tải qua MediaFire</div>
        </article>

        <article class="file-card">
          <div class="file-shine"></div>
          <div class="file-top">
            <div class="file-icon">💫</div>
            <div class="file-head">
              <small>FILE SHARE • Tiến Đạt Vn</small>
              <h2>𝙖𝙞𝙢•𝙣𝙤𝙫𝙖💫</h2>
            </div>
          </div>
          <p class="file-desc">Voice Control Commands chia sẻ mới từ Tiến Đạt Vn.</p>
          <div class="tags">
            <span class="tag blue">iOS 🍎</span>
            <span class="tag green">VoiceControl ✓</span>
            <span class="tag gold">New 💫</span>
          </div>
          <a class="download-btn" href="https://www.mediafire.com/file/iweeq2oxxm4mbdc/%F0%9D%99%96%F0%9D%99%9E%F0%9D%99%A2%E2%80%A2%F0%9D%99%A3%F0%9D%99%A4%F0%9D%99%AB%F0%9D%99%96%F0%9F%92%AB.voicecontrolcommands/file" target="_blank" rel="noopener noreferrer">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.3"><path d="M12 3v12M7 10l5 5 5-5"></path><path d="M5 20h14"></path></svg>
            TẢI FILE
          </a>
          <div class="file-note">📌 File được tải qua MediaFire</div>
        </article>

        <article class="file-card">
          <div class="file-shine"></div>
          <div class="file-top">
            <div class="file-icon">👑</div>
            <div class="file-head">
              <small>FILE SHARE • Tiến Đạt Vn</small>
              <h2>𝐍𝐄𝐔𝐑𝐎•𝐕𝟏👑</h2>
            </div>
          </div>
          <p class="file-desc">File chia sẻ mới nhất từ Tiến Đạt Vn.</p>
          <div class="tags">
            <span class="tag blue">iOS 🍎</span>
            <span class="tag green">File Share ✓</span>
            <span class="tag gold">Mới Nhất 👑</span>
          </div>
          <a class="download-btn" href="https://www.mediafire.com/file/y62z3hptoga4n5o/%25F0%259D%2590%258D%25F0%259D%2590%2584%25F0%259D%2590%2594%25F0%259D%2590%2591%25F0%259D%2590%258E%25E2%2580%25A2%25F0%259D%2590%2595%25F0%259D%259F%258F%25F0%259F%2591%2591.zip/file" target="_blank" rel="noopener noreferrer">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.3"><path d="M12 3v12M7 10l5 5 5-5"></path><path d="M5 20h14"></path></svg>
            TẢI FILE
          </a>
          <div class="file-note">📌 File được tải qua MediaFire</div>
        </article>

        <article class="file-card">
          <div class="file-shine"></div>
          <div class="file-top">
            <div class="file-icon">🐾</div>
            <div class="file-head">
              <small>FILE SHARE • Tiến Đạt Vn</small>
              <h2>𝘼𝙞𝙢𝙨𝙬𝙞𝙛𝙩🐾</h2>
            </div>
          </div>
          <p class="file-desc">File AimSwift chia sẻ mới từ Tiến Đạt Vn.</p>
          <div class="tags">
            <span class="tag blue">iOS 🍎</span>
            <span class="tag green">AimSwift ✓</span>
            <span class="tag gold">New ⚡</span>
          </div>
          <a class="download-btn" href="https://www.mediafire.com/file/5ihevmf06ek5xgn/%25F0%259D%2598%25BC%25F0%259D%2599%259E%25F0%259D%2599%25A2%25F0%259D%2599%25A8%25F0%259D%2599%25AC%25F0%259D%2599%259E%25F0%259D%2599%259B%25F0%259D%2599%25A9%25F0%259F%2590%25BE.zip/file" target="_blank" rel="noopener noreferrer">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.3"><path d="M12 3v12M7 10l5 5 5-5"></path><path d="M5 20h14"></path></svg>
            TẢI FILE
          </a>
          <div class="file-note">📌 File được tải qua MediaFire</div>
        </article>

        <article class="file-card">
          <div class="file-shine"></div>
          <div class="file-top">
            <div class="file-icon">🐾</div>
            <div class="file-head">
              <small>FILE SHARE • Tiến Đạt Vn</small>
              <h2>𝙄𝙉𝙁𝙄𝙉𝙄𝙏𝙄 🐾</h2>
            </div>
          </div>
          <p class="file-desc">File chia sẻ từ Tiến Đạt Vn.</p>
          <div class="tags">
            <span class="tag blue">iOS 🍎</span>
            <span class="tag green">Bám Đầu ✓</span>
            <span class="tag gold">Nhạy Tâm ⚡</span>
          </div>
          <a class="download-btn" href="https://www.mediafire.com/file/azz9sr8c1j0jqs6/%25F0%259D%2599%2584%25F0%259D%2599%2589%25F0%259D%2599%2581%25F0%259D%2599%2584%25F0%259D%2599%2589%25F0%259D%2599%2584%25F0%259D%2599%258F%25F0%259D%2599%2584_%25F0%259F%2590%25BE.zip/file" target="_blank" rel="noopener noreferrer">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.3"><path d="M12 3v12M7 10l5 5 5-5"></path><path d="M5 20h14"></path></svg>
            TẢI FILE
          </a>
          <div class="file-note">📌 File được tải qua MediaFire</div>
        </article>

        <article class="file-card">
          <div class="file-shine"></div>
          <div class="file-top">
            <div class="file-icon">⚙️</div>
            <div class="file-head">
              <small>FILE SHARE • Tiến Đạt Vn</small>
              <h2>𝘿𝙋𝙄𝙉𝙀𝙒𝙍𝙊 𝘾𝙇𝘼𝙎𝙄𝘾 ⚙️</h2>
            </div>
          </div>
          <p class="file-desc">File chia sẻ mới từ Tiến Đạt Vn. Tải về trực tiếp và đọc kỹ hướng dẫn bên trong file trước khi sử dụng.</p>
          <div class="tags">
            <span class="tag blue">iOS 🍎</span>
            <span class="tag green">File Share ✓</span>
            <span class="tag gold">New ⚡</span>
          </div>
          <a class="download-btn" href="https://www.mediafire.com/file/dc6ywzi8szc8blb/%F0%9D%98%BF%F0%9D%99%8B%F0%9D%99%84%F0%9D%99%89%F0%9D%99%80%F0%9D%99%92%F0%9D%99%8D%F0%9D%99%8A+%F0%9D%98%BE%F0%9D%99%87%F0%9D%98%BC%F0%9D%99%8E%F0%9D%99%84%F0%9D%98%BE+%E2%9A%99%EF%B8%8F.zip/file" target="_blank" rel="noopener noreferrer">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.3"><path d="M12 3v12M7 10l5 5 5-5"></path><path d="M5 20h14"></path></svg>
            TẢI FILE
          </a>
          <div class="file-note">📌 File được tải qua MediaFire</div>
        </article>

      </div>
    </section>

    <!-- PAGE ADMIN -->
    <section class="page" id="page-admin">
      <div class="section-title"><span></span>Thông Tin Admin</div>
      <article class="admin-card">
        <div class="admin-cover"></div>
        <img class="admin-avatar" data-img alt="Tiến Đạt Vn">
        <h2>Tiến Đạt Vn</h2>
        <p>Admin hỗ trợ file và giải đáp khi cần.</p>
        <div class="admin-info">
          <div><span>Thương hiệu</span><b>Tiến Đạt Vn</b></div>
          <div><span>Liên hệ</span><b>Zalo Admin</b></div>
        </div>
        <a class="zalo-btn" href="http://zalo.me/84394270607" target="_blank" rel="noopener noreferrer">
          <span class="zalo-logo">Z</span>NHẮN ZALO ADMIN
        </a>
      </article>
    </section>
  </main>

  <!-- BOTTOM NAV -->
  <nav class="bottom-nav">
    <button class="nav-item active" data-page="file" type="button">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M14 2H6a2 2 0 00-2 2v16a2 2 0 002 2h12a2 2 0 002-2V8z"></path><path d="M14 2v6h6"></path></svg>
      <span>File</span>
    </button>
    <button class="nav-item" data-page="admin" type="button">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="7" r="4"></circle><path d="M4 21v-2a6 6 0 0112 0v2"></path></svg>
      <span>Admin</span>
    </button>
  </nav>

  <div class="toast" id="toast">Đã mở liên kết</div>

  <script>
    /* ============================================
       CẤU HÌNH — ĐỔI 1 CHỖ, ĐỔI TOÀN BỘ
       ============================================ */
    const CONFIG = {
      IMG: "https://i.ibb.co/KxS1sx4f/1791141809380-342920311908232227-5721713761588871814-bca86ff374ea9deaee325164a984efa8.jpg",
      BRAND: "Tiến Đạt Vn",
      ZALO: "http://zalo.me/84394270607",
      STORAGE_KEY: "tien-dat-vn-theme"
    };

    /* ============================================
       1. TỰ ĐỘNG GÁN ẢNH VÀO TẤT CẢ <img data-img>
       ============================================ */
    document.querySelectorAll('img[data-img]').forEach(img => {
      img.src = CONFIG.IMG;
      img.onerror = () => { img.style.background = 'linear-gradient(135deg,#62eaff,#4f8cff)'; };
    });

    /* ============================================
       2. TỰ ĐỘNG GÁN ẢNH NỀN BACKGROUND
       ============================================ */
    document.documentElement.style.setProperty('--img', `url("${CONFIG.IMG}")`);

    /* ============================================
       3. TỰ ĐỘNG GÁN LINK ZALO (nếu có thẻ a.zalo-btn)
       ============================================ */
    document.querySelectorAll('a.zalo-btn').forEach(a => { a.href = CONFIG.ZALO; });

    /* ============================================
       4. ĐỔI THEME SÁNG / TỐI
       ============================================ */
    const root = document.documentElement;
    const themeBtn = document.getElementById('themeBtn');
    const savedTheme = localStorage.getItem(CONFIG.STORAGE_KEY) || 'dark';
    root.dataset.theme = savedTheme;
    themeBtn.textContent = savedTheme === 'dark' ? '☾' : '☀';
    themeBtn.addEventListener('click', () => {
      const next = root.dataset.theme === 'dark' ? 'light' : 'dark';
      root.dataset.theme = next;
      localStorage.setItem(CONFIG.STORAGE_KEY, next);
      themeBtn.textContent = next === 'dark' ? '☾' : '☀';
    });

    /* ============================================
       5. CHUYỂN TAB FILE / ADMIN
       ============================================ */
    document.querySelectorAll('.nav-item').forEach(btn => btn.addEventListener('click', () => {
      const id = btn.dataset.page;
      document.querySelectorAll('.nav-item').forEach(x => x.classList.remove('active'));
      document.querySelectorAll('.page').forEach(x => x.classList.remove('active'));
      btn.classList.add('active');
      document.getElementById('page-' + id).classList.add('active');
      window.scrollTo({top: 0, behavior: 'smooth'});
    }));

    /* ============================================
       6. TOAST THÔNG BÁO
       ============================================ */
    function showToast(text) {
      const toast = document.getElementById('toast');
      toast.textContent = text;
      toast.classList.add('show');
      clearTimeout(window.tdvToastTimer);
      window.tdvToastTimer = setTimeout(() => toast.classList.remove('show'), 1400);
    }

    /* ============================================
       7. HIỆN TOAST KHI CLICK LINK
       ============================================ */
    document.querySelectorAll('a[target="_blank"]').forEach(link =>
      link.addEventListener('click', () => showToast('Đang mở liên kết...'))
    );

    /* ============================================
       8. ẨN SPLASH SAU 1.5 GIÂY
       ============================================ */
    window.addEventListener('load', () =>
      setTimeout(() => document.getElementById('splash').classList.add('hide'), 1500)
    );

    /* ============================================
       9. LOG RA CONSOLE (TIỆN DEBUG)
       ============================================ */
    console.log('%c🐾 Tiến Đạt Vn • Share File', 'color:#62eaff;font-size:16px;font-weight:bold');
    console.log('📷 Ảnh:', CONFIG.IMG);
    console.log('💬 Zalo:', CONFIG.ZALO);
    console.log('💡 Đổi ảnh/tên/zalo: sửa biến CONFIG ở đầu <script>');
  </script>
</body>
</html>
