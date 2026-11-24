<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Азиз — Профиль</title>
<style>
  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    font-family: 'Segoe UI', Tahoma, sans-serif;
    background: linear-gradient(-45deg, #0f0c29, #302b63, #24243e, #1a1a2e);
    background-size: 400% 400%;
    animation: gradientBG 15s ease infinite;
    overflow: hidden;
    position: relative;
  }

  @keyframes gradientBG {
    0%   { background-position: 0% 50%; }
    50%  { background-position: 100% 50%; }
    100% { background-position: 0% 50%; }
  }

  /* Плавающие частицы на фоне */
  .particle {
    position: absolute;
    border-radius: 50%;
    background: rgba(120, 180, 255, 0.35);
    animation: floatUp linear infinite;
    pointer-events: none;
  }

  @keyframes floatUp {
    0%   { transform: translateY(100vh) scale(0); opacity: 0; }
    20%  { opacity: 1; }
    100% { transform: translateY(-20vh) scale(1); opacity: 0; }
  }

  /* Карточка профиля */
  .card {
    position: relative;
    z-index: 10;
    width: 380px;
    max-width: 92vw;
    padding: 40px 30px 30px;
    border-radius: 24px;
    background: rgba(255, 255, 255, 0.07);
    backdrop-filter: blur(20px);
    -webkit-backdrop-filter: blur(20px);
    border: 1px solid rgba(255, 255, 255, 0.15);
    box-shadow: 0 20px 60px rgba(0, 0, 0, 0.5),
                0 0 40px rgba(80, 130, 255, 0.15);
    text-align: center;
    animation: cardAppear 1s cubic-bezier(0.22, 1, 0.36, 1) both;
    transition: transform 0.4s ease, box-shadow 0.4s ease;
  }

  .card:hover {
    transform: translateY(-8px);
    box-shadow: 0 30px 80px rgba(0, 0, 0, 0.6),
                0 0 60px rgba(80, 130, 255, 0.3);
  }

  @keyframes cardAppear {
    from { opacity: 0; transform: translateY(40px) scale(0.95); }
    to   { opacity: 1; transform: translateY(0) scale(1); }
  }

  /* Аватар с вращающимся кольцом */
  .avatar-wrap {
    position: relative;
    width: 130px;
    height: 130px;
    margin: 0 auto 22px;
  }

  .avatar-ring {
    position: absolute;
    inset: -6px;
    border-radius: 50%;
    background: conic-gradient(from 0deg, #00c6ff, #0072ff, #7b2ff7, #00c6ff);
    animation: spin 4s linear infinite;
    filter: blur(2px);
  }

  @keyframes spin {
    to { transform: rotate(360deg); }
  }

  .avatar {
    position: relative;
    width: 100%;
    height: 100%;
    border-radius: 50%;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 52px;
    font-weight: 700;
    color: #fff;
    background: linear-gradient(135deg, #1e3c72, #2a5298);
    border: 4px solid #0f0c29;
    z-index: 2;
    animation: pulse 3s ease-in-out infinite;
  }

  @keyframes pulse {
    0%, 100% { box-shadow: 0 0 0 0 rgba(0, 198, 255, 0.4); }
    50%      { box-shadow: 0 0 0 18px rgba(0, 198, 255, 0); }
  }

  .name {
    font-size: 30px;
    font-weight: 700;
    color: #fff;
    letter-spacing: 1px;
    margin-bottom: 8px;
    background: linear-gradient(90deg, #fff, #a0c4ff, #fff);
    background-size: 200% auto;
    -webkit-background-clip: text;
    background-clip: text;
    -webkit-text-fill-color: transparent;
    animation: shine 3s linear infinite;
  }

  @keyframes shine {
    to { background-position: 200% center; }
  }

  .role {
    font-size: 15px;
    color: #a0a8c8;
    margin-bottom: 24px;
    min-height: 22px;
  }

  .role::after {
    content: '|';
    color: #00c6ff;
    animation: blink 1s step-end infinite;
  }

  @keyframes blink {
    50% { opacity: 0; }
  }

  /* Скиллы */
  .skills {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
    justify-content: center;
    margin-bottom: 28px;
  }

  .skill {
    padding: 8px 16px;
    font-size: 13px;
    font-weight: 600;
    color: #e0e6ff;
    background: rgba(255, 255, 255, 0.08);
    border: 1px solid rgba(255, 255, 255, 0.15);
    border-radius: 30px;
    cursor: default;
    opacity: 0;
    animation: skillPop 0.5s ease forwards;
    transition: all 0.3s ease;
  }

  .skill:hover {
    transform: translateY(-3px) scale(1.08);
    background: linear-gradient(135deg, #00c6ff, #0072ff);
    border-color: transparent;
    box-shadow: 0 8px 20px rgba(0, 114, 255, 0.5);
    color: #fff;
  }

  .skill:nth-child(1) { animation-delay: 0.9s; }
  .skill:nth-child(2) { animation-delay: 1.0s; }
  .skill:nth-child(3) { animation-delay: 1.1s; }
  .skill:nth-child(4) { animation-delay: 1.2s; }
  .skill:nth-child(5) { animation-delay: 1.3s; }
  .skill:nth-child(6) { animation-delay: 1.4s; }

  @keyframes skillPop {
    from { opacity: 0; transform: translateY(10px) scale(0.8); }
    to   { opacity: 1; transform: translateY(0) scale(1); }
  }

  /* Кнопка Telegram */
  .tg-btn {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    gap: 10px;
    width: 100%;
    padding: 15px 20px;
    font-size: 16px;
    font-weight: 600;
    color: #fff;
    text-decoration: none;
    border-radius: 14px;
    background: linear-gradient(135deg, #29b6f6, #0088cc);
    box-shadow: 0 8px 25px rgba(0, 136, 204, 0.5);
    position: relative;
    overflow: hidden;
    transition: transform 0.3s ease, box-shadow 0.3s ease;
    animation: btnAppear 0.6s ease 1.5s both;
  }

  @keyframes btnAppear {
    from { opacity: 0; transform: translateY(15px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  .tg-btn::before {
    content: '';
    position: absolute;
    top: 0;
    left: -100%;
    width: 100%;
    height: 100%;
    background: linear-gradient(120deg, transparent, rgba(255,255,255,0.4), transparent);
    transition: left 0.6s ease;
  }

  .tg-btn:hover {
    transform: translateY(-3px) scale(1.03);
    box-shadow: 0 14px 35px rgba(0, 136, 204, 0.7);
  }

  .tg-btn:hover::before {
    left: 100%;
  }

  .tg-btn:active {
    transform: translateY(-1px) scale(0.99);
  }

  .tg-btn svg {
    width: 22px;
    height: 22px;
    fill: #fff;
    animation: floatIcon 2s ease-in-out infinite;
  }

  @keyframes floatIcon {
    0%, 100% { transform: translateY(0); }
    50%      { transform: translateY(-3px); }
  }
</style>
</head>
<body>

  <div class="card">
    <div class="avatar-wrap">
      <div class="avatar-ring"></div>
      <div class="avatar">A</div>
    </div>

    <h1 class="name">Азиз</h1>
    <p class="role" id="typed"></p>

    <div class="skills">
      <span class="skill">🐍 Python</span>
      <span class="skill">☕ Java</span>
      <span class="skill">⚡ C++</span>
      <span class="skill">🔷 C#</span>
      <span class="skill">💻 JavaScript</span>
      <span class="skill">🚀 И др.</span>
    </div>

    <a class="tg-btn" href="https://t.me/Worqqws" target="_blank" rel="noopener">
      <svg viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
        <path d="M11.944 0A12 12 0 0 0 0 12a12 12 0 0 0 12 12 12 12 0 0 0 12-12A12 12 0 0 0 12 0a12 12 0 0 0-.056 0zm4.962 7.224c.1-.002.321.023.465.14a.506.506 0 0 1 .171.325c.016.093.036.306.02.472-.18 1.898-.962 6.502-1.36 8.627-.168.9-.499 1.201-.82 1.23-.696.065-1.225-.46-1.9-.902-1.056-.693-1.653-1.124-2.678-1.8-1.185-.78-.417-1.21.258-1.91.177-.184 3.247-2.977 3.307-3.23.007-.032.014-.15-.056-.212s-.174-.041-.249-.024c-.106.024-1.793 1.14-5.061 3.345-.48.33-.913.49-1.302.48-.428-.008-1.252-.241-1.865-.44-.752-.245-1.349-.374-1.297-.789.027-.216.325-.437.893-.663 3.498-1.524 5.83-2.529 6.998-3.014 3.332-1.386 4.025-1.627 4.476-1.635z"/>
      </svg>
      Написать в Telegram
    </a>
  </div>

  <script>
    // --- Фоновые частицы ---
    const body = document.body;
    for (let i = 0; i < 25; i++) {
      const p = document.createElement('div');
      p.className = 'particle';
      const size = Math.random() * 6 + 3;
      p.style.width = size + 'px';
      p.style.height = size + 'px';
      p.style.left = Math.random() * 100 + 'vw';
      p.style.animationDuration = (Math.random() * 10 + 8) + 's';
      p.style.animationDelay = (Math.random() * 10) + 's';
      body.appendChild(p);
    }

    // --- Эффект печатающегося текста ---
    const phrases = [
      'Знаю Python, Java, C++ и C#',
      'Пишу код, который работает ✨',
      'Backend & Frontend разработчик',
      'Всегда на связи 🚀'
    ];
    const el = document.getElementById('typed');
    let phraseIndex = 0, charIndex = 0, deleting = false;

    function type() {
      const current = phrases[phraseIndex];
      if (!deleting) {
        el.textContent = current.substring(0, charIndex++);
        if (charIndex > current.length) {
          deleting = true;
          setTimeout(type, 1600);
          return;
        }
      } else {
        el.textContent = current.substring(0, charIndex--);
        if (charIndex < 0) {
          deleting = false;
          phraseIndex = (phraseIndex + 1) % phrases.length;
        }
      }
      setTimeout(type, deleting ? 40 : 80);
    }
    setTimeout(type, 900);
  </script>
</body>
</html>
