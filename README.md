<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>The Cinematic Realm | Portfolio</title>
    
    <!-- Google Fonts: Elegant Serif for Headings, Clean Sans-Serif for Body -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,400;0,600;1,400&family=Inter:wght@300;400;600&display=swap" rel="stylesheet">

    <style>
    /* ============================================================
   CUSTOM CURSOR SYSTEM (Neo-Noir Theme)
 ============================================================ */

/* ডেস্কটপে ডিফল্ট কার্সার হাইড করার জন্য */
body {
  cursor: none;
}

/* টাচ স্ক্রিন ডিভাইসে ডিফল্ট কার্সার ফিরিয়ে আনার জন্য অ্যাক্সেসিবিলিটি */
@media (hover: none) {
  body { cursor: auto; }
}

#custom-cursor {
  position: fixed;
  top: 0; left: 0;
  z-index: 99999;
  pointer-events: none;
  will-change: opacity;
  transition: opacity 0.35s ease;
}

/* দ্য ক্রিমসন কোর (কেন্দ্রের ডায়মন্ড আকৃতি) */
#cursor-core {
  position: absolute;
  width: 8px;
  height: 8px;
  background: #8b0000; /* Crimson Red */
  transform: translate(-50%, -50%) rotate(45deg);
  top: 0; left: 0;
  border-radius: 1px;
  box-shadow:
    0 0 4px 1px rgba(139,0,0,0.9),
    0 0 8px 2px rgba(139,0,0,0.4);
  will-change: transform, opacity;
  transition:
    opacity 0.18s ease,
    transform 0.18s ease;
  z-index: 2;
}

/* দ্য ইঙ্ক আভা (বাইরের ব্লার সার্কেল) */
#cursor-aura {
  position: absolute;
  width: 28px;
  height: 28px;
  background: rgba(20, 20, 20, 0.7);
  border-radius: 50%;
  filter: blur(4px);
  transform: translate(-50%, -50%) scale(1);
  top: 0; left: 0;
  will-change: transform, filter, box-shadow;
  transition:
    transform 0.28s cubic-bezier(0.22, 1, 0.36, 1),
    filter    0.28s cubic-bezier(0.22, 1, 0.36, 1),
    box-shadow 0.28s cubic-bezier(0.22, 1, 0.36, 1);
  z-index: 1;
}

/* কোনো ইন্টারঅ্যাক্টিভ এলিমেন্টে হোভার করলে আভার পরিবর্তন */
#cursor-aura.is-hovering {
  transform: translate(-50%, -50%) scale(1.85);
  filter: blur(2px);
  box-shadow:
    0 0 12px 4px rgba(139,0,0,0.35),
    0 0 28px 8px rgba(139,0,0,0.15),
    inset 0 0 6px rgba(139,0,0,0.2);
  animation: auraPulse 1.6s ease-in-out infinite;
}

#cursor-core.is-hovering {
  opacity: 0;
  transform: translate(-50%, -50%) rotate(45deg) scale(0.3);
}

/* হোভার অবস্থার পালস অ্যানিমেশন */
@keyframes auraPulse {
  0%, 100% {
    box-shadow:
      0 0 12px 4px rgba(139,0,0,0.35),
      0 0 28px 8px rgba(139,0,0,0.15);
  }
  50% {
    box-shadow:
      0 0 18px 7px rgba(192,57,43,0.55),
      0 0 40px 14px rgba(139,0,0,0.22),
      0 0 2px 1px rgba(255,80,60,0.3);
  }
}

/* মোবাইল বা টাচ ডিভাইসে হাইড করার ইউটিলিটি */
#custom-cursor.touch-hidden { opacity: 0 !important; }

        /* --- CSS VARIABLES & CORE STYLES --- */
        :root {
            --bg-pure: #050505;
            --bg-card: #0d0d0d;
            --accent-crimson: #ff003c;
            --accent-glow: rgba(255, 0, 60, 0.35);
            --text-main: #e0e0e0;
            --text-muted: #8c8c8c;
            --font-serif: 'Cormorant Garamond', serif;
            --font-sans: 'Inter', sans-serif;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        html {
            scroll-behavior: smooth;
            background-color: var(--bg-pure);
            color: var(--text-main);
            font-family: var(--font-sans);
            overflow-x: hidden;
        }

        /* Custom Scrollbar */
        ::-webkit-scrollbar {
            width: 8px;
        }
        ::-webkit-scrollbar-track {
            background: var(--bg-pure);
        }
        ::-webkit-scrollbar-thumb {
            background: #1a1a1a;
            border-radius: 4px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: var(--accent-crimson);
        }

        body {<div id="custom-cursor" aria-hidden="true">
  <div id="cursor-aura"></div>
  <div id="cursor-core"></div>
</div>

            position: relative;
            min-height: 100vh;
        }

        /* Hardware-Accelerated Film Grain Overlay */
        body::after {
            content: "";
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noiseFilter'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.8' numOctaves='3' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noiseFilter)'/%3E%3C/svg%3E");
            opacity: 0.04;
            pointer-events: none;
            z-index: 9999;
        }

        /* --- GLOBAL ANIMATIONS --- */
        .reveal {
            opacity: 0;
            transform: translateY(40px);
            transition: opacity 1.2s cubic-bezier(0.215, 0.610, 0.355, 1), transform 1.2s cubic-bezier(0.215, 0.610, 0.355, 1);
        }

        .reveal.active {
            opacity: 1;
            transform: translateY(0);
        }

        /* --- NAVIGATION --- */
        nav {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            padding: 2rem 4%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            z-index: 100;
            background: linear-gradient(to bottom, rgba(5,5,5,0.9) 0%, rgba(5,5,5,0) 100%);
            backdrop-filter: blur(5px);
        }

        .logo {
            font-family: var(--font-serif);
            font-size: 1.8rem;
            font-weight: 600;
            letter-spacing: 2px;
            text-transform: uppercase;
            color: #fff;
            text-decoration: none;
        }

        .logo span {
            color: var(--accent-crimson);
        }

        .nav-links {
            display: flex;
            list-style: none;
            gap: 2rem;
        }

        .nav-links a {
            color: var(--text-muted);
            text-decoration: none;
            font-size: 0.85rem;
            text-transform: uppercase;
            letter-spacing: 2px;
            transition: color 0.3s ease;
        }

        .nav-links a:hover {
            color: var(--accent-crimson);
        }

        /* --- HERO SECTION --- */
        .hero {
            height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            position: relative;
            padding: 0 1rem;
            background: radial-gradient(circle at center, rgba(20, 20, 20, 0.8) 0%, var(--bg-pure) 100%);
        }

        /* Cinematic Mood Vignette */
        .hero::before {
            content: '';
            position: absolute;
            inset: 0;
            background: radial-gradient(circle at center, transparent 30%, rgba(0,0,0,0.9) 100%);
            pointer-events: none;
        }

        .hero-title {
            font-family: var(--font-serif);
            font-size: clamp(3.5rem, 8vw, 7rem);
            font-weight: 400;
            line-height: 1.1;
            margin-bottom: 1.5rem;
            letter-spacing: -1px;
            color: #fff;
            z-index: 1;
        }

        .hero-title em {
            font-style: italic;
            font-family: var(--font-serif);
            color: var(--text-muted);
        }

        .hero-subtitle {
            font-size: clamp(0.8rem, 2vw, 1rem);
            text-transform: uppercase;
            letter-spacing: 6px;
            color: var(--text-muted);
            margin-bottom: 3rem;
            z-index: 1;
        }

        /* Glassmorphism CTA */
        .cta-btn {
            display: inline-block;
            padding: 1.2rem 2.5rem;
            font-family: var(--font-sans);
            font-size: 0.85rem;
            text-transform: uppercase;
            letter-spacing: 3px;
            color: #fff;
            text-decoration: none;
            background: rgba(255, 255, 255, 0.03);
            border: 1px solid rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            -webkit-backdrop-filter: blur(10px);
            border-radius: 0px;
            position: relative;
            overflow: hidden;
            transition: all 0.4s ease;
            cursor: pointer;
            z-index: 1;
        }

        .cta-btn:hover {
            border-color: var(--accent-crimson);
            box-shadow: 0 0 25px var(--accent-glow);
            background: rgba(255, 0, 60, 0.05);
            transform: translateY(-2px);
        }

        /* --- SECTION STRUCTURE --- */
        section {
            padding: 8rem 4% 4rem 4%;
            max-width: 1400px;
            margin: 0 auto;
        }

        .section-title {
            font-family: var(--font-serif);
            font-size: clamp(2.5rem, 5vw, 4rem);
            font-weight: 400;
            margin-bottom: 4rem;
            position: relative;
            display: flex;
            align-items: center;
            gap: 2rem;
        }

        .section-title::after {
            content: '';
            height: 1px;
            flex-grow: 1;
            background: linear-gradient(to right, rgba(255,0,60,0.5), transparent);
        }

        /* --- SHORT FILMS (VIDEO SHOWCASE) --- */
        .video-grid {
            display: grid;
            grid-template-columns: 1fr;
            gap: 4rem;
        }

        .video-container {
            position: relative;
            width: 100%;
            background: var(--bg-card);
            border: 1px solid #1a1a1a;
            padding: 1.5rem;
            transition: border-color 0.5s ease, box-shadow 0.5s ease;
        }

        /* Villain Aura Neon Shadow Glow */
        .video-container:hover {
            border-color: rgba(255, 0, 60, 0.4);
            box-shadow: 0 15px 50px rgba(0, 0, 0, 0.9), 0 0 30px var(--accent-glow);
        }

        .video-wrapper {
            position: relative;
            width: 100%;
            aspect-ratio: 16 / 9;
            overflow: hidden;
        }

        .video-wrapper iframe {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            border: 0;
        }

        .video-meta {
            margin-top: 1.5rem;
            display: flex;
            justify-content: space-between;
            align-items: flex-start;
            flex-wrap: wrap;
            gap: 1rem;
        }

        .video-info h3 {
            font-family: var(--font-serif);
            font-size: 1.8rem;
            font-weight: 400;
            color: #fff;
            margin-bottom: 0.25rem;
        }

        .video-info p {
            font-size: 0.9rem;
            color: var(--text-muted);
        }

        /* --- PHOTOGRAPHY GALLERY (MASONRY/GRID) --- */
        .gallery-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(350px, 1fr));
            auto-rows: 450px;
            gap: 1.5rem;
        }

        .gallery-item {
            position: relative;
            overflow: hidden;
            cursor: pointer;
            background: var(--bg-card);
            border: 1px solid #111;
        }

        /* Making alternate items taller for a pseudo-masonry feel */
        @media (min-width: 768px) {
            .gallery-item:nth-child(2n) {
                grid-row: span 1.2;
            }
            .gallery-item:nth-child(3n) {
                grid-row: span 1.1;
            }
        }

        .gallery-item img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            /* Grayscale to color base state */
            filter: grayscale(100%) brightness(0.7) contrast(1.1);
            transition: filter 0.7s cubic-bezier(0.15, 0.85, 0.45, 1), transform 0.7s cubic-bezier(0.15, 0.85, 0.45, 1);
        }

        .gallery-item:hover img {
            filter: grayscale(0%) brightness(0.9) contrast(1);
            transform: scale(1.03);
        }

        .gallery-overlay {
            position: absolute;
            bottom: 0;
            left: 0;
            width: 100%;
            padding: 2rem;
            background: linear-gradient(to top, rgba(0,0,0,0.9) 0%, rgba(0,0,0,0) 100%);
            opacity: 0;
            transition: opacity 0.4s ease;
        }

        .gallery-item:hover .gallery-overlay {
            opacity: 1;
        }

        .gallery-overlay h4 {
            font-family: var(--font-serif);
            font-size: 1.5rem;
            color: #fff;
        }

        /* --- ABOUT / BIO SECTION --- */
        .about-layout {
            display: grid;
            grid-template-columns: 1fr;
            gap: 3rem;
        }

        @media (min-width: 992px) {
            .about-layout {
                grid-template-columns: 2fr 1fr;
            }
        }

        .bio-text {
            font-family: var(--font-serif);
            font-size: clamp(1.4rem, 3vw, 2.2rem);
            line-height: 1.6;
            color: #d1d1d1;
        }

        .bio-text span {
            color: #fff;
            border-bottom: 1px dashed var(--accent-crimson);
        }

        .bio-details {
            display: flex;
            flex-direction: column;
            gap: 2rem;
            justify-content: center;
            border-left: 1px solid #1a1a1a;
            padding-left: 0;
        }

        @media (min-width: 992px) {
            .bio-details {
                padding-left: 3rem;
            }
        }

        .detail-item h5 {
            font-size: 0.8rem;
            text-transform: uppercase;
            letter-spacing: 3px;
            color: var(--accent-crimson);
            margin-bottom: 0.5rem;
        }

        .detail-item p {
            font-size: 1rem;
            color: var(--text-muted);
        }

        /* --- LIGHTBOX MODAL --- */
        .lightbox {
            position: fixed;
            inset: 0;
            background: rgba(5, 5, 5, 0.98);
            z-index: 1000;
            display: flex;
            justify-content: center;
            align-items: center;
            opacity: 0;
            pointer-events: none;
            transition: opacity 0.4s ease;
            padding: 2rem;
        }

        .lightbox.active {
            opacity: 1;
            pointer-events: auto;
        }

        .lightbox-content {
            max-width: 90%;
            max-height: 85vh;
            object-fit: contain;
            border: 1px solid #222;
            transform: scale(0.95);
            transition: transform 0.4s ease;
        }

        .lightbox.active .lightbox-content {
            transform: scale(1);
        }

        .lightbox-close {
            position: absolute;
            top: 2rem;
            right: 2rem;
            background: none;
            border: none;
            color: #fff;
            font-size: 2.5rem;
            font-weight: 300;
            cursor: pointer;
            transition: color 0.3s ease;
        }

        .lightbox-close:hover {
            color: var(--accent-crimson);
        }

        /* --- FOOTER --- */
        footer {
            padding: 4rem 4%;
            text-align: center;
            border-top: 1px solid #0d0d0d;
            color: var(--text-muted);
            font-size: 0.8rem;
            letter-spacing: 1px;
            text-transform: uppercase;
        }
    </style>
</head>
<body>

    <!-- LIGHTBOX MODAL -->
    <div class="lightbox" id="lightbox">
        <button class="lightbox-close" id="lightbox-close">&times;</button>
        <img src="" alt="Enlarged Showcase" class="lightbox-content" id="lightbox-img">
    </div>

    <!-- NAVIGATION -->
    <nav>
        <a href="#" class="logo">Auteur<span>.</span></a>
        <ul class="nav-links">
            <li><a href="#films">Films</a></li>
            <li><a href="#photography">Frames</a></li>
            <li><a href="#about">Manifesto</a></li>
        </ul>
    </nav>

    <!-- HERO SECTION -->
    <header class="hero">
        <h1 class="hero-title">Shadows & <em>Celluloid</em></h1>
        <p class="hero-subtitle">Cinematography & Visual Direction</p>
        <a href="#films" class="cta-btn">Enter the Realm</a>
    </header>

    <!-- SHORT FILMS SECTION -->
    <section id="films">
        <h2 class="section-title reveal">Short Films</h2>
        <div class="video-grid">
            
            <!-- Video Container 1 -->
            <div class="video-container reveal">
                <div class="video-wrapper">
                    <!-- Replace 'dQw4w9WgXcQ' with your actual YouTube video IDs -->
                    <iframe src="https://www.youtube.com/embed/dQw4w9WgXcQ?rel=0" title="Short Film 1" allowfullscreen></iframe>
                </div>
                <div class="video-meta">
                    <div class="video-info">
                        <h3>The Midnight Monologue</h3>
                        <p>Director of Photography & Editor — 4K Narrative Short (2025)</p>
                    </div>
                </div>
            </div>

            <!-- Video Container 2 -->
            <div class="video-container reveal">
                <div class="video-wrapper">
                    <iframe src="https://www.youtube.com/embed/dQw4w9WgXcQ?rel=0" title="Short Film 2" allowfullscreen></iframe>
                </div>
                <div class="video-meta">
                    <div class="video-info">
                        <h3>Neon Bleed</h3>
                        <p>Director & Colorist — Cyber-Noir Experimental (2026)</p>
                    </div>
                </div>
            </div>

        </div>
    </section>

    <!-- PHOTOGRAPHY SECTION -->
    <section id="photography">
        <h2 class="section-title reveal">Captured Frames</h2>
        <div class="gallery-grid">
            
            <!-- Gallery Item 1 -->
            <div class="gallery-item reveal">
                <!-- Using premium high-contrast placeholder images from Unsplash -->
                <img src="https://images.unsplash.com/photo-1509281373149-e957c6296406?auto=format&fit=crop&w=800&q=80" alt="Cinematic Frame 1">
                <div class="gallery-overlay">
                    <h4>Chasing Carousels</h4>
                </div>
            </div>

            <!-- Gallery Item 2 -->
            <div class="gallery-item reveal">
                <img src="https://images.unsplash.com/photo-1536440136628-849c177e76a1?auto=format&fit=crop&w=800&q=80" alt="Cinematic Frame 2">
                <div class="gallery-overlay">
                    <h4>The Corridor</h4>
                </div>
            </div>

            <!-- Gallery Item 3 -->
            <div class="gallery-item reveal">
                <img src="https://images.unsplash.com/photo-1485846234645-a62644f84728?auto=format&fit=crop&w=800&q=80" alt="Cinematic Frame 3">
                <div class="gallery-overlay">
                    <h4>Ashen Light</h4>
                </div>
            </div>

            <!-- Gallery Item 4 -->
            <div class="gallery-item reveal">
                <img src="https://images.unsplash.com/photo-1507679799987-c73779587ccf?auto=format&fit=crop&w=800&q=80" alt="Cinematic Frame 4">
                <div class="gallery-overlay">
                    <h4>Anonymity</h4>
                </div>
            </div>

        </div>
    </section>

    <!-- ABOUT / BIO SECTION -->
    <section id="about">
        <h2 class="section-title reveal">The Manifesto</h2>
        <div class="about-layout reveal">
            <div class="bio-text">
                I capture the stories told in the dark. I believe beauty exists where light fractures, preferring <span>high-contrast realities</span> and a subtle touch of atmospheric tension. My work is built for those who understand that the villain is often just an uncompromised visionary.
            </div>
            <div class="bio-details">
                <div class="detail-item">
                    <h5>Weapon of Choice</h5>
                    <p>Arri Alexa Mini LF & Vintage Anamorphic Glass</p>
                </div>
                <div class="detail-item">
                    <h5>Location Base</h5>
                    <p>Available for global assignments.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- FOOTER -->
    <footer>
        &copy; 2026 Auteur. Engineered with malicious compliance.
    </footer>

    <!-- --- JAVASCRIPT --- -->
    <script>
        document.addEventListener('DOMContentLoaded', () => {
            
            // 1. Intersection Observer for Smooth Scroll Reveal
            const revealElements = document.querySelectorAll('.reveal');
            
            const revealCallback = (entries, observer) => {
                entries.forEach(entry => {
                    if (entry.isIntersecting) {
                        entry.target.classList.add('active');
                        // Stop observing once revealed to preserve processing power
                        observer.unobserve(entry.target);
                    }
                });
            };

            const revealObserver = new IntersectionObserver(revealCallback, {
                root: null,
                threshold: 0.1,
                rootMargin: '0px 0px -50px 0px'
            });

            revealElements.forEach(element => revealObserver.observe(element));

            // 2. Custom Lightbox Functionality
            const lightbox = document.getElementById('lightbox');
            const lightboxImg = document.getElementById('lightbox-img');
            const lightboxClose = document.getElementById('lightbox-close');
            const galleryItems = document.querySelectorAll('.gallery-item');

            galleryItems.forEach(item => {
                item.addEventListener('click', () => {
                    const imgSrc = item.querySelector('img').src;
                    const imgAlt = item.querySelector('img').alt;
                    
                    lightboxImg.src = imgSrc;
                    lightboxImg.alt = imgAlt;
                    lightbox.classList.add('active');
                    document.body.style.overflow = 'hidden'; // Lock background scroll
                });
            });

            const closeLightbox = () => {
                lightbox.classList.remove('active');
                document.body.style.overflow = ''; // Unlock background scroll
                setTimeout(() => { lightboxImg.src = ''; }, 400); // Clear image asset link
            };

            lightboxClose.addEventListener('click', closeLightbox);
            
            // Close Lightbox when clicking outside the frame
            lightbox.addEventListener('click', (e) => {
                if (e.target === lightbox) {
                    closeLightbox();
                }
            });

            // Accessibility: Close via Escape Key
            document.addEventListener('keydown', (e) => {
                if (e.key === 'Escape' && lightbox.classList.contains('active')) {
                    closeLightbox();
                }
            });
        });
    </script>
    (function () {
  'use strict';

  const cursorContainer = document.getElementById('custom-cursor');
  const core            = document.getElementById('cursor-core');
  const aura            = document.getElementById('cursor-aura');

  let targetX = -200, targetY = -200;
  let coreX   = -200, coreY   = -200;
  let auraX   = -200, auraY   = -200;

  const LERP_FACTOR   = 0.11; // আভা কত স্মুথলি ফলো করবে (কম হলে বেশি ল্যাগ/স্মুথ হবে)
  const LERP_EPSILON  = 0.05;

  let  isHovering     = false;
  let  rafId          = null;
  let  isTouching     = false;
  let  touchFadeTimer = null;

  /* তোমার ওয়েবসাইটের ইন্টারঅ্যাক্টিভ এলিমেন্টগুলোর সিলেক্টর (প্রয়োজন অনুযায়ী এখানে ক্লাস বা ট্যাগ যোগ করবে) */
  const INTERACTIVE = 'a, button, .film-card, [role="button"], input, label, select, textarea';

  function lerp(a, b, t) { return a + (b - a) * t; }

  function showCursor() {
    cursorContainer.style.opacity = '1';
    cursorContainer.classList.remove('touch-hidden');
  }
  function hideCursor() { cursorContainer.style.opacity = '0'; }

  function setHover(active) {
    if (active === isHovering) return;
    isHovering = active;
    if (active) {
      core.classList.add('is-hovering');
      aura.classList.add('is-hovering');
    } else {
      core.classList.remove('is-hovering');
      aura.classList.remove('is-hovering');
    }
  }

  function tick() {
    rafId = requestAnimationFrame(tick);
    coreX = targetX;
    coreY = targetY;

    const dx = targetX - auraX;
    const dy = targetY - auraY;

    if (Math.abs(dx) > LERP_EPSILON || Math.abs(dy) > LERP_EPSILON) {
      auraX = lerp(auraX, targetX, LERP_FACTOR);
      auraY = lerp(auraY, targetY, LERP_FACTOR);
    } else {
      auraX = targetX;
      auraY = targetY;
    }

    core.style.transform = `translate3d(calc(${coreX}px - 50%), calc(${coreY}px - 50%), 0) rotate(45deg)`;
    core.style.webkitTransform = core.style.transform;

    aura.style.transform = isHovering
        ? `translate3d(calc(${auraX}px - 50%), calc(${auraY}px - 50%), 0) scale(1.85)`
        : `translate3d(calc(${auraX}px - 50%), calc(${auraY}px - 50%), 0) scale(1)`;
    aura.style.webkitTransform = aura.style.transform;
  }

  document.addEventListener('mousemove', function (e) {
    if (isTouching) return;
    targetX = e.clientX;
    targetY = e.clientY;
    showCursor();
  }, { passive: true });

  document.addEventListener('mouseover', function (e) {
    if (e.target.closest(INTERACTIVE)) setHover(true);
  }, { passive: true });

  document.addEventListener('mouseout', function (e) {
    if (e.target.closest(INTERACTIVE)) setHover(false);
  }, { passive: true });

  document.addEventListener('mouseleave', function () {
    hideCursor();
    setHover(false);
  }, { passive: true });

  document.addEventListener('mouseenter', function () { showCursor(); }, { passive: true });

  function getTouch(e) {
    return e.touches && e.touches.length > 0
      ? e.touches[0]
      : (e.changedTouches && e.changedTouches.length > 0 ? e.changedTouches[0] : null);
  }

  document.addEventListener('touchstart', function (e) {
    clearTimeout(touchFadeTimer);
    isTouching = true;
    const t = getTouch(e);
    if (!t) return;
    targetX = t.clientX; targetY = t.clientY;
    auraX = targetX; auraY = targetY;
    showCursor();
    const el = document.elementFromPoint(t.clientX, t.clientY);
    setHover(el && el.closest(INTERACTIVE) ? true : false);
  }, { passive: true });

  document.addEventListener('touchmove', function (e) {
    const t = getTouch(e);
    if (!t) return;
    targetX = t.clientX; targetY = t.clientY;
    showCursor();
    const el = document.elementFromPoint(t.clientX, t.clientY);
    setHover(el && el.closest(INTERACTIVE) ? true : false);
  }, { passive: true });

  document.addEventListener('touchend', function () {
    isTouching = false; setHover(false);
    clearTimeout(touchFadeTimer);
    touchFadeTimer = setTimeout(function () { hideCursor(); }, 520);
  }, { passive: true });

  document.addEventListener('touchcancel', function () {
    isTouching = false; setHover(false);
    clearTimeout(touchFadeTimer); hideCursor();
  }, { passive: true });

  let scrollTimer = null;
  window.addEventListener('scroll', function () {
    if (isTouching) return;
    hideCursor();
    clearTimeout(scrollTimer);
    scrollTimer = setTimeout(showCursor, 200);
  }, { passive: true });

  tick();
  hideCursor();
})();

</body>
</html>
# 1
