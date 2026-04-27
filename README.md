<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Preparation of Phenols — Aryaz Omed Hawez</title>
<script src="https://cdn.tailwindcss.com"></script>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
<script>
tailwind.config = {
  theme: {
    extend: {
      fontFamily: {
        sans: ['Inter', 'sans-serif'],
        mono: ['JetBrains Mono', 'monospace'],
      },
      colors: {
        bg: '#050507',
        surface: '#0E1016',
        card: '#0A0A0A',
        brand: { blue: '#0091FF', gold: '#FFC800', cyan: '#00E5FF' },
        tiu: { purple: '#6B3FA0', gold: '#FFC800' }
      }
    }
  }
}
</script>
<style>
  * { margin: 0; padding: 0; box-sizing: border-box; }
  body { background: #050507; color: #fff; font-family: 'Inter', sans-serif; overflow: hidden; height: 100vh; }

  /* Slide System */
  .slide { position: absolute; inset: 0; display: flex; align-items: center; justify-content: center; opacity: 0; transform: translateX(60px); transition: all 0.6s cubic-bezier(0.16, 1, 0.3, 1); pointer-events: none; padding: 2rem; }
  .slide.active { opacity: 1; transform: translateX(0); pointer-events: auto; }
  .slide.exit-left { opacity: 0; transform: translateX(-60px); }

  /* Chemical formula styling */
  .chem { font-family: 'JetBrains Mono', monospace; color: #00E5FF; }
  .chem-gold { font-family: 'JetBrains Mono', monospace; color: #FFC800; }
  .sub { font-size: 0.75em; vertical-align: sub; }
  .sup { font-size: 0.75em; vertical-align: super; }

  /* Glow effects */
  .glow-blue { text-shadow: 0 0 30px rgba(0,145,255,0.3); }
  .glow-gold { text-shadow: 0 0 30px rgba(255,200,0,0.3); }
  .glow-cyan { text-shadow: 0 0 25px rgba(0,229,255,0.3); }

  /* Cards */
  .method-card {
    background: rgba(14,16,22,0.8);
    border: 1px solid rgba(255,255,255,0.08);
    border-radius: 1rem;
    padding: 1.5rem;
    backdrop-filter: blur(12px);
    transition: all 0.3s ease;
  }
  .method-card:hover {
    border-color: rgba(0,145,255,0.3);
    background: rgba(14,16,22,0.95);
    transform: translateY(-2px);
  }

  /* Reaction box */
  .reaction-box {
    background: rgba(0,229,255,0.04);
    border: 1px solid rgba(0,229,255,0.15);
    border-radius: 0.75rem;
    padding: 1.25rem 1.5rem;
    font-family: 'JetBrains Mono', monospace;
    font-size: 1.05rem;
    color: #CBD5E1;
    text-align: center;
    line-height: 2;
  }

  /* Step indicator */
  .step-num {
    width: 36px; height: 36px; border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    font-weight: 700; font-size: 0.875rem;
    flex-shrink: 0;
  }

  /* Progress bar */
  .progress-bar { transition: width 0.5s cubic-bezier(0.16, 1, 0.3, 1); }

  /* Benzene ring SVG */
  .benzene-ring { filter: drop-shadow(0 0 8px rgba(0,229,255,0.2)); }

  /* Bullet animations */
  .bullet-item { opacity: 0; transform: translateX(-15px); }
  .slide.active .bullet-item { opacity: 1; transform: translateX(0); transition: all 0.5s ease; }
  .slide.active .bullet-item:nth-child(1) { transition-delay: 0.2s; }
  .slide.active .bullet-item:nth-child(2) { transition-delay: 0.35s; }
  .slide.active .bullet-item:nth-child(3) { transition-delay: 0.5s; }
  .slide.active .bullet-item:nth-child(4) { transition-delay: 0.65s; }
  .slide.active .bullet-item:nth-child(5) { transition-delay: 0.8s; }

  /* Title animation */
  .slide.active .title-reveal { opacity: 1; transform: translateY(0); }
  .title-reveal { opacity: 0; transform: translateY(20px); transition: all 0.7s cubic-bezier(0.16, 1, 0.3, 1); }

  /* Navigation buttons */
  .nav-btn {
    width: 48px; height: 48px; border-radius: 50%;
    background: rgba(255,255,255,0.05);
    border: 1px solid rgba(255,255,255,0.1);
    color: #94A3B8;
    display: flex; align-items: center; justify-content: center;
    cursor: pointer; transition: all 0.25s ease;
  }
  .nav-btn:hover { background: rgba(0,145,255,0.15); border-color: rgba(0,145,255,0.3); color: #0091FF; }
  .nav-btn:active { transform: scale(0.92); }
  .nav-btn:disabled { opacity: 0.2; cursor: not-allowed; }
  .nav-btn:disabled:hover { background: rgba(255,255,255,0.05); border-color: rgba(255,255,255,0.1); color: #94A3B8; }

  /* Slide counter */
  .slide-counter { font-family: 'JetBrains Mono', monospace; font-variant-numeric: tabular-nums; }

  /* Warning box */
  .warning-box {
    background: rgba(255,60,60,0.06);
    border: 1px solid rgba(255,60,60,0.2);
    border-radius: 0.75rem;
    padding: 1.25rem 1.5rem;
  }

  /* Scrollbar hide */
  .no-scrollbar::-webkit-scrollbar { display: none; }
  .no-scrollbar { -ms-overflow-style: none; scrollbar-width: none; }

  /* Grid background */
  .grid-bg {
    background-image:
      linear-gradient(rgba(255,255,255,0.02) 1px, transparent 1px),
      linear-gradient(90deg, rgba(255,255,255,0.02) 1px, transparent 1px);
    background-size: 60px 60px;
  }

  /* Keyboard hint */
  .kbd {
    background: rgba(255,255,255,0.06);
    border: 1px solid rgba(255,255,255,0.1);
    border-radius: 4px;
    padding: 2px 6px;
    font-size: 0.7rem;
    font-family: 'JetBrains Mono', monospace;
  }

  /* Method number badge */
  .method-badge {
    width: 28px; height: 28px; border-radius: 8px;
    display: flex; align-items: center; justify-content: center;
    font-size: 0.75rem; font-weight: 700; flex-shrink: 0;
  }

  @keyframes float { 0%,100% { transform: translateY(0); } 50% { transform: translateY(-8px); } }
  .float-anim { animation: float 4s ease-in-out infinite; }

  @keyframes pulse-ring { 0% { transform: scale(0.8); opacity: 0.6; } 100% { transform: scale(1.4); opacity: 0; } }
  .pulse-ring { animation: pulse-ring 2.5s ease-out infinite; }
</style>
</head>
<body class="grid-bg">

<!-- Background Blobs -->
<div class="fixed inset-0 pointer-events-none overflow-hidden z-0">
  <div class="absolute top-[-20%] left-[-10%] w-[600px] h-[600px] rounded-full bg-brand-blue/5 blur-[120px]"></div>
  <div class="absolute bottom-[-15%] right-[-10%] w-[500px] h-[500px] rounded-full bg-brand-cyan/4 blur-[100px]"></div>
  <div class="absolute top-[40%] left-[50%] w-[400px] h-[400px] rounded-full bg-tiu-purple/3 blur-[100px]"></div>
</div>

<!-- Top Progress Bar -->
<div class="fixed top-0 left-0 right-0 h-[3px] z-50 bg-white/5">
  <div id="progressBar" class="progress-bar h-full bg-gradient-to-r from-brand-blue via-brand-cyan to-brand-gold" style="width: 8.33%"></div>
</div>

<!-- Header Bar -->
<header class="fixed top-0 left-0 right-0 z-40 flex items-center justify-between px-6 py-4" style="background: rgba(5,5,7,0.7); backdrop-filter: blur(12px);">
  <div class="flex items-center gap-3">
    <img src="https://z-cdn-media.chatglm.cn/files/4d9e4f88-49d8-4f47-9b17-93101df5e1ee.jpg?auth_key=1877297798-cbeed9fa3cd74009ab8c581173dc54c4-0-51d611f4f3dd401382fb169294b785b0" alt="TIU" class="w-9 h-9 rounded-full object-cover border border-white/10">
    <div>
      <p class="text-xs font-semibold text-white/90 tracking-wide">Preparation of Phenols</p>
      <p class="text-[10px] text-white/40">Tishk International University</p>
    </div>
  </div>
  <div class="flex items-center gap-4">
    <span class="slide-counter text-xs text-white/50">
      <span id="currentSlide" class="text-brand-blue font-semibold">01</span>
      <span class="mx-1">/</span>
      <span id="totalSlides">12</span>
    </span>
    <button onclick="toggleOverview()" class="nav-btn !w-8 !h-8" title="Slide Overview">
      <svg width="14" height="14" fill="none" stroke="currentColor" stroke-width="1.5" viewBox="0 0 24 24"><rect x="3" y="3" width="7" height="7" rx="1"/><rect x="14" y="3" width="7" height="7" rx="1"/><rect x="3" y="14" width="7" height="7" rx="1"/><rect x="14" y="14" width="7" height="7" rx="1"/></svg>
    </button>
  </div>
</header>

<!-- ==================== SLIDES ==================== -->
<main class="relative w-full h-full">

  <!-- SLIDE 1: Title -->
  <section class="slide active" data-slide="1">
    <div class="max-w-4xl mx-auto text-center">
      <div class="title-reveal">
        <div class="inline-flex items-center gap-2 px-4 py-1.5 rounded-full bg-white/5 border border-white/10 mb-8">
          <span class="w-2 h-2 rounded-full bg-brand-cyan"></span>
          <span class="text-xs font-medium text-white/60 tracking-wider uppercase">Organic Chemistry Presentation</span>
        </div>
      </div>
      <h1 class="title-reveal text-5xl md:text-7xl font-bold tracking-tighter leading-[0.95] mb-6" style="transition-delay:0.15s">
        <span class="bg-gradient-to-r from-brand-blue via-brand-cyan to-white bg-clip-text text-transparent">Preparation</span><br>
        <span class="text-white">of Phenols</span>
      </h1>
      <p class="title-reveal text-lg text-white/50 font-light max-w-xl mx-auto mb-10" style="transition-delay:0.3s">
        Methods, mechanisms, and industrial processes for synthesizing phenolic compounds
      </p>
      <div class="title-reveal flex flex-wrap items-center justify-center gap-6 text-sm text-white/40" style="transition-delay:0.45s">
        <div class="flex items-center gap-2">
          <svg width="16" height="16" fill="none" stroke="currentColor" stroke-width="1.5" viewBox="0 0 24 24"><path d="M15.75 6a3.75 3.75 0 11-7.5 0 3.75 3.75 0 017.5 0zM4.5 20.25a8.25 8.25 0 0115 0"/></svg>
          <span>Aryaz Omed Hawez</span>
        </div>
        <div class="flex items-center gap-2">
          <svg width="16" height="16" fill="none" stroke="currentColor" stroke-width="1.5" viewBox="0 0 24 24"><path d="M4.26 10.147a60.438 60.438 0 00-.491 6.347A48.62 48.62 0 0112 20.904a48.62 48.62 0 018.232-4.41 60.46 60.46 0 00-.491-6.347m-15.482 0a50.636 50.636 0 00-2.658-.813A59.906 59.906 0 0112 3.493a59.903 59.903 0 0110.399 5.84c-.896.248-1.783.52-2.658.814m-15.482 0A50.717 50.717 0 0112 13.489a50.702 50.702 0 017.74-3.342"/></svg>
          <span>Dr. Tara Fuad</span>
        </div>
        <div class="flex items-center gap-2">
          <svg width="16" height="16" fill="none" stroke="currentColor" stroke-width="1.5" viewBox="0 0 24 24"><path d="M15 10.5a3 3 0 11-6 0 3 3 0 016 0z"/><path d="M19.5 10.5c0 7.142-7.5 11.25-7.5 11.25S4.5 17.642 4.5 10.5a7.5 7.5 0 1115 0z"/></svg>
          <span>TIU Sulaimaniyah</span>
        </div>
      </div>
      <div class="title-reveal mt-12" style="transition-delay:0.6s">
        <button onclick="goToSlide(2)" class="inline-flex items-center gap-2 px-6 py-3 rounded-full bg-brand-blue text-white font-bold text-sm uppercase tracking-wide hover:-translate-y-1 transition-all duration-300" style="box-shadow: 0 0 30px rgba(0,145,255,0.3)">
          Start Presentation
          <svg width="16" height="16" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><path d="M13.5 4.5L21 12m0 0l-7.5 7.5M21 12H3"/></svg>
        </button>
      </div>
    </div>
  </section>

  <!-- SLIDE 2: Introduction -->
  <section class="slide" data-slide="2">
    <div class="max-w-4xl mx-auto w-full">
      <div class="flex items-center gap-3 mb-2 title-reveal">
        <span class="text-xs font-mono text-brand-blue/60 tracking-widest">01</span>
        <div class="w-12 h-[1px] bg-brand-blue/30"></div>
      </div>
      <h2 class="text-4xl md:text-5xl font-semibold tracking-tight mb-10 title-reveal">Introduction</h2>
      <div class="grid md:grid-cols-2 gap-8">
        <div class="title-reveal" style="transition-delay:0.15s">
          <p class="text-lg text-white/70 font-light leading-relaxed mb-6">
            Phenols are organic compounds in which a <span class="text-brand-cyan font-medium">hydroxyl group (–OH)</span> is directly attached to an aromatic benzene ring.
          </p>
          <div class="flex items-center gap-4 p-4 rounded-xl bg-white/[0.03] border border-white/[0.06]">
            <!-- Benzene + OH diagram -->
            <svg width="80" height="80" viewBox="0 0 80 80" class="benzene-ring flex-shrink-0">
              <polygon points="40,10 66,25 66,55 40,70 14,55 14,25" fill="none" stroke="#00E5FF" stroke-width="1.5"/>
              <circle cx="40" cy="40" r="16" fill="none" stroke="#00E5FF" stroke-width="1" stroke-dasharray="3 2"/>
              <line x1="66" y1="25" x2="78" y2="18" stroke="#FFC800" stroke-width="1.5"/>
              <text x="78" y="14" fill="#FFC800" font-size="10" font-family="JetBrains Mono" text-anchor="start">OH</text>
            </svg>
            <div>
              <p class="chem text-lg">C<span class="sub">6</span>H<span class="sub">5</span>OH</p>
              <p class="text-xs text-white/40 mt-1">Phenol — simplest phenolic compound</p>
            </div>
          </div>
        </div>
        <div class="title-reveal" style="transition-delay:0.3s">
          <p class="text-sm font-semibold text-white/50 uppercase tracking-wider mb-4">Key Applications</p>
          <div class="space-y-3">
            <div class="bullet-item flex items-start gap-3 p-3 rounded-lg bg-white/[0.02] border border-white/[0.05]">
              <div class="w-8 h-8 rounded-lg bg-brand-blue/10 flex items-center justify-center flex-shrink-0 mt-0.5">
                <svg width="16" height="16" fill="none" stroke="#0091FF" stroke-width="1.5" viewBox="0 0 24 24"><path d="M9.75 3.104v5.714a2.25 2.25 0 01-.659 1.591L5 14.5M9.75 3.104c-.251.023-.501.05-.75.082m.75-.082a24.301 24.301 0 014.5 0m0 0v5.714c0 .597.237 1.17.659 1.591L19.8 15.3M14.25 3.104c.251.023.501.05.75.082M19.8 15.3l-1.57.393A9.065 9.065 0 0112 15a9.065 9.065 0 00-6.23.693L5 14.5m14.8.8l1.402 1.402c1.232 1.232.65 3.318-1.067 3.611A48.309 48.309 0 0112 21c-2.773 0-5.491-.235-8.135-.687-1.718-.293-2.3-2.379-1.067-3.61L5 14.5"/></svg>
              </div>
              <div>
                <p class="text-sm font-medium text-white/90">Pharmaceuticals</p>
                <p class="text-xs text-white/40">Drug synthesis & medicinal chemistry</p>
              </div>
            </div>
            <div class="bullet-item flex items-start gap-3 p-3 rounded-lg bg-white/[0.02] border border-white/[0.05]">
              <div class="w-8 h-8 rounded-lg bg-brand-cyan/10 flex items-center justify-center flex-shrink-0 mt-0.5">
                <svg width="16" height="16" fill="none" stroke="#00E5FF" stroke-width="1.5" viewBox="0 0 24 24"><path d="M9.75 3.104v5.714a2.25 2.25 0 01-.659 1.591L5 14.5M9.75 3.104c-.251.023-.501.05-.75.082m.75-.082a24.301 24.301 0 014.5 0m0 0v5.714c0 .597.237 1.17.659 1.591L19.8 15.3M14.25 3.104c.251.023.501.05.75.082M19.8 15.3l-1.57.393A9.065 9.065 0 0112 15a9.065 9.065 0 00-6.23.693L5 14.5m14.8.8l1.402 1.402c1.232 1.232.65 3.318-1.067 3.611A48.309 48.309 0 0112 21c-2.773 0-5.491-.235-8.135-.687-1.718-.293-2.3-2.379-1.067-3.61L5 14.5"/></svg>
              </div>
              <div>
                <p class="text-sm font-medium text-white/90">Antiseptics & Disinfectants</p>
                <p class="text-xs text-white/40">Surface sterilization solutions</p>
              </div>
            </div>
            <div class="bullet-item flex items-start gap-3 p-3 rounded-lg bg-white/[0.02] border border-white/[0.05]">
              <div class="w-8 h-8 rounded-lg bg-brand-gold/10 flex items-center justify-center flex-shrink-0 mt-0.5">
                <svg width="16" height="16" fill="none" stroke="#FFC800" stroke-width="1.5" viewBox="0 0 24 24"><path d="M21 7.5l-2.25-1.313M21 7.5v2.25m0-2.25l-2.25 1.313M3 7.5l2.25-1.313M3 7.5l2.25 1.313M3 7.5v2.25m9 3l2.25-1.313M12 12.75l-2.25-1.313M12 12.75V15m0 6.75l2.25-1.313M12 21.75V19.5m0 2.25l-2.25-1.313m0-16.875L12 2.25l2.25 1.313M21 14.25v2.25l-2.25 1.313m-13.5 0L3 16.5v-2.25"/></svg>
              </div>
              <div>
                <p class="text-sm font-medium text-white/90">Plastics & Resins</p>
                <p class="text-xs text-white/40">Bakelite, epoxy resins, polycarbonates</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- SLIDE 3: Structure of Phenol -->
  <section class="slide" data-slide="3">
    <div class="max-w-4xl mx-auto w-full">
      <div class="flex items-center gap-3 mb-2 title-reveal">
        <span class="text-xs font-mono text-brand-blue/60 tracking-widest">02</span>
        <div class="w-12 h-[1px] bg-brand-blue/30"></div>
      </div>
      <h2 class="text-4xl md:text-5xl font-semibold tracking-tight mb-10 title-reveal">Structure of Phenol</h2>
      <div class="grid md:grid-cols-2 gap-8 items-center">
        <div class="flex justify-center title-reveal" style="transition-delay:0.15s">
          <!-- Large benzene ring diagram -->
          <div class="relative">
            <div class="absolute inset-0 rounded-full bg-brand-cyan/5 blur-[60px] pulse-ring"></div>
            <svg width="220" height="220" viewBox="0 0 220 220" class="benzene-ring relative z-10 float-anim">
              <!-- Benzene hexagon -->
              <polygon points="110,30 186,70 186,150 110,190 34,150 34,70" fill="rgba(0,229,255,0.03)" stroke="#00E5FF" stroke-width="2"/>
              <!-- Inner circle (delocalized electrons) -->
              <circle cx="110" cy="110" r="45" fill="none" stroke="#00E5FF" stroke-width="1.2" stroke-dasharray="6 4" opacity="0.6"/>
              <!-- OH group -->
              <line x1="186" y1="70" x2="210" y2="52" stroke="#FFC800" stroke-width="2.5"/>
              <circle cx="210" cy="52" r="3" fill="#FFC800"/>
              <text x="218" y="48" fill="#FFC800" font-size="16" font-family="JetBrains Mono" font-weight="600" text-anchor="start">O</text>
              <text x="218" y="65" fill="#FFC800" font-size="16" font-family="JetBrains Mono" font-weight="600" text-anchor="start">H</text>
              <!-- Carbon labels -->
              <text x="110" y="24" fill="rgba(255,255,255,0.3)" font-size="10" font-family="JetBrains Mono" text-anchor="middle">C</text>
              <text x="194" y="72" fill="rgba(255,255,255,0.3)" font-size="10" font-family="JetBrains Mono" text-anchor="start">C</text>
              <text x="194" y="156" fill="rgba(255,255,255,0.3)" font-size="10" font-family="JetBrains Mono" text-anchor="start">C</text>
              <text x="110" y="208" fill="rgba(255,255,255,0.3)" font-size="10" font-family="JetBrains Mono" text-anchor="middle">C</text>
              <text x="22" y="156" fill="rgba(255,255,255,0.3)" font-size="10" font-family="JetBrains Mono" text-anchor="end">C</text>
              <text x="22" y="72" fill="rgba(255,255,255,0.3)" font-size="10" font-family="JetBrains Mono" text-anchor="end">C</text>
              <!-- H labels on carbons -->
              <text x="100" y="10" fill="rgba(255,255,255,0.15)" font-size="9" font-family="JetBrains Mono" text-anchor="middle">H</text>
              <text x="202" y="60" fill="rgba(255,255,255,0.15)" font-size="9" font-family="JetBrains Mono" text-anchor="start">H</text>
              <text x="202" y="168" fill="rgba(255,255,255,0.15)" font-size="9" font-family="JetBrains Mono" text-anchor="start">H</text>
              <text x="110" y="222" fill="rgba(255,255,255,0.15)" font-size="9" font-family="JetBrains Mono" text-anchor="middle">H</text>
              <text x="14" y="168" fill="rgba(255,255,255,0.15)" font-size="9" font-family="JetBrains Mono" text-anchor="end">H</text>
              <text x="14" y="60" fill="rgba(255,255,255,0.15)" font-size="9" font-family="JetBrains Mono" text-anchor="end">H</text>
            </svg>
          </div>
        </div>
        <div class="space-y-5">
          <div class="bullet-item method-card" style="transition-delay:0.2s">
            <p class="text-sm font-semibold text-brand-cyan mb-1">Chemical Formula</p>
            <p class="chem text-xl">C<span class="sub">6</span>H<span class="sub">5</span>OH</p>
            <p class="text-xs text-white/40 mt-1">Molecular weight: 94.11 g/mol</p>
          </div>
          <div class="bullet-item method-card" style="transition-delay:0.35s">
            <p class="text-sm font-semibold text-brand-blue mb-1">Resonance Stabilization</p>
            <p class="text-sm text-white/60 leading-relaxed">The oxygen's lone pairs delocalize into the ring, creating multiple resonance structures that stabilize the molecule.</p>
          </div>
          <div class="bullet-item method-card" style="transition-delay:0.5s">
            <p class="text-sm font-semibold text-brand-gold mb-1">Electron Donation</p>
            <p class="text-sm text-white/60 leading-relaxed">The –OH group donates electron density into the benzene ring through resonance, making the ring <span class="text-brand-gold">electron-rich</span>.</p>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- SLIDE 4: Importance -->
  <section class="slide" data-slide="4">
    <div class="max-w-4xl mx-auto w-full">
      <div class="flex items-center gap-3 mb-2 title-reveal">
        <span class="text-xs font-mono text-brand-blue/60 tracking-widest">03</span>
        <div class="w-12 h-[1px] bg-brand-blue/30"></div>
      </div>
      <h2 class="text-4xl md:text-5xl font-semibold tracking-tight mb-10 title-reveal">Importance of Phenols</h2>
      <div class="grid grid-cols-2 md:grid-cols-4 gap-4">
        <div class="bullet-item method-card text-center group" style="transition-delay:0.15s">
          <div class="w-14 h-14 rounded-2xl bg-gradient-to-br from-brand-blue/20 to-brand-blue/5 flex items-center justify-center mx-auto mb-4 group-hover:scale-110 transition-transform duration-300">
            <svg width="28" height="28" fill="none" stroke="#0091FF" stroke-width="1.5" viewBox="0 0 24 24"><path d="M9.75 3.104v5.714a2.25 2.25 0 01-.659 1.591L5 14.5M9.75 3.104c-.251.023-.501.05-.75.082m.75-.082a24.301 24.301 0 014.5 0m0 0v5.714c0 .597.237 1.17.659 1.591L19.8 15.3M14.25 3.104c.251.023.501.05.75.082M19.8 15.3l-1.57.393A9.065 9.065 0 0112 15a9.065 9.065 0 00-6.23.693L5 14.5"/></svg>
          </div>
          <p class="text-sm font-semibold text-white/90 mb-1">Drugs</p>
          <p class="text-xs text-white/40">Aspirin, paracetamol, antiseptics</p>
        </div>
        <div class="bullet-item method-card text-center group" style="transition-delay:0.3s">
          <div class="w-14 h-14 rounded-2xl bg-gradient-to-br from-brand-cyan/20 to-brand-cyan/5 flex items-center justify-center mx-auto mb-4 group-hover:scale-110 transition-transform duration-300">
            <svg width="28" height="28" fill="none" stroke="#00E5FF" stroke-width="1.5" viewBox="0 0 24 24"><path d="M21 7.5l-2.25-1.313M21 7.5v2.25m0-2.25l-2.25 1.313M3 7.5l2.25-1.313M3 7.5l2.25 1.313M3 7.5v2.25m9 3l2.25-1.313M12 12.75l-2.25-1.313M12 12.75V15m0 6.75l2.25-1.313M12 21.75V19.5m0 2.25l-2.25-1.313m0-16.875L12 2.25l2.25 1.313M21 14.25v2.25l-2.25 1.313m-13.5 0L3 16.5v-2.25"/></svg>
          </div>
          <p class="text-sm font-semibold text-white/90 mb-1">Plastics</p>
          <p class="text-xs text-white/40">Bakelite, epoxy resins</p>
        </div>
        <div class="bullet-item method-card text-center group" style="transition-delay:0.45s">
          <div class="w-14 h-14 rounded-2xl bg-gradient-to-br from-brand-gold/20 to-brand-gold/5 flex items-center justify-center mx-auto mb-4 group-hover:scale-110 transition-transform duration-300">
            <svg width="28" height="28" fill="none" stroke="#FFC800" stroke-width="1.5" viewBox="0 0 24 24"><path d="M4.098 19.902a3.75 3.75 0 005.304 0l6.401-6.402M6.75 21A3.75 3.75 0 013 17.25V4.125C3 3.504 3.504 3 4.125 3h5.25c.621 0 1.125.504 1.125 1.125v4.072M6.75 21a3.75 3.75 0 003.75-3.75V8.197M6.75 21h13.125c.621 0 1.125-.504 1.125-1.125v-5.25c0-.621-.504-1.125-1.125-1.125h-4.072M10.5 8.197l2.88-2.88c.438-.439 1.15-.439 1.59 0l3.712 3.713c.44.44.44 1.152 0 1.59l-2.879 2.88M6.75 17.25h.008v.008H6.75v-.008z"/></svg>
          </div>
          <p class="text-sm font-semibold text-white/90 mb-1">Dyes</p>
          <p class="text-xs text-white/40">Textile & industrial dyes</p>
        </div>
        <div class="bullet-item method-card text-center group" style="transition-delay:0.6s">
          <div class="w-14 h-14 rounded-2xl bg-gradient-to-br from-red-500/20 to-red-500/5 flex items-center justify-center mx-auto mb-4 group-hover:scale-110 transition-transform duration-300">
            <svg width="28" height="28" fill="none" stroke="#EF4444" stroke-width="1.5" viewBox="0 0 24 24"><path d="M15.362 5.214A8.252 8.252 0 0112 21 8.25 8.25 0 016.038 7.048 8.287 8.287 0 009 9.6a8.983 8.983 0 013.361-6.867 8.21 8.21 0 003 2.48z"/><path d="M12 18a3.75 3.75 0 00.495-7.467 5.99 5.99 0 00-1.925 3.546 5.974 5.974 0 01-2.133-1A3.75 3.75 0 0012 18z"/></svg>
          </div>
          <p class="text-sm font-semibold text-white/90 mb-1">Explosives</p>
          <p class="text-xs text-white/40">Picric acid, TNT derivatives</p>
        </div>
      </div>
      <div class="bullet-item mt-8 p-5 rounded-xl bg-gradient-to-r from-brand-blue/5 to-brand-cyan/5 border border-brand-blue/10 title-reveal" style="transition-delay:0.75s">
        <p class="text-sm text-white/60 leading-relaxed">
          <span class="text-brand-cyan font-semibold">💡 Key Fact:</span> Phenol itself was the first antiseptic used in surgery by Joseph Lister in 1865, revolutionizing medical practice.
        </p>
      </div>
    </div>
  </section>

  <!-- SLIDE 5: Methods Overview -->
  <section class="slide" data-slide="5">
    <div class="max-w-4xl mx-auto w-full">
      <div class="flex items-center gap-3 mb-2 title-reveal">
        <span class="text-xs font-mono text-brand-blue/60 tracking-widest">04</span>
        <div class="w-12 h-[1px] bg-brand-blue/30"></div>
      </div>
      <h2 class="text-4xl md:text-5xl font-semibold tracking-tight mb-3 title-reveal">Methods of Preparation</h2>
      <p class="text-white/40 mb-10 title-reveal" style="transition-delay:0.1s">Four principal routes to synthesize phenols</p>
      <div class="grid md:grid-cols-2 gap-4">
        <div class="bullet-item method-card flex items-start gap-4 cursor-pointer group" style="transition-delay:0.15s" onclick="goToSlide(6)">
          <div class="method-badge bg-brand-blue/15 text-brand-blue">1</div>
          <div class="flex-1">
            <p class="font-semibold text-white/90 group-hover:text-brand-blue transition-colors">From Haloarenes</p>
            <p class="text-xs text-white/40 mt-1">Nucleophilic aromatic substitution with NaOH</p>
            <div class="flex items-center gap-1 mt-2 text-brand-blue/50 group-hover:text-brand-blue transition-colors">
              <span class="text-[10px] uppercase tracking-wider font-semibold">View details</span>
              <svg width="12" height="12" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><path d="M13.5 4.5L21 12m0 0l-7.5 7.5M21 12H3"/></svg>
            </div>
          </div>
        </div>
        <div class="bullet-item method-card flex items-start gap-4 cursor-pointer group" style="transition-delay:0.3s" onclick="goToSlide(7)">
          <div class="method-badge bg-brand-cyan/15 text-brand-cyan">2</div>
          <div class="flex-1">
            <p class="font-semibold text-white/90 group-hover:text-brand-cyan transition-colors">From Benzene Sulfonic Acid</p>
            <p class="text-xs text-white/40 mt-1">Sulfonation → fusion → acidification</p>
            <div class="flex items-center gap-1 mt-2 text-brand-cyan/50 group-hover:text-brand-cyan transition-colors">
              <span class="text-[10px] uppercase tracking-wider font-semibold">View details</span>
              <svg width="12" height="12" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><path d="M13.5 4.5L21 12m0 0l-7.5 7.5M21 12H3"/></svg>
            </div>
          </div>
        </div>
        <div class="bullet-item method-card flex items-start gap-4 cursor-pointer group" style="transition-delay:0.45s" onclick="goToSlide(8)">
          <div class="method-badge bg-brand-gold/15 text-brand-gold">3</div>
          <div class="flex-1">
            <p class="font-semibold text-white/90 group-hover:text-brand-gold transition-colors">From Diazonium Salts</p>
            <p class="text-xs text-white/40 mt-1">Mild hydrolysis of arenediazonium salts</p>
            <div class="flex items-center gap-1 mt-2 text-brand-gold/50 group-hover:text-brand-gold transition-colors">
              <span class="text-[10px] uppercase tracking-wider font-semibold">View details</span>
              <svg width="12" height="12" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><path d="M13.5 4.5L21 12m0 0l-7.5 7.5M21 12H3"/></svg>
            </div>
          </div>
        </div>
        <div class="bullet-item method-card flex items-start gap-4 cursor-pointer group" style="transition-delay:0.6s" onclick="goToSlide(9)">
          <div class="method-badge bg-tiu-purple/15 text-tiu-purple">4</div>
          <div class="flex-1">
            <p class="font-semibold text-white/90 group-hover:text-tiu-purple transition-colors">Cumene Process <span class="text-[10px] uppercase tracking-wider px-2 py-0.5 rounded bg-brand-gold/10 text-brand-gold font-bold ml-2">Industrial</span></p>
            <p class="text-xs text-white/40 mt-1">Most economical large-scale method</p>
            <div class="flex items-center gap-1 mt-2 text-tiu-purple/50 group-hover:text-tiu-purple transition-colors">
              <span class="text-[10px] uppercase tracking-wider font-semibold">View details</span>
              <svg width="12" height="12" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><path d="M13.5 4.5L21 12m0 0l-7.5 7.5M21 12H3"/></svg>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- SLIDE 6: From Haloarenes -->
  <section class="slide" data-slide="6">
    <div class="max-w-4xl mx-auto w-full">
      <div class="flex items-center gap-3 mb-2 title-reveal">
        <span class="text-xs font-mono text-brand-blue/60 tracking-widest">05</span>
        <div class="w-12 h-[1px] bg-brand-blue/30"></div>
        <span class="text-[10px] uppercase tracking-wider px-2 py-0.5 rounded bg-brand-blue/10 text-brand-blue font-bold">Method 1</span>
      </div>
      <h2 class="text-4xl md:text-5xl font-semibold tracking-tight mb-8 title-reveal">From Haloarenes</h2>
      <div class="grid md:grid-cols-5 gap-6">
        <div class="md:col-span-3 space-y-5">
          <div class="title-reveal" style="transition-delay:0.1s">
            <p class="text-sm text-white/50 mb-3">Reaction Equation</p>
            <div class="reaction-box">
              <span class="chem">C<span class="sub">6</span>H<span class="sub">5</span>Cl</span>
              <span class="text-white/30 mx-2">+</span>
              <span class="text-white/70">NaOH</span>
              <span class="text-white/20 mx-1">→</span>
              <span class="chem-gold">C<span class="sub">6</span>H<span class="sub">5</span>ONa</span>
              <span class="text-white/20 mx-1">→</span>
              <span class="text-white font-medium" style="color:#4ADE80">C<span class="sub">6</span>H<span class="sub">5</span>OH</span>
            </div>
          </div>
          <div class="title-reveal" style="transition-delay:0.25s">
            <p class="text-sm text-white/50 mb-3">Step-by-Step</p>
            <div class="space-y-3">
              <div class="bullet-item flex items-start gap-3">
                <div class="step-num bg-brand-blue/15 text-brand-blue text-xs">1</div>
                <div>
                  <p class="text-sm text-white/80">Chlorobenzene reacts with aqueous NaOH</p>
                  <p class="text-xs text-white/40 mt-0.5">Nucleophilic aromatic substitution</p>
                </div>
              </div>
              <div class="bullet-item flex items-start gap-3">
                <div class="step-num bg-brand-gold/15 text-brand-gold text-xs">2</div>
                <div>
                  <p class="text-sm text-white/80">Forms sodium phenoxide (C₆H₅ONa)</p>
                  <p class="text-xs text-white/40 mt-0.5">Intermediate product</p>
                </div>
              </div>
              <div class="bullet-item flex items-start gap-3">
                <div class="step-num bg-green-500/15 text-green-400 text-xs">3</div>
                <div>
                  <p class="text-sm text-white/80">Acidification yields phenol</p>
                  <p class="text-xs text-white/40 mt-0.5">H⁺ or dilute acid treatment</p>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="md:col-span-2">
          <div class="bullet-item method-card !border-brand-blue/20" style="transition-delay:0.3s">
            <p class="text-xs font-bold text-brand-blue uppercase tracking-wider mb-4">Conditions</p>
            <div class="space-y-4">
              <div>
                <div class="flex items-center justify-between mb-1">
                  <span class="text-xs text-white/50">Temperature</span>
                  <span class="chem text-xs">~300°C</span>
                </div>
                <div class="w-full h-1.5 rounded-full bg-white/5">
                  <div class="h-full rounded-full bg-brand-blue" style="width:85%"></div>
                </div>
              </div>
              <div>
                <div class="flex items-center justify-between mb-1">
                  <span class="text-xs text-white/50">Pressure</span>
                  <span class="text-xs text-brand-gold font-mono">High</span>
                </div>
                <div class="w-full h-1.5 rounded-full bg-white/5">
                  <div class="h-full rounded-full bg-brand-gold" style="width:90%"></div>
                </div>
              </div>
              <div>
                <div class="flex items-center justify-between mb-1">
                  <span class="text-xs text-white/50">Yield</span>
                  <span class="text-xs text-green-400 font-mono">Moderate</span>
                </div>
                <div class="w-full h-1.5 rounded-full bg-white/5">
                  <div class="h-full rounded-full bg-green-500" style="width:55%"></div>
                </div>
              </div>
            </div>
            <div class="mt-5 pt-4 border-t border-white/5">
              <p class="text-[11px] text-white/30 leading-relaxed">⚠ High temperature and pressure required due to the strength of the C–Cl bond in aryl halides.</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- SLIDE 7: From Benzene Sulfonic Acid -->
  <section class="slide" data-slide="7">
    <div class="max-w-4xl mx-auto w-full">
      <div class="flex items-center gap-3 mb-2 title-reveal">
        <span class="text-xs font-mono text-brand-blue/60 tracking-widest">06</span>
        <div class="w-12 h-[1px] bg-brand-blue/30"></div>
        <span class="text-[10px] uppercase tracking-wider px-2 py-0.5 rounded bg-brand-cyan/10 text-brand-cyan font-bold">Method 2</span>
      </div>
      <h2 class="text-4xl md:text-5xl font-semibold tracking-tight mb-8 title-reveal">From Benzene Sulfonic Acid</h2>
      <div class="grid md:grid-cols-2 gap-8">
        <div class="space-y-4">
          <!-- Step 1 -->
          <div class="bullet-item method-card" style="transition-delay:0.1s">
            <div class="flex items-center gap-3 mb-3">
              <div class="step-num bg-brand-cyan/15 text-brand-cyan text-xs">1</div>
              <p class="text-sm font-semibold text-brand-cyan">Sulfonation</p>
            </div>
            <div class="reaction-box !text-sm !py-3">
              <span class="chem">C<span class="sub">6</span>H<span class="sub">6</span></span>
              <span class="text-white/30 mx-2">+</span>
              <span class="text-white/70">H<span class="sub">2</span>SO<span class="sub">4</span></span>
              <span class="text-white/20 mx-1">→</span>
              <span class="chem-gold">C<span class="sub">6</span>H<span class="sub">5</span>SO<span class="sub">3</span>H</span>
            </div>
            <p class="text-xs text-white/40 mt-2">Benzene + conc. H₂SO₄ → Benzene sulfonic acid</p>
          </div>
          <!-- Step 2 -->
          <div class="bullet-item method-card" style="transition-delay:0.3s">
            <div class="flex items-center gap-3 mb-3">
              <div class="step-num bg-brand-gold/15 text-brand-gold text-xs">2</div>
              <p class="text-sm font-semibold text-brand-gold">Fusion with NaOH</p>
            </div>
            <div class="reaction-box !text-sm !py-3">
              <span class="chem-gold">C<span class="sub">6</span>H<span class="sub">5</span>SO<span class="sub">3</span>H</span>
              <span class="text-white/30 mx-2">+</span>
              <span class="text-white/70">2NaOH</span>
              <span class="text-white/20 mx-1">→</span>
              <span class="text-white font-medium" style="color:#4ADE80">C<span class="sub">6</span>H<span class="sub">5</span>ONa</span>
              <span class="text-white/30 mx-2">+</span>
              <span class="text-white/50">Na<span class="sub">2</span>SO<span class="sub">3</span></span>
              <span class="text-white/30 mx-2">+</span>
              <span class="text-white/50">H<span class="sub">2</span>O</span>
            </div>
            <p class="text-xs text-white/40 mt-2">Molten NaOH at high temperature (~300°C)</p>
          </div>
          <!-- Step 3 -->
          <div class="bullet-item method-card" style="transition-delay:0.5s">
            <div class="flex items-center gap-3 mb-3">
              <div class="step-num bg-green-500/15 text-green-400 text-xs">3</div>
              <p class="text-sm font-semibold text-green-400">Acidification</p>
            </div>
            <div class="reaction-box !text-sm !py-3 !border-green-500/15 !bg-green-500/[0.03]">
              <span class="text-white font-medium" style="color:#4ADE80">C<span class="sub">6</span>H<span class="sub">5</span>ONa</span>
              <span class="text-white/30 mx-2">+</span>
              <span class="text-white/70">H⁺</span>
              <span class="text-white/20 mx-1">→</span>
              <span class="text-white font-bold" style="color:#4ADE80">C<span class="sub">6</span>H<span class="sub">5</span>OH</span>
              <span class="text-white/30 mx-2">+</span>
              <span class="text-white/50">Na⁺</span>
            </div>
          </div>
        </div>
        <div class="bullet-item flex flex-col justify-center" style="transition-delay:0.4s">
          <div class="method-card !border-brand-cyan/15">
            <p class="text-sm font-semibold text-white/80 mb-4">Process Flow</p>
            <div class="flex flex-col items-center gap-2">
              <div class="w-full text-center py-2 px-4 rounded-lg bg-brand-cyan/10 border border-brand-cyan/15">
                <p class="chem text-xs">C₆H₆</p>
                <p class="text-[10px] text-white/40">Benzene</p>
              </div>
              <svg width="16" height="16" fill="none" stroke="rgba(255,255,255,0.2)" stroke-width="1.5" viewBox="0 0 24 24"><path d="M19.5 13.5L12 21m0 0l-7.5-7.5M12 21V3"/></svg>
              <div class="w-full text-center py-2 px-4 rounded-lg bg-brand-gold/10 border border-brand-gold/15">
                <p class="chem-gold text-xs">C₆H₅SO₃H</p>
                <p class="text-[10px] text-white/40">Sulfonic acid</p>
              </div>
              <svg width="16" height="16" fill="none" stroke="rgba(255,255,255,0.2)" stroke-width="1.5" viewBox="0 0 24 24"><path d="M19.5 13.5L12 21m0 0l-7.5-7.5M12 21V3"/></svg>
              <div class="w-full text-center py-2 px-4 rounded-lg bg-green-500/10 border border-green-500/15">
                <p class="text-xs font-mono" style="color:#4ADE80">C₆H₅ONa</p>
                <p class="text-[10px] text-white/40">Sodium phenoxide</p>
              </div>
              <svg width="16" height="16" fill="none" stroke="rgba(255,255,255,0.2)" stroke-width="1.5" viewBox="0 0 24 24"><path d="M19.5 13.5L12 21m0 0l-7.5-7.5M12 21V3"/></svg>
              <div class="w-full text-center py-2 px-4 rounded-lg bg-green-500/15 border border-green-500/25">
                <p class="text-xs font-mono font-bold" style="color:#4ADE80">C₆H₅OH</p>
                <p class="text-[10px] text-white/50">Phenol ✓</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- SLIDE 8: From Diazonium Salts -->
  <section class="slide" data-slide="8">
    <div class="max-w-4xl mx-auto w-full">
      <div class="flex items-center gap-3 mb-2 title-reveal">
        <span class="text-xs font-mono text-brand-blue/60 tracking-widest">07</span>
        <div class="w-12 h-[1px] bg-brand-blue/30"></div>
        <span class="text-[10px] uppercase tracking-wider px-2 py-0.5 rounded bg-brand-gold/10 text-brand-gold font-bold">Method 3</span>
      </div>
      <h2 class="text-4xl md:text-5xl font-semibold tracking-tight mb-8 title-reveal">From Diazonium Salts</h2>
      <div class="grid md:grid-cols-5 gap-6">
        <div class="md:col-span-3 space-y-5">
          <div class="title-reveal" style="transition-delay:0.1s">
            <p class="text-sm text-white/50 mb-3">Reaction Equation</p>
            <div class="reaction-box !border-brand-gold/15 !bg-brand-gold/[0.03]">
              <span class="chem">C<span class="sub">6</span>H<span class="sub">5</span>N<span class="sub">2</span><span class="sup">+</span>Cl<span class="sup">−</span></span>
              <span class="text-white/30 mx-2">+</span>
              <span class="text-white/70">H<span class="sub">2</span>O</span>
              <span class="text-white/20 mx-1">→</span>
              <span class="text-white font-bold" style="color:#4ADE80">C<span class="sub">6</span>H<span class="sub">5</span>OH</span>
              <span class="text-white/30 mx-2">+</span>
              <span class="text-white/50">N<span class="sub">2</span><span class="sup">↑</span></span>
              <span class="text-white/30 mx-2">+</span>
              <span class="text-white/50">HCl</span>
            </div>
          </div>
          <div class="title-reveal" style="transition-delay:0.25s">
            <p class="text-sm text-white/50 mb-3">Mechanism Steps</p>
            <div class="space-y-3">
              <div class="bullet-item flex items-start gap-3">
                <div class="step-num bg-brand-gold/15 text-brand-gold text-xs">1</div>
                <div>
                  <p class="text-sm text-white/80">Aniline → Diazonium salt</p>
                  <p class="text-xs text-white/40 mt-0.5">Treatment with NaNO₂ + HCl at 0–5°C</p>
                </div>
              </div>
              <div class="bullet-item flex items-start gap-3">
                <div class="step-num bg-brand-blue/15 text-brand-blue text-xs">2</div>
                <div>
                  <p class="text-sm text-white/80">Diazonium salt + warm water</p>
                  <p class="text-xs text-white/40 mt-0.5">Hydrolysis releases N₂ gas</p>
                </div>
              </div>
              <div class="bullet-item flex items-start gap-3">
                <div class="step-num bg-green-500/15 text-green-400 text-xs">3</div>
                <div>
                  <p class="text-sm text-white/80">Phenol is obtained</p>
                  <p class="text-xs text-white/40 mt-0.5">N₂ evolution drives the reaction forward</p>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="md:col-span-2">
          <div class="bullet-item method-card !border-green-500/15" style="transition-delay:0.3s">
            <div class="flex items-center gap-2 mb-4">
              <svg width="18" height="18" fill="none" stroke="#4ADE80" stroke-width="1.5" viewBox="0 0 24 24"><path d="M9 12.75L11.25 15 15 9.75M21 12c0 1.268-.63 2.39-1.593 3.068a3.745 3.745 0 01-1.043 3.296 3.745 3.745 0 01-3.296 1.043A3.745 3.745 0 0112 21c-1.268 0-2.39-.63-3.068-1.593a3.746 3.746 0 01-3.296-1.043 3.745 3.745 0 01-1.043-3.296A3.745 3.745 0 013 12c0-1.268.63-2.39 1.593-3.068a3.745 3.745 0 011.043-3.296 3.746 3.746 0 013.296-1.043A3.746 3.746 0 0112 3c1.268 0 2.39.63 3.068 1.593a3.746 3.746 0 013.296 1.043 3.746 3.746 0 011.043 3.296A3.745 3.745 0 0121 12z"/></svg>
              <p class="text-sm font-semibold text-green-400">Advantage</p>
            </div>
            <p class="text-sm text-white/60 leading-relaxed mb-4">
              This method occurs under <span class="text-green-400 font-medium">mild conditions</span> — low temperature and atmospheric pressure.
            </p>
            <div class="space-y-2 text-xs">
              <div class="flex items-center gap-2 text-white/40">
                <span class="w-1 h-1 rounded-full bg-green-400"></span>
                No extreme pressure needed
              </div>
              <div class="flex items-center gap-2 text-white/40">
                <span class="w-1 h-1 rounded-full bg-green-400"></span>
                Good for laboratory scale
              </div>
              <div class="flex items-center gap-2 text-white/40">
                <span class="w-1 h-1 rounded-full bg-green-400"></span>
                High purity product
              </div>
              <div class="flex items-center gap-2 text-white/40">
                <span class="w-1 h-1 rounded-full bg-green-400"></span>
                N₂ gas drives reaction to completion
              </div>
            </div>
          </div>
          <div class="bullet-item mt-4 method-card" style="transition-delay:0.45s">
            <p class="text-xs font-bold text-white/40 uppercase tracking-wider mb-2">Note</p>
            <p class="text-xs text-white/40 leading-relaxed">This is the <span class="text-white/60 font-medium">best laboratory method</span> for preparing phenol from aniline.</p>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- SLIDE 9: Cumene Process -->
  <section class="slide" data-slide="9">
    <div class="max-w-4xl mx-auto w-full">
      <div class="flex items-center gap-3 mb-2 title-reveal">
        <span class="text-xs font-mono text-brand-blue/60 tracking-widest">08</span>
        <div class="w-12 h-[1px] bg-brand-blue/30"></div>
        <span class="text-[10px] uppercase tracking-wider px-2 py-0.5 rounded bg-brand-gold/15 text-brand-gold font-bold">Method 4 · Industrial</span>
      </div>
      <h2 class="text-4xl md:text-5xl font-semibold tracking-tight mb-3 title-reveal">Cumene Process</h2>
      <p class="text-white/40 text-sm mb-8 title-reveal" style="transition-delay:0.1s">The most important industrial method for phenol production</p>

      <div class="space-y-4">
        <!-- Step 1: Friedel-Crafts -->
        <div class="bullet-item method-card !border-brand-blue/20" style="transition-delay:0.15s">
          <div class="flex items-start gap-4">
            <div class="step-num bg-brand-blue text-white text-xs">1</div>
            <div class="flex-1">
              <div class="flex items-center gap-2 mb-2">
                <p class="text-sm font-semibold text-brand-blue">Friedel-Crafts Alkylation</p>
                <span class="text-[10px] px-2 py-0.5 rounded bg-white/5 text-white/30 font-mono">AlCl₃ catalyst</span>
              </div>
              <div class="reaction-box !text-sm !py-2.5 !text-left !bg-brand-blue/[0.03] !border-brand-blue/10">
                <span class="chem">C<span class="sub">6</span>H<span class="sub">6</span></span>
                <span class="text-white/30 mx-2">+</span>
                <span class="text-white/70">CH<span class="sub">2</span>=CH–CH<span class="sub">3</span></span>
                <span class="text-white/20 mx-2">→</span>
                <span class="chem-gold">C₆H₅–CH(CH₃)₂</span>
                <span class="text-white/20 mx-2">·</span>
                <span class="text-white/30 text-xs">(Cumene / Isopropylbenzene)</span>
              </div>
            </div>
          </div>
        </div>

        <!-- Step 2: Oxidation -->
        <div class="bullet-item method-card !border-brand-gold/20" style="transition-delay:0.3s">
          <div class="flex items-start gap-4">
            <div class="step-num bg-brand-gold text-black text-xs">2</div>
            <div class="flex-1">
              <div class="flex items-center gap-2 mb-2">
                <p class="text-sm font-semibold text-brand-gold">Oxidation</p>
                <span class="text-[10px] px-2 py-0.5 rounded bg-white/5 text-white/30 font-mono">O₂, no catalyst</span>
              </div>
              <div class="reaction-box !text-sm !py-2.5 !text-left !bg-brand-gold/[0.03] !border-brand-gold/10">
                <span class="chem-gold">Cumene</span>
                <span class="text-white/30 mx-2">+</span>
                <span class="text-white/70">O<span class="sub">2</span></span>
                <span class="text-white/20 mx-2">→</span>
                <span class="text-white font-medium" style="color:#F97316">Cumene hydroperoxide</span>
                <span class="text-white/20 mx-2">(CHP)</span>
              </div>
            </div>
          </div>
        </div>

        <!-- Step 3: Decomposition -->
        <div class="bullet-item method-card !border-green-500/20" style="transition-delay:0.45s">
          <div class="flex items-start gap-4">
            <div class="step-num bg-green-500 text-white text-xs">3</div>
            <div class="flex-1">
              <div class="flex items-center gap-2 mb-2">
                <p class="text-sm font-semibold text-green-400">Acid-Catalyzed Rearrangement</p>
                <span class="text-[10px] px-2 py-0.5 rounded bg-white/5 text-white/30 font-mono">H₂SO₄, dilute</span>
              </div>
              <div class="reaction-box !text-sm !py-2.5 !text-left !border-green-500/10 !bg-green-500/[0.03]">
                <span class="text-white font-medium" style="color:#F97316">CHP</span>
                <span class="text-white/20 mx-2">→</span>
                <span class="text-white font-bold" style="color:#4ADE80">C₆H₅OH</span>
                <span class="text-white/30 mx-2">+</span>
                <span class="text-white font-medium" style="color:#C084FC">(CH₃)₂CO</span>
                <span class="text-white/20 mx-2">·</span>
                <span class="text-white/30 text-xs">(Phenol + Acetone)</span>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- Bottom highlight -->
      <div class="bullet-item mt-6 flex flex-wrap gap-3 title-reveal" style="transition-delay:0.6s">
        <div class="flex items-center gap-2 px-3 py-1.5 rounded-full bg-brand-gold/10 border border-brand-gold/15">
          <span class="w-1.5 h-1.5 rounded-full bg-brand-gold"></span>
          <span class="text-xs text-brand-gold font-medium">Economical</span>
        </div>
        <div class="flex items-center gap-2 px-3 py-1.5 rounded-full bg-brand-blue/10 border border-brand-blue/15">
          <span class="w-1.5 h-1.5 rounded-full bg-brand-blue"></span>
          <span class="text-xs text-brand-blue font-medium">Large-scale</span>
        </div>
        <div class="flex items-center gap-2 px-3 py-1.5 rounded-full bg-purple-500/10 border border-purple-500/15">
          <span class="w-1.5 h-1.5 rounded-full bg-purple-400"></span>
          <span class="text-xs text-purple-400 font-medium">Co-produces Acetone</span>
        </div>
      </div>
    </div>
  </section>

  <!-- SLIDE 10: Properties -->
  <section class="slide" data-slide="10">
    <div class="max-w-4xl mx-auto w-full">
      <div class="flex items-center gap-3 mb-2 title-reveal">
        <span class="text-xs font-mono text-brand-blue/60 tracking-widest">09</span>
        <div class="w-12 h-[1px] bg-brand-blue/30"></div>
      </div>
      <h2 class="text-4xl md:text-5xl font-semibold tracking-tight mb-10 title-reveal">Properties of Phenol</h2>
      <div class="grid md:grid-cols-2 gap-6">
        <!-- Physical -->
        <div class="bullet-item method-card" style="transition-delay:0.15s">
          <div class="flex items-center gap-2 mb-5">
            <div class="w-8 h-8 rounded-lg bg-brand-blue/10 flex items-center justify-center">
              <svg width="16" height="16" fill="none" stroke="#0091FF" stroke-width="1.5" viewBox="0 0 24 24"><path d="M9.75 3.104v5.714a2.25 2.25 0 01-.659 1.591L5 14.5M9.75 3.104c-.251.023-.501.05-.75.082m.75-.082a24.301 24.301 0 014.5 0m0 0v5.714c0 .597.237 1.17.659 1.591L19.8 15.3M14.25 3.104c.251.023.501.05.75.082M19.8 15.3l-1.57.393A9.065 9.065 0 0112 15a9.065 9.065 0 00-6.23.693L5 14.5"/></svg>
            </div>
            <p class="text-sm font-bold text-brand-blue uppercase tracking-wider">Physical Properties</p>
          </div>
          <div class="space-y-3">
            <div class="flex items-start gap-3">
              <span class="w-1.5 h-1.5 rounded-full bg-brand-blue/50 mt-2 flex-shrink-0"></span>
              <p class="text-sm text-white/70">Colorless crystalline solid (turns pink on oxidation)</p>
            </div>
            <div class="flex items-start gap-3">
              <span class="w-1.5 h-1.5 rounded-full bg-brand-blue/50 mt-2 flex-shrink-0"></span>
              <p class="text-sm text-white/70">Melting point: <span class="chem text-xs">40.5°C</span></p>
            </div>
            <div class="flex items-start gap-3">
              <span class="w-1.5 h-1.5 rounded-full bg-brand-blue/50 mt-2 flex-shrink-0"></span>
              <p class="text-sm text-white/70">Boiling point: <span class="chem text-xs">181.7°C</span></p>
            </div>
            <div class="flex items-start gap-3">
              <span class="w-1.5 h-1.5 rounded-full bg-brand-blue/50 mt-2 flex-shrink-0"></span>
              <p class="text-sm text-white/70">Slightly soluble in water (8.3 g / 100 mL)</p>
            </div>
            <div class="flex items-start gap-3">
              <span class="w-1.5 h-1.5 rounded-full bg-brand-blue/50 mt-2 flex-shrink-0"></span>
              <p class="text-sm text-white/70">Characteristic medicinal odor</p>
            </div>
          </div>
        </div>
        <!-- Chemical -->
        <div class="bullet-item method-card" style="transition-delay:0.3s">
          <div class="flex items-center gap-2 mb-5">
            <div class="w-8 h-8 rounded-lg bg-brand-gold/10 flex items-center justify-center">
              <svg width="16" height="16" fill="none" stroke="#FFC800" stroke-width="1.5" viewBox="0 0 24 24"><path d="M9.75 3.104v5.714a2.25 2.25 0 01-.659 1.591L5 14.5M9.75 3.104c-.251.023-.501.05-.75.082m.75-.082a24.301 24.301 0 014.5 0m0 0v5.714c0 .597.237 1.17.659 1.591L19.8 15.3M14.25 3.104c.251.023.501.05.75.082M19.8 15.3l-1.57.393A9.065 9.065 0 0112 15a9.065 9.065 0 00-6.23.693L5 14.5"/></svg>
            </div>
            <p class="text-sm font-bold text-brand-gold uppercase tracking-wider">Chemical Properties</p>
          </div>
          <div class="space-y-3">
            <div class="flex items-start gap-3">
              <span class="w-1.5 h-1.5 rounded-full bg-brand-gold/50 mt-2 flex-shrink-0"></span>
              <p class="text-sm text-white/70"><span class="text-brand-gold font-medium">Weakly acidic</span> — pKa ≈ 10 (stronger than alcohols)</p>
            </div>
            <div class="flex items-start gap-3">
              <span class="w-1.5 h-1.5 rounded-full bg-brand-gold/50 mt-2 flex-shrink-0"></span>
              <p class="text-sm text-white/70">Reacts with NaOH to form phenoxide</p>
            </div>
            <div class="flex items-start gap-3">
              <span class="w-1.5 h-1.5 rounded-full bg-brand-gold/50 mt-2 flex-shrink-0"></span>
              <p class="text-sm text-white/70"><span class="text-brand-gold font-medium">Electrophilic substitution</span> — activated ring</p>
            </div>
            <div class="flex items-start gap-3">
              <span class="w-1.5 h-1.5 rounded-full bg-brand-gold/50 mt-2 flex-shrink-0"></span>
              <p class="text-sm text-white/70">Ortho/para directing (–OH activation)</p>
            </div>
            <div class="flex items-start gap-3">
              <span class="w-1.5 h-1.5 rounded-full bg-brand-gold/50 mt-2 flex-shrink-0"></span>
              <p class="text-sm text-white/70">Undergoes esterification, ether formation</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- SLIDE 11: Safety -->
  <section class="slide" data-slide="11">
    <div class="max-w-4xl mx-auto w-full">
      <div class="flex items-center gap-3 mb-2 title-reveal">
        <span class="text-xs font-mono text-brand-blue/60 tracking-widest">10</span>
        <div class="w-12 h-[1px] bg-brand-blue/30"></div>
      </div>
      <h2 class="text-4xl md:text-5xl font-semibold tracking-tight mb-10 title-reveal">Safety & Handling</h2>
      <div class="grid md:grid-cols-3 gap-4 mb-6">
        <div class="bullet-item warning-box text-center" style="transition-delay:0.1s">
          <div class="w-12 h-12 rounded-2xl bg-red-500/10 flex items-center justify-center mx-auto mb-3">
            <svg width="24" height="24" fill="none" stroke="#EF4444" stroke-width="1.5" viewBox="0 0 24 24"><path d="M12 9v3.75m-9.303 3.376c-.866 1.5.217 3.374 1.948 3.374h14.71c1.73 0 2.813-1.874 1.948-3.374L13.949 3.378c-.866-1.5-3.032-1.5-3.898 0L2.697 16.126zM12 15.75h.007v.008H12v-.008z"/></svg>
          </div>
          <p class="text-sm font-semibold text-red-400 mb-1">Toxic</p>
          <p class="text-xs text-white/40">Can be fatal if swallowed, inhaled, or absorbed through skin</p>
        </div>
        <div class="bullet-item warning-box text-center" style="transition-delay:0.25s">
          <div class="w-12 h-12 rounded-2xl bg-orange-500/10 flex items-center justify-center mx-auto mb-3">
            <svg width="24" height="24" fill="none" stroke="#F97316" stroke-width="1.5" viewBox="0 0 24 24"><path d="M15.362 5.214A8.252 8.252 0 0112 21 8.25 8.25 0 016.038 7.048 8.287 8.287 0 009 9.6a8.983 8.983 0 013.361-6.867 8.21 8.21 0 003 2.48z"/></svg>
          </div>
          <p class="text-sm font-semibold text-orange-400 mb-1">Corrosive</p>
          <p class="text-xs text-white/40">Causes severe skin burns and eye damage</p>
        </div>
        <div class="bullet-item warning-box text-center" style="transition-delay:0.4s">
          <div class="w-12 h-12 rounded-2xl bg-yellow-500/10 flex items-center justify-center mx-auto mb-3">
            <svg width="24" height="24" fill="none" stroke="#EAB308" stroke-width="1.5" viewBox="0 0 24 24"><path d="M12 3v2.25m6.364.386l-1.591 1.591M21 12h-2.25m-.386 6.364l-1.591-1.591M12 18.75V21m-4.773-4.227l-1.591 1.591M5.25 12H3m4.227-4.773L5.636 5.636M15.75 12a3.75 3.75 0 11-7.5 0 3.75 3.75 0 017.5 0z"/></svg>
          </div>
          <p class="text-sm font-semibold text-yellow-400 mb-1">Light Sensitive</p>
          <p class="text-xs text-white/40">Oxidizes to pink/red in air and light</p>
        </div>
      </div>
      <div class="bullet-item method-card !border-red-500/15" style="transition-delay:0.5s">
        <p class="text-sm font-bold text-white/60 uppercase tracking-wider mb-4">Required Precautions</p>
        <div class="grid grid-cols-2 gap-3">
          <div class="flex items-center gap-2 text-sm text-white/60">
            <svg width="16" height="16" fill="none" stroke="#4ADE80" stroke-width="2" viewBox="0 0 24 24"><path d="M4.5 12.75l6 6 9-13.5"/></svg>
            Wear nitrile gloves
          </div>
          <div class="flex items-center gap-2 text-sm text-white/60">
            <svg width="16" height="16" fill="none" stroke="#4ADE80" stroke-width="2" viewBox="0 0 24 24"><path d="M4.5 12.75l6 6 9-13.5"/></svg>
            Safety goggles
          </div>
          <div class="flex items-center gap-2 text-sm text-white/60">
            <svg width="16" height="16" fill="none" stroke="#4ADE80" stroke-width="2" viewBox="0 0 24 24"><path d="M4.5 12.75l6 6 9-13.5"/></svg>
            Lab coat / apron
          </div>
          <div class="flex items-center gap-2 text-sm text-white/60">
            <svg width="16" height="16" fill="none" stroke="#4ADE80" stroke-width="2" viewBox="0 0 24 24"><path d="M4.5 12.75l6 6 9-13.5"/></svg>
            Fume hood use
          </div>
          <div class="flex items-center gap-2 text-sm text-white/60">
            <svg width="16" height="16" fill="none" stroke="#4ADE80" stroke-width="2" viewBox="0 0 24 24"><path d="M4.5 12.75l6 6 9-13.5"/></svg>
            Avoid skin contact
          </div>
          <div class="flex items-center gap-2 text-sm text-white/60">
            <svg width="16" height="16" fill="none" stroke="#4ADE80" stroke-width="2" viewBox="0 0 24 24"><path d="M4.5 12.75l6 6 9-13.5"/></svg>
            Store in amber bottle
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- SLIDE 12: Conclusion -->
  <section class="slide" data-slide="12">
    <div class="max-w-4xl mx-auto w-full text-center">
      <div class="title-reveal mb-6">
        <div class="inline-flex items-center gap-2 px-4 py-1.5 rounded-full bg-brand-gold/10 border border-brand-gold/15 mb-8">
          <span class="w-2 h-2 rounded-full bg-brand-gold"></span>
          <span class="text-xs font-medium text-brand-gold/80 tracking-wider uppercase">Summary</span>
        </div>
      </div>
      <h2 class="text-4xl md:text-6xl font-bold tracking-tighter mb-8 title-reveal" style="transition-delay:0.1s">
        <span class="bg-gradient-to-r from-brand-blue via-brand-cyan to-brand-gold bg-clip-text text-transparent">Key Takeaways</span>
      </h2>
      <div class="grid md:grid-cols-2 gap-4 text-left mb-10">
        <div class="bullet-item method-card" style="transition-delay:0.2s">
          <p class="text-sm text-white/70 leading-relaxed">Phenols are <span class="text-brand-cyan font-medium">essential aromatic compounds</span> with the –OH group bonded directly to the benzene ring.</p>
        </div>
        <div class="bullet-item method-card" style="transition-delay:0.35s">
          <p class="text-sm text-white/70 leading-relaxed">Four main preparation methods: <span class="text-brand-blue font-medium">Haloarenes</span>, <span class="text-brand-cyan font-medium">Sulfonic acid</span>, <span class="text-brand-gold font-medium">Diazonium salts</span>, and <span class="text-purple-400 font-medium">Cumene process</span>.</p>
        </div>
        <div class="bullet-item method-card" style="transition-delay:0.5s">
          <p class="text-sm text-white/70 leading-relaxed">The <span class="text-purple-400 font-medium">Cumene process</span> is the most economical method for industrial-scale production, co-producing acetone.</p>
        </div>
        <div class="bullet-item method-card" style="transition-delay:0.65s">
          <p class="text-sm text-white/70 leading-relaxed">Phenols are widely used in <span class="text-brand-gold font-medium">medicine, plastics, dyes</span>, and antiseptics — making their synthesis critically important.</p>
        </div>
      </div>
      <div class="title-reveal" style="transition-delay:0.8s">
        <p class="text-lg text-white/30 font-light italic">"Understanding preparation methods is the bridge between laboratory chemistry and industrial production."</p>
        <p class="text-xs text-white/20 mt-4">— Dr. Tara Fuad, TIU Sulaimaniyah</p>
      </div>
    </div>
  </section>

  <!-- SLIDE 13: References -->
  <section class="slide" data-slide="13">
    <div class="max-w-3xl mx-auto w-full">
      <div class="flex items-center gap-3 mb-2 title-reveal">
        <span class="text-xs font-mono text-brand-blue/60 tracking-widest">11</span>
        <div class="w-12 h-[1px] bg-brand-blue/30"></div>
      </div>
      <h2 class="text-4xl md:text-5xl font-semibold tracking-tight mb-10 title-reveal">References</h2>
      <div class="space-y-4">
        <div class="bullet-item method-card flex items-start gap-4" style="transition-delay:0.15s">
          <div class="w-10 h-10 rounded-lg bg-brand-blue/10 flex items-center justify-center flex-shrink-0">
            <svg width="18" height="18" fill="none" stroke="#0091FF" stroke-width="1.5" viewBox="0 0 24 24"><path d="M12 6.042A8.967 8.967 0 006 3.75c-1.052 0-2.062.18-3 .512v14.25A8.987 8.987 0 016 18c2.305 0 4.408.867 6 2.292m0-14.25a8.966 8.966 0 016-2.292c1.052 0 2.062.18 3 .512v14.25A8.987 8.987 0 0018 18a8.967 8.967 0 00-6 2.292m0-14.25v14.25"/></svg>
          </div>
          <div>
            <p class="text-sm text-white/80 font-medium">Organic Chemistry Textbooks</p>
            <p class="text-xs text-white/40 mt-0.5">Morrison & Boyd, Clayden et al., Solomons & Fryhle</p>
          </div>
        </div>
        <div class="bullet-item method-card flex items-start gap-4" style="transition-delay:0.3s">
          <div class="w-10 h-10 rounded-lg bg-brand-cyan/10 flex items-center justify-center flex-shrink-0">
            <svg width="18" height="18" fill="none" stroke="#00E5FF" stroke-width="1.5" viewBox="0 0 24 24"><path d="M19.5 14.25v-2.625a3.375 3.375 0 00-3.375-3.375h-1.5A1.125 1.125 0 0113.5 7.125v-1.5a3.375 3.375 0 00-3.375-3.375H8.25m2.25 0H5.625c-.621 0-1.125.504-1.125 1.125v17.25c0 .621.504 1.125 1.125 1.125h12.75c.621 0 1.125-.504 1.125-1.125V11.25a9 9 0 00-9-9z"/></svg>
          </div>
          <div>
            <p class="text-sm text-white/80 font-medium">Lecture Notes</p>
            <p class="text-xs text-white/40 mt-0.5">Dr. Tara Fuad — Tishk International University</p>
          </div>
        </div>
        <div class="bullet-item method-card flex items-start gap-4" style="transition-delay:0.45s">
          <div class="w-10 h-10 rounded-lg bg-brand-gold/10 flex items-center justify-center flex-shrink-0">
            <svg width="18" height="18" fill="none" stroke="#FFC800" stroke-width="1.5" viewBox="0 0 24 24"><path d="M12 21a9.004 9.004 0 008.716-6.747M12 21a9.004 9.004 0 01-8.716-6.747M12 21c2.485 0 4.5-4.03 4.5-9S14.485 3 12 3m0 18c-2.485 0-4.5-4.03-4.5-9S9.515 3 12 3m0 0a8.997 8.997 0 017.843 4.582M12 3a8.997 8.997 0 00-7.843 4.582m15.686 0A11.953 11.953 0 0112 10.5c-2.998 0-5.74-1.1-7.843-2.918m15.686 0A8.959 8.959 0 0121 12c0 .778-.099 1.533-.284 2.253m0 0A17.919 17.919 0 0112 16.5c-3.162 0-6.133-.815-8.716-2.247m0 0A9.015 9.015 0 013 12c0-1.605.42-3.113 1.157-4.418"/></svg>
          </div>
          <div>
            <p class="text-sm text-white/80 font-medium">Academic Resources</p>
            <p class="text-xs text-white/40 mt-0.5">NCERT Chemistry, PubChem, IUPAC Gold Book</p>
          </div>
        </div>
      </div>
      <div class="title-reveal mt-12 text-center" style="transition-delay:0.6s">
        <div class="inline-flex items-center gap-3 px-6 py-4 rounded-2xl bg-white/[0.03] border border-white/[0.06]">
          <img src="https://z-cdn-media.chatglm.cn/files/4d9e4f88-49d8-4f47-9b17-93101df5e1ee.jpg?auth_key=1877297798-cbeed9fa3cd74009ab8c581173dc54c4-0-51d611f4f3dd401382fb169294b785b0" alt="TIU" class="w-10 h-10 rounded-full object-cover border border-white/10">
          <div class="text-left">
            <p class="text-sm font-semibold text-white/80">Tishk International University</p>
            <p class="text-xs text-white/40">Sulaimaniyah, Kurdistan Region, Iraq</p>
          </div>
        </div>
        <p class="text-xs text-white/20 mt-6">Thank you for your attention</p>
      </div>
    </div>
  </section>

</main>

<!-- Navigation Controls -->
<div class="fixed bottom-0 left-0 right-0 z-40 flex items-center justify-between px-6 py-4" style="background: linear-gradient(to top, rgba(5,5,7,0.9), transparent);">
  <button id="prevBtn" class="nav-btn" onclick="prevSlide()" disabled>
    <svg width="20" height="20" fill="none" stroke="currentColor" stroke-width="1.5" viewBox="0 0 24 24"><path d="M10.5 19.5L3 12m0 0l7.5-7.5M3 12h18"/></svg>
  </button>
  <div class="flex items-center gap-3">
    <!-- Slide dots -->
    <div id="slideDots" class="flex items-center gap-1.5"></div>
    <div class="ml-4 hidden md:flex items-center gap-1 text-white/20">
      <span class="kbd">←</span>
      <span class="kbd">→</span>
      <span class="text-[10px] ml-1">or click</span>
    </div>
  </div>
  <button id="nextBtn" class="nav-btn" onclick="nextSlide()">
    <svg width="20" height="20" fill="none" stroke="currentColor" stroke-width="1.5" viewBox="0 0 24 24"><path d="M13.5 4.5L21 12m0 0l-7.5 7.5M21 12H3"/></svg>
  </button>
</div>

<!-- Overview Modal -->
<div id="overviewModal" class="fixed inset-0 z-50 hidden" style="background: rgba(5,5,7,0.95); backdrop-filter: blur(20px);">
  <div class="w-full h-full overflow-auto p-6 md:p-10">
    <div class="flex items-center justify-between mb-8">
      <h3 class="text-xl font-semibold">Slide Overview</h3>
      <button onclick="toggleOverview()" class="nav-btn !w-8 !h-8">
        <svg width="16" height="16" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><path d="M6 18L18 6M6 6l12 12"/></svg>
      </button>
    </div>
    <div id="overviewGrid" class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4 max-w-6xl mx-auto"></div>
  </div>
</div>

<script>
  const slides = document.querySelectorAll('.slide');
  const totalSlides = slides.length;
  let currentSlideIndex = 0;

  // Update total
  document.getElementById('totalSlides').textContent = String(totalSlides).padStart(2, '0');

  // Create dots
  const dotsContainer = document.getElementById('slideDots');
  for (let i = 0; i < totalSlides; i++) {
    const dot = document.createElement('button');
    dot.className = 'w-2 h-2 rounded-full bg-white/15 transition-all duration-300 hover:bg-white/30';
    dot.onclick = () => goToSlide(i + 1);
    dotsContainer.appendChild(dot);
  }

  // Create overview grid
  const slideNames = [
    'Title', 'Introduction', 'Structure of Phenol', 'Importance',
    'Methods Overview', 'From Haloarenes', 'From Sulfonic Acid',
    'From Diazonium Salts', 'Cumene Process', 'Properties',
    'Safety & Handling', 'Conclusion', 'References'
  ];
  const overviewGrid = document.getElementById('overviewGrid');
  slideNames.forEach((name, i) => {
    const card = document.createElement('button');
    card.className = 'p-4 rounded-xl bg-white/[0.03] border border-white/[0.06] text-left hover:border-brand-blue/30 hover:bg-white/[0.06] transition-all duration-200 group';
    card.innerHTML = `
      <div class="flex items-center gap-2 mb-2">
        <span class="text-xs font-mono text-brand-blue/60">${String(i+1).padStart(2,'0')}</span>
        ${i === currentSlideIndex ? '<span class="w-1.5 h-1.5 rounded-full bg-brand-blue"></span>' : ''}
      </div>
      <p class="text-sm text-white/60 group-hover:text-white/80 font-medium">${name}</p>
    `;
    card.onclick = () => { goToSlide(i + 1); toggleOverview(); };
    overviewGrid.appendChild(card);
  });

  function updateSlide(newIndex, direction) {
    if (newIndex < 0 || newIndex >= totalSlides || newIndex === currentSlideIndex) return;

    const oldSlide = slides[currentSlideIndex];
    const newSlide = slides[newIndex];

    // Remove previous states
    oldSlide.classList.remove('active');
    oldSlide.classList.add(direction === 'next' ? 'exit-left' : '');
    oldSlide.style.transform = direction === 'next' ? 'translateX(-60px)' : 'translateX(60px)';
    oldSlide.style.opacity = '0';

    // Prepare new slide
    newSlide.style.transform = direction === 'next' ? 'translateX(60px)' : 'translateX(-60px)';
    newSlide.style.opacity = '0';

    // Force reflow
    void newSlide.offsetWidth;

    newSlide.classList.add('active');
    newSlide.style.transform = '';
    newSlide.style.opacity = '';

    currentSlideIndex = newIndex;

    // Update UI
    document.getElementById('currentSlide').textContent = String(currentSlideIndex + 1).padStart(2, '0');
    document.getElementById('progressBar').style.width = ((currentSlideIndex + 1) / totalSlides * 100) + '%';

    // Update dots
    const dots = dotsContainer.children;
    for (let i = 0; i < dots.length; i++) {
      if (i === currentSlideIndex) {
        dots[i].className = 'w-6 h-2 rounded-full bg-brand-blue transition-all duration-300';
      } else {
        dots[i].className = 'w-2 h-2 rounded-full bg-white/15 transition-all duration-300 hover:bg-white/30';
      }
    }

    // Update buttons
    document.getElementById('prevBtn').disabled = currentSlideIndex === 0;
    document.getElementById('nextBtn').disabled = currentSlideIndex === totalSlides - 1;
  }

  function nextSlide() { updateSlide(currentSlideIndex + 1, 'next'); }
  function prevSlide() { updateSlide(currentSlideIndex - 1, 'prev'); }
  function goToSlide(n) { 
    const target = n - 1;
    updateSlide(target, target > currentSlideIndex ? 'next' : 'prev'); 
  }

  function toggleOverview() {
    const modal = document.getElementById('overviewModal');
    modal.classList.toggle('hidden');
    // Rebuild grid to show current indicator
    overviewGrid.innerHTML = '';
    slideNames.forEach((name, i) => {
      const card = document.createElement('button');
      card.className = 'p-4 rounded-xl bg-white/[0.03] border border-white/[0.06] text-left hover:border-brand-blue/30 hover:bg-white/[0.06] transition-all duration-200 group';
      card.innerHTML = `
        <div class="flex items-center gap-2 mb-2">
          <span class="text-xs font-mono text-brand-blue/60">${String(i+1).padStart(2,'0')}</span>
          ${i === currentSlideIndex ? '<span class="w-1.5 h-1.5 rounded-full bg-brand-blue"></span>' : ''}
        </div>
        <p class="text-sm text-white/60 group-hover:text-white/80 font-medium">${name}</p>
      `;
      card.onclick = () => { goToSlide(i + 1); toggleOverview(); };
      overviewGrid.appendChild(card);
    });
  }

  // Keyboard navigation
  document.addEventListener('keydown', (e) => {
    const modal = document.getElementById('overviewModal');
    if (!modal.classList.contains('hidden')) {
      if (e.key === 'Escape') toggleOverview();
      return;
    }
    if (e.key === 'ArrowRight' || e.key === 'ArrowDown' || e.key === ' ') { e.preventDefault(); nextSlide(); }
    if (e.key === 'ArrowLeft' || e.key === 'ArrowUp') { e.preventDefault(); prevSlide(); }
    if (e.key === 'Escape') toggleOverview();
    if (e.key === 'Home') { e.preventDefault(); goToSlide(1); }
    if (e.key === 'End') { e.preventDefault(); goToSlide(totalSlides); }
  });

  // Touch swipe
  let touchStartX = 0;
  let touchStartY = 0;
  document.addEventListener('touchstart', (e) => {
    touchStartX = e.changedTouches[0].screenX;
    touchStartY = e.changedTouches[0].screenY;
  });
  document.addEventListener('touchend', (e) => {
    const dx = e.changedTouches[0].screenX - touchStartX;
    const dy = e.changedTouches[0].screenY - touchStartY;
    if (Math.abs(dx) > Math.abs(dy) && Math.abs(dx) > 50) {
      if (dx < 0) nextSlide();
      else prevSlide();
    }
  });

  // Initialize
  updateSlide(0, 'next');
</script>

</body>
</html>


ئەمەم بۆ بکە بە power point file
