fgg



<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Kalakar – Handicrafts & Artisans</title>
  <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;1,400&family=Cormorant+Garamond:wght@300;400;500&family=Raleway:wght@300;400;600&display=swap" rel="stylesheet"/>
  <style>
    :root {
      --cream: #f5ede0;
      --warm-white: #fdf8f2;
      --terracotta: #c0603a;
      --terracotta-dark: #9a4a2c;
      --ochre: #d4933a;
      --forest: #3a5c3e;
      --clay: #8c5e3c;
      --ink: #1e1612;
      --text-muted: #6b5240;
      --border: rgba(140,94,60,0.2);
    }
    * { margin:0; padding:0; box-sizing:border-box; }
    html { scroll-behavior: smooth; }

    body {
      font-family: 'Cormorant Garamond', Georgia, serif;
      background: var(--warm-white);
      color: var(--ink);
      cursor: none;
    }

    /* Custom cursor */
    .cursor {
      width: 12px; height: 12px;
      background: var(--terracotta);
      border-radius: 50%;
      position: fixed; top:0; left:0;
      pointer-events: none;
      z-index: 9999;
      transition: transform 0.15s ease;
      mix-blend-mode: multiply;
    }
    .cursor-follower {
      width: 36px; height: 36px;
      border: 1.5px solid var(--terracotta);
      border-radius: 50%;
      position: fixed; top:0; left:0;
      pointer-events: none;
      z-index: 9998;
      transition: all 0.3s ease;
      opacity: 0.6;
    }

    /* NAV */
    nav {
      position: fixed; top:0; width:100%; z-index: 1000;
      padding: 18px 60px;
      display: flex; align-items: center; justify-content: space-between;
      background: rgba(253,248,242,0.92);
      backdrop-filter: blur(10px);
      border-bottom: 1px solid var(--border);
      transition: padding 0.3s;
    }
    nav.scrolled { padding: 12px 60px; }
    .nav-logo {
      font-family: 'Playfair Display', serif;
      font-size: 1.7rem; font-weight: 700;
      color: var(--terracotta);
      letter-spacing: 0.02em;
      text-decoration: none;
    }
    .nav-logo span { color: var(--ochre); font-style: italic; }
    .nav-links { display: flex; gap: 40px; list-style: none; }
    .nav-links a {
      font-family: 'Raleway', sans-serif;
      font-size: 0.78rem; font-weight: 600;
      letter-spacing: 0.15em; text-transform: uppercase;
      color: var(--text-muted); text-decoration: none;
      position: relative; padding-bottom: 4px;
      transition: color 0.3s;
    }
    .nav-links a::after {
      content: '';
      position: absolute; bottom:0; left:0;
      width:0; height:1.5px;
      background: var(--terracotta);
      transition: width 0.3s ease;
    }
    .nav-links a:hover { color: var(--terracotta); }
    .nav-links a:hover::after { width:100%; }

    /* HERO */
    #home {
      min-height: 100vh;
      display: grid; grid-template-columns: 1fr 1fr;
      position: relative; overflow: hidden;
    }
    .hero-left {
      display: flex; flex-direction: column; justify-content: center;
      padding: 140px 60px 80px;
      position: relative; z-index: 2;
    }
    .hero-tag {
      font-family: 'Raleway', sans-serif;
      font-size: 0.7rem; font-weight: 600;
      letter-spacing: 0.3em; text-transform: uppercase;
      color: var(--ochre); margin-bottom: 20px;
      display: flex; align-items: center; gap: 12px;
    }
    .hero-tag::before {
      content: ''; display: block;
      width: 40px; height: 1px; background: var(--ochre);
    }
    .hero-title {
      font-family: 'Playfair Display', serif;
      font-size: clamp(3rem, 5vw, 5.5rem);
      line-height: 1.05; font-weight: 700;
      color: var(--ink); margin-bottom: 28px;
    }
    .hero-title em { color: var(--terracotta); font-style: italic; }
    .hero-desc {
      font-size: 1.15rem; line-height: 1.9;
      color: var(--text-muted); max-width: 440px;
      font-weight: 300; margin-bottom: 48px;
    }
    .btn-group { display: flex; gap: 20px; align-items: center; }
    .btn-primary {
      display: inline-block;
      padding: 16px 40px;
      background: var(--terracotta);
      color: #fff; text-decoration: none;
      font-family: 'Raleway', sans-serif;
      font-size: 0.78rem; font-weight: 600;
      letter-spacing: 0.15em; text-transform: uppercase;
      transition: all 0.3s; border: none; cursor: none;
    }
    .btn-primary:hover { background: var(--terracotta-dark); transform: translateY(-2px); }
    .btn-ghost {
      display: inline-flex; align-items: center; gap: 10px;
      color: var(--text-muted); text-decoration: none;
      font-family: 'Raleway', sans-serif;
      font-size: 0.78rem; font-weight: 600;
      letter-spacing: 0.12em; text-transform: uppercase;
      transition: color 0.3s; cursor: none;
    }
    .btn-ghost:hover { color: var(--terracotta); }
    .btn-ghost svg { transition: transform 0.3s; }
    .btn-ghost:hover svg { transform: translateX(4px); }

    .hero-right {
      position: relative;
      background: var(--cream);
      overflow: hidden;
    }
    .hero-pattern {
      position: absolute; inset: 0;
      background-image:
        radial-gradient(circle at 20% 30%, rgba(192,96,58,0.12) 0%, transparent 50%),
        radial-gradient(circle at 80% 70%, rgba(212,147,58,0.1) 0%, transparent 50%);
    }
    .hero-art {
      position: absolute; inset: 0;
      display: flex; align-items: center; justify-content: center;
    }
    .mandala {
      width: 500px; height: 500px;
      position: relative;
    }
    .mandala svg {
      width: 100%; height: 100%;
      animation: rotateSlow 40s linear infinite;
      opacity: 0.15;
    }
    .mandala-inner {
      position: absolute; inset: 0;
      display: flex; align-items: center; justify-content: center;
    }
    .mandala-inner svg {
      width: 300px; height: 300px;
      animation: rotateSlow 25s linear infinite reverse;
      opacity: 0.2;
    }
    @keyframes rotateSlow { to { transform: rotate(360deg); } }

    .hero-craft-cards {
      position: absolute; bottom: 60px; left: 40px; right: 40px;
      display: flex; gap: 16px;
    }
    .craft-chip {
      padding: 10px 20px;
      background: rgba(253,248,242,0.85);
      border: 1px solid var(--border);
      font-family: 'Raleway', sans-serif;
      font-size: 0.72rem; font-weight: 600;
      letter-spacing: 0.1em; text-transform: uppercase;
      color: var(--clay);
      backdrop-filter: blur(8px);
      animation: floatUp 0.6s ease forwards;
      opacity: 0;
    }
    .craft-chip:nth-child(1) { animation-delay: 0.8s; }
    .craft-chip:nth-child(2) { animation-delay: 1.0s; }
    .craft-chip:nth-child(3) { animation-delay: 1.2s; }
    @keyframes floatUp { from { opacity:0; transform:translateY(20px); } to { opacity:1; transform:translateY(0); } }

    .hero-stats {
      display: flex; gap: 50px; margin-top: 60px;
      padding-top: 40px; border-top: 1px solid var(--border);
    }
    .stat-num {
      font-family: 'Playfair Display', serif;
      font-size: 2.2rem; font-weight: 700; color: var(--terracotta);
      line-height: 1;
    }
    .stat-label {
      font-family: 'Raleway', sans-serif;
      font-size: 0.7rem; font-weight: 600;
      letter-spacing: 0.12em; text-transform: uppercase;
      color: var(--text-muted); margin-top: 6px;
    }

    /* SECTION BASE */
    section { position: relative; }
    .section-tag {
      font-family: 'Raleway', sans-serif;
      font-size: 0.68rem; font-weight: 600;
      letter-spacing: 0.3em; text-transform: uppercase;
      color: var(--ochre); margin-bottom: 16px;
      display: flex; align-items: center; gap: 12px;
    }
    .section-tag::before {
      content: ''; display: block;
      width: 30px; height: 1px; background: var(--ochre);
    }
    .section-title {
      font-family: 'Playfair Display', serif;
      font-size: clamp(2rem, 3.5vw, 3.2rem);
      line-height: 1.15; font-weight: 700; color: var(--ink);
    }
    .section-title em { color: var(--terracotta); font-style: italic; }

    /* ABOUT */
    #about {
      padding: 120px 60px;
      display: grid; grid-template-columns: 1fr 1fr;
      gap: 80px; align-items: center;
      background: var(--cream);
    }
    .about-visual {
      position: relative;
    }
    .about-img-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      grid-template-rows: auto auto;
      gap: 16px;
    }
    .img-block {
      border-radius: 2px;
      overflow: hidden;
      position: relative;
    }
    .img-block:first-child {
      grid-row: span 2;
      min-height: 420px;
    }
    .img-block:not(:first-child) {
      min-height: 190px;
    }
    .img-placeholder {
      width: 100%; height: 100%;
      min-height: inherit;
      display: flex; align-items: center; justify-content: center;
      flex-direction: column; gap: 12px;
      font-family: 'Raleway', sans-serif;
      font-size: 0.7rem; letter-spacing: 0.12em; text-transform: uppercase;
      color: rgba(255,255,255,0.8);
      position: relative; overflow: hidden;
    }
    .img-placeholder.bg1 { background: linear-gradient(135deg, #c0603a 0%, #9a4a2c 100%); }
    .img-placeholder.bg2 { background: linear-gradient(135deg, #d4933a 0%, #b07a2a 100%); }
    .img-placeholder.bg3 { background: linear-gradient(135deg, #3a5c3e 0%, #2a4430 100%); }
    .img-placeholder svg { opacity: 0.6; }

    .about-badge {
      position: absolute;
      bottom: -20px; right: -20px;
      width: 120px; height: 120px;
      background: var(--ink);
      border-radius: 50%;
      display: flex; align-items: center; justify-content: center;
      flex-direction: column;
      color: var(--cream);
      text-align: center;
      z-index: 3;
    }
    .about-badge-num {
      font-family: 'Playfair Display', serif;
      font-size: 2rem; font-weight: 700; line-height: 1;
      color: var(--ochre);
    }
    .about-badge-text {
      font-family: 'Raleway', sans-serif;
      font-size: 0.6rem; letter-spacing: 0.1em; text-transform: uppercase;
      color: rgba(245,237,224,0.7);
      margin-top: 4px;
    }

    .about-content {}
    .about-content .section-title { margin-bottom: 24px; }
    .about-desc {
      font-size: 1.05rem; line-height: 2;
      color: var(--text-muted); font-weight: 300;
      margin-bottom: 20px;
    }
    .about-values {
      display: flex; flex-direction: column; gap: 16px;
      margin-top: 36px;
    }
    .value-item {
      display: flex; align-items: flex-start; gap: 20px;
      padding: 20px; background: var(--warm-white);
      border-left: 3px solid var(--terracotta);
    }
    .value-icon {
      width: 40px; height: 40px; flex-shrink: 0;
      color: var(--terracotta);
    }
    .value-title {
      font-family: 'Playfair Display', serif;
      font-size: 1rem; font-weight: 700; color: var(--ink);
      margin-bottom: 4px;
    }
    .value-text {
      font-size: 0.9rem; color: var(--text-muted); line-height: 1.7;
    }

    /* SERVICES */
    #services {
      padding: 120px 60px;
      background: var(--warm-white);
    }
    .services-header {
      display: grid; grid-template-columns: 1fr 1fr;
      align-items: end; gap: 40px; margin-bottom: 70px;
    }
    .services-header p {
      font-size: 1.05rem; line-height: 1.9;
      color: var(--text-muted); font-weight: 300;
      align-self: end;
    }
    .services-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 2px;
    }
    .service-card {
      padding: 48px 40px;
      background: var(--cream);
      border: 1px solid transparent;
      position: relative; overflow: hidden;
      transition: all 0.4s ease;
      cursor: none;
    }
    .service-card::before {
      content: '';
      position: absolute; top: 0; left: 0;
      width: 3px; height: 0;
      background: var(--terracotta);
      transition: height 0.4s ease;
    }
    .service-card:hover { background: var(--warm-white); transform: translateY(-4px); box-shadow: 0 20px 60px rgba(30,22,18,0.1); }
    .service-card:hover::before { height: 100%; }
    .service-num {
      font-family: 'Playfair Display', serif;
      font-size: 3rem; font-weight: 700;
      color: rgba(192,96,58,0.12);
      line-height: 1; margin-bottom: 24px;
    }
    .service-icon {
      width: 52px; height: 52px;
      background: rgba(192,96,58,0.1);
      border-radius: 50%;
      display: flex; align-items: center; justify-content: center;
      margin-bottom: 24px;
      color: var(--terracotta);
      transition: background 0.3s;
    }
    .service-card:hover .service-icon { background: var(--terracotta); color: #fff; }
    .service-name {
      font-family: 'Playfair Display', serif;
      font-size: 1.4rem; font-weight: 700;
      color: var(--ink); margin-bottom: 14px;
    }
    .service-desc {
      font-size: 0.95rem; line-height: 1.85;
      color: var(--text-muted); font-weight: 300;
      margin-bottom: 28px;
    }
    .service-link {
      font-family: 'Raleway', sans-serif;
      font-size: 0.72rem; font-weight: 600;
      letter-spacing: 0.15em; text-transform: uppercase;
      color: var(--terracotta); text-decoration: none;
      display: inline-flex; align-items: center; gap: 8px;
      transition: gap 0.3s;
    }
    .service-link:hover { gap: 14px; }

    /* FEATURED */
    .featured-strip {
      padding: 80px 0;
      background: var(--terracotta);
      overflow: hidden;
    }
    .strip-inner {
      display: flex; gap: 80px; align-items: center;
      animation: scrollStrip 20s linear infinite;
      white-space: nowrap;
    }
    @keyframes scrollStrip {
      from { transform: translateX(0); }
      to { transform: translateX(-50%); }
    }
    .strip-item {
      font-family: 'Playfair Display', serif;
      font-size: 1.4rem; font-style: italic;
      color: rgba(253,248,242,0.85);
      flex-shrink: 0;
    }
    .strip-dot {
      width: 6px; height: 6px;
      background: rgba(253,248,242,0.4);
      border-radius: 50%; flex-shrink: 0;
    }

    /* CONTACT */
    #contact {
      padding: 120px 60px;
      background: var(--ink);
      display: grid; grid-template-columns: 1fr 1fr;
      gap: 100px; align-items: start;
    }
    .contact-info .section-tag { color: var(--ochre); }
    .contact-info .section-tag::before { background: var(--ochre); }
    .contact-info .section-title { color: var(--cream); }
    .contact-info .section-title em { color: var(--terracotta); }
    .contact-tagline {
      font-size: 1.05rem; line-height: 1.9;
      color: rgba(245,237,224,0.6); font-weight: 300;
      margin: 24px 0 48px;
    }
    .contact-details { display: flex; flex-direction: column; gap: 28px; }
    .contact-item {
      display: flex; align-items: flex-start; gap: 20px;
    }
    .contact-item-icon {
      width: 44px; height: 44px; flex-shrink: 0;
      border: 1px solid rgba(245,237,224,0.15);
      display: flex; align-items: center; justify-content: center;
      color: var(--ochre);
    }
    .contact-item-label {
      font-family: 'Raleway', sans-serif;
      font-size: 0.68rem; font-weight: 600;
      letter-spacing: 0.15em; text-transform: uppercase;
      color: rgba(245,237,224,0.4); margin-bottom: 6px;
    }
    .contact-item-value {
      font-size: 1.05rem; color: var(--cream);
      font-weight: 300;
    }

    /* FORM */
    .contact-form { display: flex; flex-direction: column; gap: 20px; }
    .form-row { display: grid; grid-template-columns: 1fr 1fr; gap: 20px; }
    .form-group { display: flex; flex-direction: column; gap: 8px; }
    .form-group label {
      font-family: 'Raleway', sans-serif;
      font-size: 0.68rem; font-weight: 600;
      letter-spacing: 0.15em; text-transform: uppercase;
      color: rgba(245,237,224,0.5);
    }
    .form-group input,
    .form-group textarea,
    .form-group select {
      background: rgba(255,255,255,0.04);
      border: 1px solid rgba(245,237,224,0.12);
      color: var(--cream);
      padding: 14px 18px;
      font-family: 'Cormorant Garamond', serif;
      font-size: 1rem; font-weight: 300;
      outline: none;
      transition: border-color 0.3s;
      cursor: none;
    }
    .form-group input:focus,
    .form-group textarea:focus,
    .form-group select:focus { border-color: var(--terracotta); }
    .form-group textarea { min-height: 130px; resize: vertical; }
    .form-group select option { background: var(--ink); }
    .form-group input::placeholder,
    .form-group textarea::placeholder { color: rgba(245,237,224,0.25); }
    .btn-submit {
      padding: 18px 48px;
      background: var(--terracotta);
      color: #fff; border: none;
      font-family: 'Raleway', sans-serif;
      font-size: 0.78rem; font-weight: 600;
      letter-spacing: 0.15em; text-transform: uppercase;
      cursor: none; transition: all 0.3s;
      align-self: flex-start;
    }
    .btn-submit:hover { background: var(--ochre); transform: translateY(-2px); }

    /* FOOTER */
    footer {
      padding: 40px 60px;
      background: #120e0b;
      display: flex; align-items: center; justify-content: space-between;
      border-top: 1px solid rgba(255,255,255,0.05);
    }
    .footer-logo {
      font-family: 'Playfair Display', serif;
      font-size: 1.4rem; color: var(--cream);
      font-weight: 700;
    }
    .footer-logo span { color: var(--terracotta); font-style: italic; }
    .footer-copy {
      font-family: 'Raleway', sans-serif;
      font-size: 0.68rem; letter-spacing: 0.1em;
      color: rgba(245,237,224,0.3);
    }
    .footer-social { display: flex; gap: 16px; }
    .social-btn {
      width: 36px; height: 36px;
      border: 1px solid rgba(245,237,224,0.1);
      display: flex; align-items: center; justify-content: center;
      color: rgba(245,237,224,0.4);
      text-decoration: none;
      transition: all 0.3s; cursor: none;
    }
    .social-btn:hover { border-color: var(--terracotta); color: var(--terracotta); }

    /* SCROLL REVEAL */
    .reveal { opacity: 0; transform: translateY(40px); transition: all 0.8s cubic-bezier(0.16,1,0.3,1); }
    .reveal.visible { opacity: 1; transform: translateY(0); }

    /* MOBILE */
    @media (max-width: 900px) {
      nav { padding: 16px 24px; }
      .nav-links { gap: 20px; }
      #home { grid-template-columns: 1fr; }
      .hero-left { padding: 120px 24px 60px; }
      .hero-right { min-height: 300px; }
      #about { grid-template-columns: 1fr; padding: 80px 24px; gap: 50px; }
      #services { padding: 80px 24px; }
      .services-header { grid-template-columns: 1fr; }
      .services-grid { grid-template-columns: 1fr; }
      #contact { grid-template-columns: 1fr; padding: 80px 24px; gap: 60px; }
      footer { flex-direction: column; gap: 20px; padding: 30px 24px; text-align: center; }
      .form-row { grid-template-columns: 1fr; }
      body { cursor: auto; }
      .cursor, .cursor-follower { display: none; }
    }
  </style>
</head>
<body>

  <div class="cursor" id="cursor"></div>
  <div class="cursor-follower" id="cursorFollower"></div>

  <!-- NAV -->
  <nav id="navbar">
    <a href="#home" class="nav-logo">Kala<span>kar</span></a>
    <ul class="nav-links">
      <li><a href="#home">Home</a></li>
      <li><a href="#about">About</a></li>
      <li><a href="#services">Services</a></li>
      <li><a href="#contact">Contact</a></li>
    </ul>
  </nav>

  <!-- HERO -->
  <section id="home">
    <div class="hero-left">
      <div class="hero-tag reveal">Handmade with Heritage</div>
      <h1 class="hero-title reveal">
        Where <em>Ancient</em><br/>
        Craft Meets<br/>
        Modern Soul
      </h1>
      <p class="hero-desc reveal">
        We connect master artisans with the world — celebrating centuries-old traditions, one handcrafted piece at a time.
      </p>
      <div class="btn-group reveal">
        <a href="#services" class="btn-primary">Explore Crafts</a>
        <a href="#about" class="btn-ghost">
          Our Story
          <svg width="16" height="16" viewBox="0 0 16 16" fill="none" stroke="currentColor