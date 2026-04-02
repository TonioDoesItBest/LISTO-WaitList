
[index.html](https://github.com/user-attachments/files/26449611/index.html)
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Listo — Your chair is waiting.</title>
  <meta name="description" content="Premium barbershop booking, coming to a city near you. Join the founding member waitlist." />
  <meta property="og:title" content="Listo — Your chair is waiting." />
  <meta property="og:description" content="The booking app built for barbers. Simple for clients. Powerful for pros." />
  <meta property="og:image" content="https://joinlisto.com/og.png" />
  <meta name="theme-color" content="#080808" />
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;1,300;1,400&family=Geist+Mono:wght@300;400&display=swap" rel="stylesheet" />

  <style>
    *, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }

    :root {
      --gold: #C9A84C;
      --gold-light: #E8C97A;
      --gold-dim: rgba(201,168,76,0.15);
      --gold-dim2: rgba(201,168,76,0.07);
      --dark: #080808;
      --dark-2: #0f0f0f;
      --dark-3: #161616;
      --text: #e8e4dc;
      --text-muted: #7a7570;
      --error: #c94c4c;
    }

    html { scroll-behavior: smooth; }

    body {
      min-height: 100vh;
      background: var(--dark);
      color: var(--text);
      font-family: 'Cormorant Garamond', serif;
      overflow-x: hidden;
      -webkit-font-smoothing: antialiased;
    }

    /* Grain */
    body::after {
      content: '';
      position: fixed;
      inset: 0;
      background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.85' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.035'/%3E%3C/svg%3E");
      pointer-events: none;
      z-index: 999;
    }

    /* Ambient light */
    .ambient-top {
      position: fixed;
      width: 700px;
      height: 500px;
      top: -250px;
      left: 50%;
      transform: translateX(-50%);
      background: radial-gradient(ellipse, rgba(201,168,76,0.07) 0%, transparent 65%);
      pointer-events: none;
    }

    .ambient-bottom {
      position: fixed;
      width: 400px;
      height: 400px;
      bottom: -200px;
      right: -100px;
      background: radial-gradient(circle, rgba(201,168,76,0.04) 0%, transparent 70%);
      pointer-events: none;
    }

    /* Layout */
    .page {
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      align-items: center;
      padding: 60px 24px 80px;
      position: relative;
      max-width: 100%;
    }

    /* Nav line */
    .nav-line {
      width: 100%;
      max-width: 640px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 72px;
      opacity: 0;
      animation: fadeUp 0.8s ease 0s both;
    }

    .nav-wordmark {
      font-family: 'Geist Mono', monospace;
      font-size: 13px;
      letter-spacing: 0.3em;
      text-transform: uppercase;
      color: var(--gold);
    }

    .nav-tag {
      font-family: 'Geist Mono', monospace;
      font-size: 10px;
      letter-spacing: 0.2em;
      text-transform: uppercase;
      color: var(--text-muted);
    }

    /* Crow SVG */
    .crow-wrap {
      margin-bottom: 24px;
      opacity: 0;
      animation: fadeUp 0.9s ease 0.1s both;
    }

    /* Founding badge */
    .badge {
      display: inline-flex;
      align-items: center;
      gap: 10px;
      border: 1px solid var(--gold-dim);
      padding: 9px 18px;
      margin-bottom: 44px;
      opacity: 0;
      animation: fadeUp 0.9s ease 0.2s both;
    }

    .badge-pulse {
      width: 6px;
      height: 6px;
      border-radius: 50%;
      background: var(--gold);
      animation: pulse 2.2s ease infinite;
      flex-shrink: 0;
    }

    .badge-text {
      font-family: 'Geist Mono', monospace;
      font-size: 10px;
      letter-spacing: 0.2em;
      text-transform: uppercase;
      color: var(--gold);
    }

    /* Hero */
    .hero {
      text-align: center;
      max-width: 600px;
      margin-bottom: 20px;
    }

    .hero-headline {
      font-size: clamp(52px, 12vw, 80px);
      font-weight: 300;
      line-height: 1.02;
      letter-spacing: -0.02em;
      color: var(--text);
      opacity: 0;
      animation: fadeUp 1s ease 0.3s both;
    }

    .hero-headline em {
      font-style: italic;
      color: var(--gold-light);
    }

    .hero-sub {
      margin-top: 20px;
      font-family: 'Geist Mono', monospace;
      font-size: 12px;
      line-height: 2;
      letter-spacing: 0.08em;
      color: var(--text-muted);
      opacity: 0;
      animation: fadeUp 1s ease 0.45s both;
    }

    /* Story line */
    .story-line {
      margin-top: 32px;
      font-size: 18px;
      font-weight: 300;
      font-style: italic;
      color: rgba(232,228,220,0.45);
      letter-spacing: 0.02em;
      opacity: 0;
      animation: fadeUp 1s ease 0.55s both;
      text-align: center;
    }

    /* Divider */
    .divider {
      display: flex;
      align-items: center;
      gap: 14px;
      width: 100%;
      max-width: 440px;
      margin: 52px auto 48px;
      opacity: 0;
      animation: fadeUp 1s ease 0.6s both;
    }

    .div-line {
      flex: 1;
      height: 1px;
      background: linear-gradient(90deg, transparent, var(--gold-dim), transparent);
    }

    .div-mark {
      font-size: 10px;
      color: var(--gold);
      opacity: 0.5;
      letter-spacing: 0.1em;
    }

    /* Form */
    .form-wrap {
      width: 100%;
      max-width: 440px;
      opacity: 0;
      animation: fadeUp 1s ease 0.7s both;
    }

    .field {
      margin-bottom: 14px;
    }

    .field-label {
      display: block;
      font-family: 'Geist Mono', monospace;
      font-size: 10px;
      letter-spacing: 0.22em;
      text-transform: uppercase;
      color: var(--text-muted);
      margin-bottom: 8px;
    }

    input[type="text"],
    input[type="email"],
    input[type="tel"],
    select {
      width: 100%;
      background: var(--dark-3);
      border: 1px solid rgba(201,168,76,0.12);
      color: var(--text);
      font-family: 'Cormorant Garamond', serif;
      font-size: 17px;
      font-weight: 300;
      padding: 15px 18px;
      outline: none;
      transition: border-color 0.25s, background 0.25s;
      -webkit-appearance: none;
      appearance: none;
      border-radius: 0;
    }

    input::placeholder { color: rgba(122,117,112,0.4); font-style: italic; }
    input:focus, select:focus {
      border-color: rgba(201,168,76,0.4);
      background: #111111;
    }

    input.error { border-color: var(--error); }

    .select-wrap { position: relative; }
    .select-wrap::after {
      content: '›';
      position: absolute;
      right: 16px;
      top: 50%;
      transform: translateY(-50%) rotate(90deg);
      color: var(--gold);
      font-size: 20px;
      pointer-events: none;
    }

    select option { background: #161616; color: var(--text); }

    .error-msg {
      font-family: 'Geist Mono', monospace;
      font-size: 10px;
      color: var(--error);
      letter-spacing: 0.1em;
      margin-top: 6px;
      display: none;
    }

    .error-msg.visible { display: block; }

    .cta-btn {
      width: 100%;
      padding: 17px;
      background: var(--gold);
      border: none;
      color: #060606;
      font-family: 'Geist Mono', monospace;
      font-size: 11px;
      font-weight: 400;
      letter-spacing: 0.28em;
      text-transform: uppercase;
      cursor: pointer;
      transition: background 0.2s ease, transform 0.15s ease, letter-spacing 0.2s ease;
      margin-top: 10px;
      border-radius: 0;
    }

    .cta-btn:hover {
      background: var(--gold-light);
      transform: translateY(-2px);
      letter-spacing: 0.32em;
    }

    .cta-btn:active { transform: translateY(0); }

    .cta-btn.loading {
      background: rgba(201,168,76,0.4);
      cursor: not-allowed;
      pointer-events: none;
    }

    /* Privacy note */
    .privacy-note {
      margin-top: 16px;
      text-align: center;
      font-family: 'Geist Mono', monospace;
      font-size: 9px;
      letter-spacing: 0.15em;
      color: rgba(122,117,112,0.35);
    }

    /* Success */
    .success-state {
      display: none;
      text-align: center;
      padding: 20px 0 40px;
      max-width: 440px;
      width: 100%;
    }

    .success-state.visible {
      display: block;
      animation: fadeUp 0.7s ease both;
    }

    .success-glyph {
      font-size: 32px;
      color: var(--gold);
      margin-bottom: 28px;
      display: block;
    }

    .success-headline {
      font-size: clamp(40px, 8vw, 58px);
      font-weight: 300;
      line-height: 1.05;
      margin-bottom: 20px;
    }

    .success-headline em { font-style: italic; color: var(--gold-light); }

    .success-body {
      font-family: 'Geist Mono', monospace;
      font-size: 11px;
      letter-spacing: 0.12em;
      color: var(--text-muted);
      line-height: 2.2;
    }

    .success-divider {
      width: 40px;
      height: 1px;
      background: var(--gold-dim);
      margin: 28px auto;
    }

    /* Footer */
    .footer {
      margin-top: 64px;
      text-align: center;
      font-family: 'Geist Mono', monospace;
      font-size: 9px;
      letter-spacing: 0.18em;
      color: rgba(122,117,112,0.3);
      text-transform: uppercase;
      opacity: 0;
      animation: fadeUp 1s ease 0.9s both;
    }

    /* Animations */
    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(22px); }
      to { opacity: 1; transform: translateY(0); }
    }

    @keyframes pulse {
      0%, 100% { opacity: 1; transform: scale(1); }
      50% { opacity: 0.3; transform: scale(0.8); }
    }

    /* Mobile */
    @media (max-width: 480px) {
      .page { padding: 40px 20px 60px; }
      .nav-line { margin-bottom: 48px; }
    }
  </style>
</head>
<body>

<div class="ambient-top"></div>
<div class="ambient-bottom"></div>

<div class="page">

  <!-- Nav -->
  <nav class="nav-line">
    <span class="nav-wordmark">Listo</span>
    <span class="nav-tag">A City Near You</span>
  </nav>

  <!-- Crow icon -->
  <div class="crow-wrap">
    <svg width="56" height="56" viewBox="0 0 56 56" fill="none" xmlns="http://www.w3.org/2000/svg">
      <circle cx="32" cy="23" r="15" fill="none" stroke="#C9A84C" stroke-width="0.75" opacity="0.35"/>
      <path d="M9 31 C11 25,17 21,23 23 C25 19,29 17,33 19 C37 17,41 19,39 23 C43 23,45 27,41 29 C43 33,39 37,35 35 C31 39,23 39,19 35 C15 37,9 37,9 31Z" fill="#C9A84C" opacity="0.88"/>
      <path d="M19 31 C21 27,29 25,35 29" stroke="#080808" stroke-width="1.2" stroke-linecap="round" fill="none"/>
      <circle cx="36" cy="22" r="1.6" fill="#080808"/>
      <circle cx="36.6" cy="21.4" r="0.5" fill="#C9A84C" opacity="0.5"/>
      <path d="M39 23 L46 21 L41 25Z" fill="#C9A84C" opacity="0.65"/>
    </svg>
  </div>

  <!-- Badge -->
  <div class="badge">
    <div class="badge-pulse"></div>
    <span class="badge-text">Founding Member Access · Now Open</span>
  </div>

  <!-- Hero -->
  <div class="hero">
    <h1 class="hero-headline">Your chair<br>is <em>waiting.</em></h1>
    <p class="hero-sub">
      The booking app built for barbers.<br>
      Simple for clients. Powerful for pros.
    </p>
    <p class="story-line">Your next great cut is one tap away.</p>
  </div>

  <!-- Divider -->
  <div class="divider">
    <div class="div-line"></div>
    <span class="div-mark">✦</span>
    <div class="div-line"></div>
  </div>

  <!-- Form -->
  <div class="form-wrap" id="formWrap">
    <div class="field">
      <label class="field-label" for="name">Full Name</label>
      <input type="text" id="name" placeholder="Your name" autocomplete="name" />
      <span class="error-msg" id="nameErr">Please enter your name</span>
    </div>

    <div class="field">
      <label class="field-label" for="contact">Phone or Email</label>
      <input type="email" id="contact" placeholder="So we can reach you first" autocomplete="email" />
      <span class="error-msg" id="contactErr">Please enter a valid phone or email</span>
    </div>

    <div class="field">
      <label class="field-label" for="role">I am a</label>
      <div class="select-wrap">
        <select id="role">
          <option value="" disabled selected>Select your role</option>
          <option value="client">Client — looking to book</option>
          <option value="barber">Barber — looking to grow</option>
        </select>
      </div>
      <span class="error-msg" id="roleErr">Please select your role</span>
    </div>

    <button class="cta-btn" id="submitBtn" onclick="handleSubmit()">
      Secure My Spot
    </button>

    <p class="privacy-note">No spam. Ever. We'll only reach out when it matters.</p>
  </div>

  <!-- Success -->
  <div class="success-state" id="successState">
    <span class="success-glyph">✦</span>
    <h2 class="success-headline">You're<br><em>in.</em></h2>
    <div class="success-divider"></div>
    <p class="success-body">
      Welcome to the founding circle.<br>
      We'll reach you first when Listo goes live<br>
      in your city.<br><br>
      — The Listo Team
    </p>
  </div>

  <footer class="footer">© 2026 Listo · Coming Soon · Built different.</footer>

</div>

<script>
  // ─── CONFIG ───────────────────────────────────────────────
  // Replace with your Supabase project URL and anon key
  const SUPABASE_URL = 'https://xkzahkjybwxtjcyvlsua.supabase.co';
  const SUPABASE_ANON_KEY = 'sb_publishable_bsKcmhkr5-6KpQIJioldsw_rjseqKtr';
  const TABLE_NAME = 'waitlist';
  // ──────────────────────────────────────────────────────────

  function showError(id, errId) {
    document.getElementById(id).classList.add('error');
    document.getElementById(errId).classList.add('visible');
  }

  function clearError(id, errId) {
    document.getElementById(id).classList.remove('error');
    document.getElementById(errId).classList.remove('visible');
  }

  function validate() {
    let valid = true;
    const name = document.getElementById('name').value.trim();
    const contact = document.getElementById('contact').value.trim();
    const role = document.getElementById('role').value;

    if (!name) { showError('name', 'nameErr'); valid = false; }
    else clearError('name', 'nameErr');

    if (!contact) { showError('contact', 'contactErr'); valid = false; }
    else clearError('contact', 'contactErr');

    if (!role) { showError('role', 'roleErr'); valid = false; }
    else clearError('role', 'roleErr');

    return valid;
  }

  async function handleSubmit() {
    if (!validate()) return;

    const btn = document.getElementById('submitBtn');
    btn.classList.add('loading');
    btn.textContent = 'Securing your spot...';

    const payload = {
      name: document.getElementById('name').value.trim(),
      contact: document.getElementById('contact').value.trim(),
      role: document.getElementById('role').value,
      source: 'qr_mailer',
      created_at: new Date().toISOString()
    };

    try {
      // If Supabase is configured, submit to it
      if (SUPABASE_URL !== 'YOUR_SUPABASE_URL') {
        const res = await fetch(`${SUPABASE_URL}/rest/v1/${TABLE_NAME}`, {
          method: 'POST',
          headers: {
            'Content-Type': 'application/json',
            'apikey': SUPABASE_ANON_KEY,
            'Authorization': `Bearer ${SUPABASE_ANON_KEY}`,
            'Prefer': 'return=minimal'
          },
          body: JSON.stringify(payload)
        });

        if (!res.ok) throw new Error('Submission failed');
      } else {
        // Dev mode — just log
        console.log('Waitlist signup (dev mode):', payload);
        await new Promise(r => setTimeout(r, 800));
      }

      // Show success
      document.getElementById('formWrap').style.display = 'none';
      const s = document.getElementById('successState');
      s.style.display = 'block';
      s.classList.add('visible');

    } catch (err) {
      console.error(err);
      btn.classList.remove('loading');
      btn.textContent = 'Try Again';
      btn.style.background = '#4a1a1a';
      btn.style.color = '#e8e4dc';
      setTimeout(() => {
        btn.style.background = '';
        btn.style.color = '';
        btn.textContent = 'Secure My Spot';
      }, 2500);
    }
  }

  // Clear errors on input
  ['name','contact','role'].forEach(id => {
    const el = document.getElementById(id);
    el.addEventListener('input', () => {
      el.classList.remove('error');
      const errMap = { name: 'nameErr', contact: 'contactErr', role: 'roleErr' };
      document.getElementById(errMap[id]).classList.remove('visible');
    });
  });
</script>

</body>
</html>
