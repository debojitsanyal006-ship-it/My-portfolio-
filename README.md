<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>D.S GAMER — Debojit | Futuristic Gaming Portfolio</title>

<!-- ===== GOOGLE FONTS ===== -->
<link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;600;700;800;900&family=Rajdhani:wght@300;400;500;600;700&family=Share+Tech+Mono&display=swap" rel="stylesheet"/>

<style>
/* ===================================================
   CSS VARIABLES & RESET
=================================================== */
:root {
  --bg-dark:     #1A1A1B;
  --bg-sec:      #333F44;
  --neon-cyan:   #37AA9C;
  --soft-mint:   #94F3E4;
  --neon-purple: #8B5CF6;
  --neon-purple2:#C084FC;
  --white:       #FFFFFF;
  --text-dim:    #94A3B8;
  --glass:       rgba(51,63,68,0.35);
  --glass-border:rgba(55,170,156,0.25);
  --glow-cyan:   0 0 20px rgba(55,170,156,0.6), 0 0 60px rgba(55,170,156,0.3);
  --glow-purple: 0 0 20px rgba(139,92,246,0.6), 0 0 60px rgba(139,92,246,0.3);
  --font-hud:    'Orbitron', monospace;
  --font-body:   'Rajdhani', sans-serif;
  --font-mono:   'Share Tech Mono', monospace;
}

*, *::before, *::after { margin:0; padding:0; box-sizing:border-box; }

html { scroll-behavior: smooth; }

body {
  background: var(--bg-dark);
  color: var(--white);
  font-family: var(--font-body);
  overflow-x: hidden;
  cursor: none;
}

/* ===================================================
   CUSTOM CURSOR
=================================================== */
#cursor {
  position: fixed;
  width: 12px; height: 12px;
  background: var(--neon-cyan);
  border-radius: 50%;
  pointer-events: none;
  z-index: 9999;
  transform: translate(-50%,-50%);
  transition: transform .08s, width .2s, height .2s, background .2s;
  box-shadow: var(--glow-cyan);
  mix-blend-mode: screen;
}
#cursor-ring {
  position: fixed;
  width: 36px; height: 36px;
  border: 1.5px solid var(--neon-cyan);
  border-radius: 50%;
  pointer-events: none;
  z-index: 9998;
  transform: translate(-50%,-50%);
  transition: transform .18s ease, width .2s, height .2s, border-color .2s;
  opacity: .7;
}
body:hover #cursor-ring { opacity: 1; }

/* ===================================================
   SCROLL PROGRESS BAR
=================================================== */
#scroll-bar {
  position: fixed;
  top: 0; left: 0;
  height: 3px;
  background: linear-gradient(90deg, var(--neon-cyan), var(--neon-purple));
  z-index: 9997;
  width: 0%;
  box-shadow: var(--glow-cyan);
  transition: width .1s;
}

/* ===================================================
   PRELOADER
=================================================== */
#preloader {
  position: fixed; inset: 0;
  background: var(--bg-dark);
  z-index: 99999;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  transition: opacity .6s, visibility .6s;
}
#preloader.hidden { opacity: 0; visibility: hidden; }

.pre-logo {
  font-family: var(--font-hud);
  font-size: clamp(3rem, 10vw, 7rem);
  font-weight: 900;
  background: linear-gradient(135deg, var(--neon-cyan), var(--soft-mint), var(--neon-purple2));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  letter-spacing: 8px;
  animation: flicker 1.4s infinite alternate;
}
.pre-bar-wrap {
  width: 280px; height: 3px;
  background: var(--bg-sec);
  border-radius: 4px;
  margin-top: 32px;
  overflow: hidden;
}
.pre-bar {
  height: 100%;
  background: linear-gradient(90deg, var(--neon-cyan), var(--neon-purple));
  border-radius: 4px;
  animation: preLoad 2s ease forwards;
  box-shadow: var(--glow-cyan);
}
.pre-text {
  font-family: var(--font-mono);
  font-size: .8rem;
  color: var(--neon-cyan);
  margin-top: 14px;
  letter-spacing: 4px;
  animation: blink 1s step-end infinite;
}
@keyframes preLoad { from{width:0} to{width:100%} }
@keyframes blink { 50%{opacity:0} }

/* ===================================================
   NAVBAR
=================================================== */
nav {
  position: fixed; top: 0; left: 0; right: 0;
  z-index: 1000;
  padding: 0 5%;
  height: 70px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  background: rgba(26,26,27,.6);
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  border-bottom: 1px solid var(--glass-border);
  transition: background .3s;
}
nav.scrolled { background: rgba(26,26,27,.92); }

.nav-logo {
  font-family: var(--font-hud);
  font-size: 1.4rem;
  font-weight: 900;
  background: linear-gradient(135deg, var(--neon-cyan), var(--soft-mint));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  letter-spacing: 4px;
  text-shadow: none;
  position: relative;
}
.nav-logo::after {
  content: '';
  position: absolute;
  bottom: -4px; left: 0; right: 0;
  height: 1px;
  background: linear-gradient(90deg, var(--neon-cyan), transparent);
}

.nav-links { display: flex; gap: 2rem; list-style: none; }
.nav-links a {
  font-family: var(--font-hud);
  font-size: .7rem;
  letter-spacing: 2px;
  color: var(--text-dim);
  text-decoration: none;
  text-transform: uppercase;
  position: relative;
  transition: color .3s;
}
.nav-links a::after {
  content: '';
  position: absolute;
  bottom: -4px; left: 0; right: 0;
  height: 1px;
  background: var(--neon-cyan);
  transform: scaleX(0);
  transform-origin: left;
  transition: transform .3s;
}
.nav-links a:hover { color: var(--neon-cyan); }
.nav-links a:hover::after { transform: scaleX(1); }

.nav-audio {
  background: none;
  border: 1px solid var(--glass-border);
  color: var(--neon-cyan);
  width: 36px; height: 36px;
  border-radius: 4px;
  cursor: none;
  font-size: .8rem;
  display: flex; align-items: center; justify-content: center;
  transition: all .3s;
  font-family: var(--font-mono);
}
.nav-audio:hover { background: rgba(55,170,156,.15); box-shadow: var(--glow-cyan); }

.hamburger {
  display: none;
  flex-direction: column;
  gap: 5px;
  background: none;
  border: none;
  cursor: none;
}
.hamburger span {
  width: 24px; height: 2px;
  background: var(--neon-cyan);
  transition: all .3s;
}

/* ===================================================
   HERO SECTION
=================================================== */
#hero {
  min-height: 100vh;
  display: flex;
  align-items: center;
  position: relative;
  overflow: hidden;
  padding: 70px 5% 0;
}

/* Animated grid background */
.hero-grid {
  position: absolute; inset: 0;
  background-image:
    linear-gradient(rgba(55,170,156,.07) 1px, transparent 1px),
    linear-gradient(90deg, rgba(55,170,156,.07) 1px, transparent 1px);
  background-size: 60px 60px;
  animation: gridMove 20s linear infinite;
  z-index: 0;
}
@keyframes gridMove {
  0%  { transform: translateY(0) }
  100%{ transform: translateY(60px) }
}

/* Particle canvas */
#particle-canvas {
  position: absolute; inset: 0; z-index: 0;
  pointer-events: none;
}

/* Corner HUD decorations */
.hud-corner {
  position: absolute;
  width: 60px; height: 60px;
  z-index: 2;
}
.hud-corner.tl { top: 90px; left: 5%; border-top: 2px solid var(--neon-cyan); border-left: 2px solid var(--neon-cyan); }
.hud-corner.tr { top: 90px; right: 5%; border-top: 2px solid var(--neon-purple); border-right: 2px solid var(--neon-purple); }
.hud-corner.bl { bottom: 30px; left: 5%; border-bottom: 2px solid var(--neon-cyan); border-left: 2px solid var(--neon-cyan); }
.hud-corner.br { bottom: 30px; right: 5%; border-bottom: 2px solid var(--neon-purple); border-right: 2px solid var(--neon-purple); }

.hero-content {
  position: relative; z-index: 2;
  flex: 1;
  max-width: 600px;
}

.hero-badge {
  display: inline-flex;
  align-items: center;
  gap: .6rem;
  background: rgba(55,170,156,.1);
  border: 1px solid var(--glass-border);
  padding: .35rem 1rem;
  border-radius: 2px;
  font-family: var(--font-mono);
  font-size: .72rem;
  letter-spacing: 3px;
  color: var(--neon-cyan);
  margin-bottom: 1.5rem;
  animation: fadeInUp .8s ease forwards;
  opacity: 0;
  animation-delay: .2s;
}
.hero-badge .dot {
  width: 6px; height: 6px;
  background: var(--neon-cyan);
  border-radius: 50%;
  animation: pulse 1.4s infinite;
}

.hero-ds {
  font-family: var(--font-hud);
  font-size: clamp(5rem, 14vw, 12rem);
  font-weight: 900;
  line-height: .9;
  background: linear-gradient(135deg, var(--neon-cyan) 0%, var(--soft-mint) 40%, var(--neon-purple2) 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  letter-spacing: 4px;
  filter: drop-shadow(0 0 30px rgba(55,170,156,.5));
  animation: fadeInUp .8s ease forwards;
  opacity: 0;
  animation-delay: .4s;
  position: relative;
}
.hero-ds::after {
  content: 'D.S';
  position: absolute;
  inset: 0;
  -webkit-text-fill-color: transparent;
  background: linear-gradient(135deg, var(--neon-cyan), var(--soft-mint), var(--neon-purple2));
  -webkit-background-clip: text;
  background-clip: text;
  filter: blur(18px);
  opacity: .4;
  animation: logoPulse 3s ease-in-out infinite alternate;
  z-index: -1;
}
@keyframes logoPulse { from{filter:blur(18px)} to{filter:blur(28px)} }

.hero-name {
  font-family: var(--font-hud);
  font-size: clamp(1rem, 3vw, 1.5rem);
  font-weight: 700;
  letter-spacing: 8px;
  color: var(--white);
  text-transform: uppercase;
  margin-top: .5rem;
  animation: fadeInUp .8s ease forwards;
  opacity: 0;
  animation-delay: .6s;
}
.hero-name span { color: var(--neon-cyan); }

.hero-sub {
  font-family: var(--font-body);
  font-size: clamp(.9rem, 2vw, 1.1rem);
  color: var(--text-dim);
  letter-spacing: 2px;
  margin-top: 1rem;
  animation: fadeInUp .8s ease forwards;
  opacity: 0;
  animation-delay: .8s;
}

.hero-btns {
  display: flex; gap: 1rem; flex-wrap: wrap;
  margin-top: 2.5rem;
  animation: fadeInUp .8s ease forwards;
  opacity: 0;
  animation-delay: 1s;
}

.btn-primary {
  font-family: var(--font-hud);
  font-size: .75rem;
  letter-spacing: 3px;
  text-transform: uppercase;
  padding: .9rem 2.2rem;
  background: linear-gradient(135deg, var(--neon-cyan), var(--soft-mint));
  color: var(--bg-dark);
  border: none;
  cursor: none;
  clip-path: polygon(12px 0, 100% 0, calc(100% - 12px) 100%, 0 100%);
  position: relative;
  overflow: hidden;
  transition: all .3s;
  font-weight: 700;
}
.btn-primary::before {
  content: '';
  position: absolute; inset: 0;
  background: linear-gradient(135deg, var(--soft-mint), var(--neon-cyan));
  opacity: 0;
  transition: opacity .3s;
}
.btn-primary:hover { transform: translateY(-3px); box-shadow: var(--glow-cyan); }
.btn-primary:hover::before { opacity: 1; }
.btn-primary span { position: relative; z-index: 1; }

.btn-secondary {
  font-family: var(--font-hud);
  font-size: .75rem;
  letter-spacing: 3px;
  text-transform: uppercase;
  padding: .9rem 2.2rem;
  background: transparent;
  color: var(--neon-cyan);
  border: 1px solid var(--neon-cyan);
  cursor: none;
  clip-path: polygon(12px 0, 100% 0, calc(100% - 12px) 100%, 0 100%);
  position: relative;
  overflow: hidden;
  transition: all .3s;
}
.btn-secondary::before {
  content: '';
  position: absolute; inset: 0;
  background: rgba(55,170,156,.1);
  transform: scaleX(0);
  transform-origin: left;
  transition: transform .3s;
}
.btn-secondary:hover { transform: translateY(-3px); box-shadow: var(--glow-cyan); }
.btn-secondary:hover::before { transform: scaleX(1); }
.btn-secondary span { position: relative; z-index: 1; }

/* ===================================================
   3D GAMER MODEL (CSS ART)
=================================================== */
.hero-model-wrap {
  position: relative;
  flex: 1;
  max-width: 520px;
  height: 520px;
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 2;
  margin-left: auto;
  animation: fadeInRight .9s ease forwards;
  opacity: 0;
  animation-delay: .5s;
}

/* Rotating glow rings */
.ring {
  position: absolute;
  border-radius: 50%;
  border: 1px solid;
}
.ring-1 {
  width: 420px; height: 420px;
  border-color: rgba(55,170,156,.4);
  animation: spin 12s linear infinite;
  box-shadow: 0 0 30px rgba(55,170,156,.2) inset, 0 0 30px rgba(55,170,156,.2);
}
.ring-2 {
  width: 340px; height: 340px;
  border-color: rgba(139,92,246,.4);
  animation: spin 8s linear infinite reverse;
  box-shadow: 0 0 20px rgba(139,92,246,.2) inset;
}
.ring-3 {
  width: 260px; height: 260px;
  border-color: rgba(148,243,228,.3);
  animation: spin 15s linear infinite;
  border-style: dashed;
}

@keyframes spin { to { transform: rotate(360deg); } }

/* Gamer figure (stylised CSS art) */
.gamer-fig {
  position: absolute;
  width: 230px;
  transform-style: preserve-3d;
  animation: figFloat 4s ease-in-out infinite alternate;
}
@keyframes figFloat {
  from { transform: translateY(0) rotateY(-8deg); }
  to   { transform: translateY(-18px) rotateY(8deg); }
}

.fig-glow {
  position: absolute;
  bottom: -40px; left: 50%;
  transform: translateX(-50%);
  width: 180px; height: 30px;
  background: radial-gradient(ellipse, rgba(55,170,156,.5) 0%, transparent 70%);
  filter: blur(8px);
  animation: glowPulse 2s ease-in-out infinite alternate;
}
@keyframes glowPulse { from{opacity:.5;transform:translateX(-50%) scaleX(.8)} to{opacity:1;transform:translateX(-50%) scaleX(1.1)} }

/* Cloak/body layers */
.fig-body {
  position: relative;
  width: 230px;
  display: flex;
  flex-direction: column;
  align-items: center;
}
.fig-head-wrap { position: relative; width: 80px; height: 80px; margin-bottom: -10px; z-index: 3; }
.fig-head {
  width: 60px; height: 70px;
  background: linear-gradient(160deg, #c8c8d8 0%, #9090a8 100%);
  border-radius: 40% 40% 35% 35%;
  margin: 0 auto;
  position: relative;
  box-shadow: 0 0 20px rgba(139,92,246,.4);
}
.fig-head::before { /* hair bun */
  content: '';
  position: absolute;
  top: -12px; left: 50%; transform: translateX(-50%);
  width: 22px; height: 22px;
  background: #d0d0e0;
  border-radius: 50%;
  box-shadow: 0 0 10px rgba(148,243,228,.5);
}
.fig-hair {
  position: absolute;
  top: 14px; left: -4px;
  width: 70px; height: 60px;
  background: linear-gradient(160deg, #d8d8e8 0%, #b0b0c0 100%);
  border-radius: 0 0 40% 40%;
  z-index: -1;
}
.fig-mark {
  position: absolute;
  top: 22px; left: 50%; transform: translateX(-50%);
  width: 10px; height: 2px;
  background: var(--neon-purple);
  box-shadow: 0 0 6px var(--neon-purple);
}
.fig-torso {
  width: 130px; height: 120px;
  background: linear-gradient(170deg, #2a2a3e 0%, #1a1a2e 100%);
  border-radius: 10px 10px 8px 8px;
  position: relative;
  z-index: 2;
  border: 1px solid rgba(139,92,246,.3);
}
.fig-torso::after {
  content: '';
  position: absolute;
  top: 20px; left: 50%; transform: translateX(-50%);
  width: 40px; height: 40px;
  border-radius: 50%;
  background: radial-gradient(circle, rgba(139,92,246,.6), transparent 70%);
  animation: coreGlow 2s infinite alternate;
}
@keyframes coreGlow { from{opacity:.6;transform:translateX(-50%) scale(.9)} to{opacity:1;transform:translateX(-50%) scale(1.1)} }

.fig-cloak-l, .fig-cloak-r {
  position: absolute;
  top: 10px;
  width: 55px; height: 130px;
  background: linear-gradient(170deg, #1e1e30, #0d0d1a);
  border-radius: 4px 4px 20px 20px;
  border: 1px solid rgba(55,170,156,.2);
}
.fig-cloak-l { left: -52px; transform: rotate(-8deg) skewY(-2deg); }
.fig-cloak-r { right: -52px; transform: rotate(8deg) skewY(2deg); }

/* Lantern */
.fig-lantern {
  position: absolute;
  top: -10px; right: -80px;
  width: 30px; height: 50px;
  z-index: 5;
}
.lantern-body {
  width: 100%; height: 100%;
  background: linear-gradient(160deg, #1a1a2e, #0d0d1a);
  border: 1px solid rgba(139,92,246,.5);
  border-radius: 4px;
  display: flex; align-items: center; justify-content: center;
  position: relative;
}
.lantern-gem {
  width: 14px; height: 14px;
  background: radial-gradient(circle, #c084fc, #8b5cf6);
  border-radius: 3px;
  transform: rotate(45deg);
  box-shadow: 0 0 15px var(--neon-purple), 0 0 30px rgba(139,92,246,.4);
  animation: gemPulse 1.5s infinite alternate;
}
@keyframes gemPulse { from{box-shadow:0 0 10px var(--neon-purple)} to{box-shadow:0 0 25px var(--neon-purple), 0 0 50px rgba(139,92,246,.5)} }

.fig-bottom-gem {
  width: 18px; height: 18px;
  background: radial-gradient(circle, var(--soft-mint), var(--neon-cyan));
  transform: rotate(45deg);
  margin: 6px auto 0;
  border-radius: 3px;
  box-shadow: 0 0 20px var(--neon-cyan);
  animation: gemPulse 2s infinite alternate;
}

/* Energy particles around model */
.e-particle {
  position: absolute;
  border-radius: 50%;
  background: var(--neon-cyan);
  box-shadow: 0 0 6px var(--neon-cyan);
  animation: eFloat linear infinite;
}
@keyframes eFloat {
  0%   { transform: translate(0,0) scale(1); opacity:.8; }
  50%  { opacity:1; }
  100% { transform: translate(var(--tx), var(--ty)) scale(0); opacity:0; }
}

/* ===================================================
   SECTION SHARED STYLES
=================================================== */
section { padding: 100px 5%; }

.section-label {
  font-family: var(--font-mono);
  font-size: .72rem;
  letter-spacing: 4px;
  color: var(--neon-cyan);
  text-transform: uppercase;
  margin-bottom: .6rem;
  display: flex;
  align-items: center;
  gap: .8rem;
}
.section-label::before {
  content: '';
  width: 30px; height: 1px;
  background: var(--neon-cyan);
}
.section-label::after {
  content: '';
  flex: 1;
  height: 1px;
  background: linear-gradient(90deg, var(--glass-border), transparent);
}

.section-title {
  font-family: var(--font-hud);
  font-size: clamp(2rem, 5vw, 3.5rem);
  font-weight: 800;
  letter-spacing: 3px;
  text-transform: uppercase;
  background: linear-gradient(135deg, var(--white) 40%, var(--neon-cyan) 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  margin-bottom: 1rem;
}

.divider {
  width: 80px; height: 3px;
  background: linear-gradient(90deg, var(--neon-cyan), transparent);
  margin-bottom: 3rem;
}

/* Reveal animation */
.reveal {
  opacity: 0;
  transform: translateY(40px);
  transition: opacity .7s ease, transform .7s ease;
}
.reveal.visible {
  opacity: 1;
  transform: translateY(0);
}

/* ===================================================
   ABOUT SECTION
=================================================== */
#about { background: linear-gradient(180deg, var(--bg-dark) 0%, #1e2830 100%); }

.about-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 3rem;
  align-items: center;
  margin-top: 2rem;
}

.about-text p {
  font-size: 1.1rem;
  line-height: 1.9;
  color: var(--text-dim);
  margin-bottom: 1rem;
  font-weight: 400;
}
.about-text p span { color: var(--neon-cyan); font-weight: 600; }

.about-text .typing-bio {
  font-family: var(--font-mono);
  font-size: .9rem;
  color: var(--soft-mint);
  border-right: 2px solid var(--neon-cyan);
  white-space: nowrap;
  overflow: hidden;
  width: 0;
  animation: typing 3.5s steps(45,end) 1.5s forwards, blink .7s step-end infinite;
  display: inline-block;
}
@keyframes typing { to{width:100%} }

.stat-cards {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
}
.stat-card {
  background: var(--glass);
  border: 1px solid var(--glass-border);
  border-radius: 4px;
  padding: 1.5rem;
  text-align: center;
  position: relative;
  overflow: hidden;
  transition: all .3s;
  backdrop-filter: blur(10px);
}
.stat-card::before {
  content: '';
  position: absolute;
  top: 0; left: 0; right: 0;
  height: 2px;
  background: linear-gradient(90deg, var(--neon-cyan), var(--neon-purple));
}
.stat-card:hover {
  transform: translateY(-4px);
  box-shadow: var(--glow-cyan);
  border-color: var(--neon-cyan);
}
.stat-num {
  font-family: var(--font-hud);
  font-size: 2.4rem;
  font-weight: 900;
  background: linear-gradient(135deg, var(--neon-cyan), var(--soft-mint));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}
.stat-label {
  font-family: var(--font-mono);
  f
