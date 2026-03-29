# La Nonna Trattoria — Complete Landing Page Specification
## Single-file, self-contained spec for Claude Code. No other documents needed.

---

# PART 1: BRAND MANUAL CONTEXT

## Brand Identity

**Name:** La Nonna Trattoria (est. 1962)
**Type:** Authentic Italian restaurant
**Location:** C. Pedro Moreno 1567, Col. Americana, Lafayette, 44160 Guadalajara, Jal., Mexico
**Phone:** +52 33 1234 5678 (REPLACE with real number)
**Email:** info@lanonnatrattoria.com
**Website:** www.lanonnatrattoria.com

## Brand Story

"Nonna" means "grandmother" in Italian. The name represents heritage, generational knowledge, and authentic home-style cooking. The brand evokes nostalgia, warmth, and comfort. More than just a restaurant — it's a place where family, love, and the joy of sharing are deeply ingrained. Three generations of family tradition since 1962.

**Core values:** Authenticity, Warmth, Family, Tradition, Passion
**Tone of voice:** Warm, inviting, elegant but never pretentious. Like a grandmother welcoming you home.
**Tagline:** "Authentic Italian Cuisine Since 1962"

## Brand Color Palette

| Name | Hex | RGB | CMYK | Pantone | Usage |
|------|-----|-----|------|---------|-------|
| Rojo (primary) | `#980E1E` | R152 G14 B30 | C0 M93 Y85 K22 | 18-1664 TCX Fiery Red | Headings, buttons, accents, logo |
| Bei / Beige | `#EAE1D6` | R234 G225 B214 | C0 M4 Y9 K8 | 12-1306 TCX Nova Scotia | Backgrounds, cards, section fills |
| Black | `#000000` | R0 G0 B0 | C0 M0 Y0 K100 | 19-3911 TCX Black Beauty | Body text, dark backgrounds |

## Brand Typography (from manual)

| Font | Role | Closest Google Font equivalent |
|------|------|-------------------------------|
| The Nautigal | Script / decorative (logo text, brand name) | Dancing Script |
| Helvetica World | Primary body / UI text | Inter |
| BlindDate | Secondary accent | Playfair Display (serif, elegant) |

## Logo

The logo is an illustration of a classic Italian trattoria storefront with a striped awning, showing "La Nonna" above in script, "est 1962" on the sides, and "Trattoria" below. It exists in these variants:
- Full color (rojo on beige)
- Monochrome black (on white/beige backgrounds)
- White/beige (on rojo or dark backgrounds)
- Icon only (storefront without text, for small sizes)

**Logo minimum sizes:** 20mm x 8mm (text only), 5mm x 7mm (icon only), 10mm x 15mm (full logo)
**Clear space:** 1x unit on all sides, 4x unit between logo edge and content

## Brand Icons (from manual)

The brand uses hand-drawn style icons in rojo (`#980E1E`) for:
- Vegan: leaf/V symbol
- Spicy: chili pepper
- Contains alcohol: wine bottle
- Kitchen, Bar, Bathrooms, Emergency Exit, Livingroom, Bedroom (for wayfinding)

## Services

- Dine-in (walk-ins welcome, reservations for groups 6+)
- Takeout (order via WhatsApp)
- NO delivery, NO catering currently

---

# PART 2: PROJECT OVERVIEW

## What to Build

A **single-page responsive landing page** in ONE `index.html` file. Premium, cinematic, animated — inspired by the Elegencia restaurant template. All visible copy in **English**.

**Conversion goals (in priority order):**
1. Order via WhatsApp (primary CTA)
2. Visit the restaurant (secondary CTA)

**Sections (in page order):**
1. Preloader
2. Fixed header with fullscreen navigation overlay
3. Hero (Swiper slider, full viewport)
4. About Us
5. Menu (list view with hover images)
6. Order (WhatsApp + directions)
7. FAQ (accordion)
8. Footer
9. Floating social bar (fixed position)

---

# PART 3: TECH STACK

## Libraries & CDN URLs

Load in this exact order:

### HEAD (CSS)
```html
<!-- Preconnect -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>

<!-- Google Fonts -->
<link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@400;700&family=Inter:wght@300;400;500;600&family=Playfair+Display:ital,wght@0,400;0,500;0,600;0,700;1,400;1,500&display=swap" rel="stylesheet">

<!-- Bootstrap 5.3 CSS -->
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet">

<!-- Bootstrap Icons -->
<link href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.3/font/bootstrap-icons.min.css" rel="stylesheet">

<!-- Swiper CSS -->
<link href="https://cdnjs.cloudflare.com/ajax/libs/Swiper/11.0.5/swiper-bundle.min.css" rel="stylesheet">
```

### END OF BODY (JS)
```html
<!-- Bootstrap JS -->
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"></script>

<!-- Swiper JS -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/Swiper/11.0.5/swiper-bundle.min.js"></script>

<!-- GSAP Core -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/gsap.min.js"></script>

<!-- GSAP ScrollTrigger -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/ScrollTrigger.min.js"></script>

<!-- GSAP ScrollToPlugin -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/ScrollToPlugin.min.js"></script>

<!-- Lenis (smooth scroll — free alternative to ScrollSmoother) -->
<script src="https://unpkg.com/lenis@1.1.18/dist/lenis.min.js"></script>

<!-- Custom JS (inline in the file) -->
<script> /* ALL custom JS here */ </script>
```

**NOTE:** Do NOT use GSAP ScrollSmoother or SplitText (they are premium/paid plugins). Use Lenis for smooth scroll and manual JS text splitting instead.

---

# PART 4: DESIGN SYSTEM

## CSS Custom Properties

```css
:root {
  /* ===== BRAND COLORS ===== */
  --nonna-rojo: #980E1E;
  --nonna-rojo-dark: #7A0B18;
  --nonna-rojo-light: rgba(152, 14, 30, 0.08);
  --nonna-rojo-medium: rgba(152, 14, 30, 0.15);
  --nonna-beige: #EAE1D6;
  --nonna-beige-dark: #D4CCBF;
  --nonna-beige-light: #F5F0E8;
  --nonna-black: #1A1A1A;
  --nonna-white: #FFFFFF;

  /* ===== TEXT COLORS ===== */
  --nonna-text: #1A1A1A;
  --nonna-text-muted: #6B6B6B;
  --nonna-text-light: #999999;

  /* ===== SOCIAL COLORS ===== */
  --nonna-whatsapp: #25D366;
  --nonna-whatsapp-dark: #1DA851;
  --nonna-facebook: #1877F2;
  --nonna-tiktok: #000000;
  --nonna-instagram: #E4405F;

  /* ===== SHADOWS ===== */
  --shadow-soft: 0 4px 20px rgba(0, 0, 0, 0.06);
  --shadow-medium: 0 8px 32px rgba(0, 0, 0, 0.10);
  --shadow-navbar: 0 2px 16px rgba(0, 0, 0, 0.08);
  --shadow-card-hover: 0 12px 40px rgba(152, 14, 30, 0.12);

  /* ===== TRANSITIONS ===== */
  --transition-fast: 0.2s cubic-bezier(0.4, 0, 0.2, 1);
  --transition-smooth: 0.4s cubic-bezier(0.4, 0, 0.2, 1);
  --transition-spring: 0.6s cubic-bezier(0.34, 1.56, 0.64, 1);

  /* ===== BORDER RADIUS ===== */
  --radius-sm: 8px;
  --radius-md: 12px;
  --radius-lg: 16px;
  --radius-xl: 24px;
  --radius-full: 50px;
}
```

## Global CSS

```css
* { box-sizing: border-box; }

html {
  scroll-padding-top: 80px;
}

body {
  font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
  font-size: 16px;
  line-height: 1.7;
  color: var(--nonna-text);
  background: var(--nonna-white);
  overflow-x: hidden;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

h1, h2, h3, h4 {
  font-family: 'Playfair Display', Georgia, serif;
  line-height: 1.2;
}

.brand-script {
  font-family: 'Dancing Script', cursive;
}

img {
  max-width: 100%;
  height: auto;
}

a {
  text-decoration: none;
  color: inherit;
  transition: var(--transition-fast);
}

/* Reduced motion support */
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
    scroll-behavior: auto !important;
  }
}
```

## Typography Scale

| Element | Font Family | Desktop Size | Mobile Size | Weight | Color | Extra |
|---------|------------|-------------|-------------|--------|-------|-------|
| `.hero-brand` | Dancing Script | 72px | 44px | 700 | --nonna-beige | — |
| `h2` section headings | Playfair Display | 52px | 34px | 700 | --nonna-rojo | — |
| `.section-eyebrow` | Inter | 13px | 12px | 600 | --nonna-rojo | uppercase, letter-spacing: 3px |
| `.section-subtitle` | Playfair Display | 20px | 17px | 400 | --nonna-text-muted | italic |
| `body / p` | Inter | 16px | 15px | 400 | --nonna-text | line-height: 1.7 |
| `.menu-item-name` | Playfair Display | 20px | 17px | 600 | --nonna-text | — |
| `.menu-price` | Inter | 18px | 16px | 700 | --nonna-rojo | — |
| `.menu-desc` | Inter | 14px | 13px | 400 | --nonna-text-muted | — |
| `.btn` text | Inter | 16px | 14px | 600 | varies | — |
| `.nav-fullscreen-link` | Playfair Display | 48px | 32px | 500 | --nonna-beige | — |
| `small, caption, .text-sm` | Inter | 14px | 13px | 400 | --nonna-text-muted | — |

## Button Styles

### Primary (solid rojo)
```css
.btn-nonna-primary {
  background: var(--nonna-rojo);
  color: var(--nonna-beige);
  border: none;
  padding: 14px 32px;
  border-radius: var(--radius-sm);
  font-family: 'Inter', sans-serif;
  font-size: 16px;
  font-weight: 600;
  cursor: pointer;
  transition: var(--transition-smooth);
  display: inline-flex;
  align-items: center;
  gap: 8px;
}
.btn-nonna-primary:hover {
  background: var(--nonna-rojo-dark);
  transform: translateY(-2px);
  box-shadow: var(--shadow-medium);
}
```

### Secondary (outline)
```css
.btn-nonna-outline {
  background: transparent;
  color: var(--nonna-rojo);
  border: 2px solid var(--nonna-rojo);
  padding: 12px 28px;
  border-radius: var(--radius-sm);
  font-family: 'Inter', sans-serif;
  font-size: 16px;
  font-weight: 600;
  cursor: pointer;
  transition: var(--transition-smooth);
}
.btn-nonna-outline:hover {
  background: var(--nonna-rojo);
  color: var(--nonna-beige);
}
```

### Hero outline (for dark backgrounds)
```css
.btn-nonna-hero-outline {
  background: rgba(234, 225, 214, 0.1);
  color: var(--nonna-beige);
  border: 1.5px solid rgba(234, 225, 214, 0.5);
  padding: 14px 32px;
  border-radius: var(--radius-sm);
  font-family: 'Inter', sans-serif;
  font-size: 16px;
  font-weight: 600;
  cursor: pointer;
  transition: var(--transition-smooth);
}
.btn-nonna-hero-outline:hover {
  background: rgba(234, 225, 214, 0.2);
  border-color: var(--nonna-beige);
}
```

### WhatsApp CTA
```css
.btn-whatsapp {
  background: var(--nonna-whatsapp);
  color: white;
  border: none;
  padding: 16px 40px;
  border-radius: var(--radius-sm);
  font-family: 'Inter', sans-serif;
  font-size: 18px;
  font-weight: 600;
  cursor: pointer;
  transition: var(--transition-smooth);
  display: inline-flex;
  align-items: center;
  gap: 10px;
  animation: pulseGlow 2s ease-in-out infinite;
}
.btn-whatsapp:hover {
  background: var(--nonna-whatsapp-dark);
  transform: scale(1.03);
}
@keyframes pulseGlow {
  0%, 100% { box-shadow: 0 0 0 0 rgba(37, 211, 102, 0.4); }
  50% { box-shadow: 0 0 0 14px rgba(37, 211, 102, 0); }
}
```

## Section Spacing

```css
.section-padding {
  padding: 100px 0; /* desktop */
}
@media (max-width: 768px) {
  .section-padding { padding: 56px 0; }
}
```

## Image Placeholder Style

For all placeholder images before the client adds real photos:

```css
.img-placeholder {
  border: 2px dashed var(--nonna-beige-dark);
  border-radius: var(--radius-md);
  background: var(--nonna-beige-light);
  display: flex;
  align-items: center;
  justify-content: center;
  color: var(--nonna-text-muted);
  font-size: 14px;
  font-style: italic;
  min-height: 200px;
  overflow: hidden;
}
```

---

# PART 5: HTML STRUCTURE

## Document Skeleton

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="description" content="La Nonna Trattoria — Authentic Italian cuisine in Guadalajara since 1962. Explore our menu and order via WhatsApp.">
  <meta name="keywords" content="Italian restaurant, Guadalajara, trattoria, pasta, pizza, authentic Italian food">
  <meta name="author" content="La Nonna Trattoria">

  <!-- Open Graph -->
  <meta property="og:title" content="La Nonna Trattoria — Authentic Italian Cuisine Since 1962">
  <meta property="og:description" content="Where every meal feels like coming home to Nonna's kitchen. Explore our menu and order via WhatsApp.">
  <meta property="og:type" content="website">
  <meta property="og:url" content="https://www.lanonnatrattoria.com">
  <!-- REPLACE: Add og:image URL -->
  <meta property="og:image" content="img/og-image.jpg">
  <meta property="og:locale" content="en_US">

  <title>La Nonna Trattoria — Authentic Italian Cuisine Since 1962 | Guadalajara</title>

  <!-- REPLACE: Add favicon -->
  <link rel="icon" href="img/favicon.ico" type="image/x-icon">

  <!-- CDN CSS (see Part 3 for URLs) -->
  <style>
    /* ALL custom CSS goes here (see Parts 4, 6-14 for all CSS) */
  </style>
</head>
<body>

  <!-- === PRELOADER === -->
  <div id="preloader"> ... </div>

  <!-- === FIXED HEADER + FULLSCREEN NAV === -->
  <header class="site-header" id="siteHeader"> ... </header>
  <div class="fullscreen-menu" id="fullscreenMenu"> ... </div>

  <!-- === SMOOTH SCROLL WRAPPER === -->
  <main id="smooth-wrapper">
    <div id="smooth-content">

      <!-- HERO -->
      <section class="hero-section" id="hero"> ... </section>

      <!-- ABOUT -->
      <section class="about-section section-padding" id="about"> ... </section>

      <!-- MENU -->
      <section class="menu-section section-padding" id="menu"> ... </section>

      <!-- ORDER -->
      <section class="order-section section-padding" id="order"> ... </section>

      <!-- FAQ -->
      <section class="faq-section section-padding" id="faq"> ... </section>

      <!-- FOOTER -->
      <footer class="site-footer" id="footer"> ... </footer>

    </div>
  </main>

  <!-- === FLOATING SOCIAL BAR (outside smooth wrapper) === -->
  <div class="floating-social" id="floatingSocial"> ... </div>

  <!-- === BACK TO TOP OVERLAY === -->
  <div class="back-to-top-overlay" id="backToTopOverlay"></div>

  <!-- CDN JS (see Part 3 for URLs) -->
  <script>
    /* ALL custom JS goes here (see Parts 6-14 for all JS) */
  </script>
</body>
</html>
```

---

# PART 6: PRELOADER

## HTML
```html
<div id="preloader">
  <div class="preloader-content">
    <span class="brand-script preloader-brand">La Nonna</span>
    <div class="preloader-bar"></div>
  </div>
  <div class="preloader-half preloader-left"></div>
  <div class="preloader-half preloader-right"></div>
</div>
```

## CSS
```css
#preloader {
  position: fixed;
  inset: 0;
  z-index: 99999;
  display: flex;
  align-items: center;
  justify-content: center;
}
.preloader-half {
  position: absolute;
  top: 0;
  width: 50%;
  height: 100%;
  background: var(--nonna-beige);
}
.preloader-left { left: 0; }
.preloader-right { right: 0; }
.preloader-content {
  position: relative;
  z-index: 1;
  text-align: center;
}
.preloader-brand {
  font-size: 40px;
  color: var(--nonna-rojo);
}
.preloader-bar {
  width: 60px;
  height: 2px;
  background: var(--nonna-rojo);
  margin: 16px auto 0;
  animation: preloaderPulse 1s ease-in-out infinite;
}
@keyframes preloaderPulse {
  0%, 100% { transform: scaleX(1); opacity: 1; }
  50% { transform: scaleX(2); opacity: 0.6; }
}
```

## JS
```javascript
function initPreloader() {
  window.addEventListener('load', () => {
    setTimeout(() => {
      const tl = gsap.timeline();
      tl.to('.preloader-content', { opacity: 0, y: -20, duration: 0.4, ease: 'power2.in' })
        .to('.preloader-left', { xPercent: -100, duration: 0.8, ease: 'expo.inOut' }, '-=0.1')
        .to('.preloader-right', { xPercent: 100, duration: 0.8, ease: 'expo.inOut' }, '<')
        .set('#preloader', { display: 'none' })
        .call(() => {
          // Trigger hero entrance animations after preloader
          initHeroAnimations();
        });
    }, 800);
  });
}
```

---

# PART 7: FIXED HEADER + FULLSCREEN NAVIGATION

## HTML
```html
<!-- Fixed Header Bar -->
<header class="site-header" id="siteHeader">
  <div class="container">
    <div class="header-inner">
      <!-- Brand -->
      <a href="#hero" class="header-brand brand-script">La Nonna</a>

      <!-- Center: Hamburger -->
      <button class="hamburger" id="hamburgerBtn" aria-label="Open menu" aria-expanded="false">
        <svg viewBox="0 0 24 16" width="28" height="18" class="hamburger-icon">
          <path class="ham-line ham-line-1" d="M0 1 L24 1" stroke="currentColor" stroke-width="1.5" fill="none"/>
          <path class="ham-line ham-line-2" d="M4 8 L20 8" stroke="currentColor" stroke-width="1.5" fill="none"/>
          <path class="ham-line ham-line-3" d="M0 15 L24 15" stroke="currentColor" stroke-width="1.5" fill="none"/>
        </svg>
        <span class="hamburger-label">Menu</span>
      </button>

      <!-- Right: Quick Order CTA -->
      <a href="https://wa.me/523312345678?text=Hello%20La%20Nonna!%20I%27d%20like%20to%20place%20an%20order.%20%F0%9F%8D%9D"
         class="header-order-btn" target="_blank" rel="noopener" aria-label="Order via WhatsApp">
        <i class="bi bi-whatsapp"></i>
        <span>Order</span>
      </a>
    </div>
  </div>
</header>

<!-- Fullscreen Menu Overlay -->
<div class="fullscreen-menu" id="fullscreenMenu" aria-hidden="true">
  <div class="fullscreen-menu-inner">
    <nav class="fullscreen-nav">
      <ul class="fullscreen-nav-list">
        <li class="nav-link-item" data-nav-img="img/nav-about.jpg">
          <a href="#about" class="fullscreen-link">About</a>
          <!-- REPLACE: image shown on hover (rec: 400x500px, restaurant interior) -->
          <img class="nav-hover-img" src="img/nav-about.jpg" alt="" aria-hidden="true" loading="lazy"/>
        </li>
        <li class="nav-link-item" data-nav-img="img/nav-menu.jpg">
          <a href="#menu" class="fullscreen-link">Menu</a>
          <!-- REPLACE: image shown on hover (rec: 400x500px, food close-up) -->
          <img class="nav-hover-img" src="img/nav-menu.jpg" alt="" aria-hidden="true" loading="lazy"/>
        </li>
        <li class="nav-link-item" data-nav-img="img/nav-order.jpg">
          <a href="#order" class="fullscreen-link">Order</a>
          <!-- REPLACE: image shown on hover (rec: 400x500px, takeout packaging) -->
          <img class="nav-hover-img" src="img/nav-order.jpg" alt="" aria-hidden="true" loading="lazy"/>
        </li>
        <li class="nav-link-item" data-nav-img="img/nav-faq.jpg">
          <a href="#faq" class="fullscreen-link">Q&A</a>
          <!-- REPLACE: image shown on hover (rec: 400x500px, cozy table scene) -->
          <img class="nav-hover-img" src="img/nav-faq.jpg" alt="" aria-hidden="true" loading="lazy"/>
        </li>
      </ul>
    </nav>

    <div class="fullscreen-menu-footer">
      <div class="fullscreen-social">
        <a href="#" target="_blank" rel="noopener" aria-label="Instagram"><i class="bi bi-instagram"></i></a>
        <!-- REPLACE: actual Instagram URL above -->
        <a href="#" target="_blank" rel="noopener" aria-label="Facebook"><i class="bi bi-facebook"></i></a>
        <!-- REPLACE: actual Facebook URL above -->
        <a href="#" target="_blank" rel="noopener" aria-label="TikTok"><i class="bi bi-tiktok"></i></a>
        <!-- REPLACE: actual TikTok URL above -->
        <a href="https://wa.me/523312345678" target="_blank" rel="noopener" aria-label="WhatsApp"><i class="bi bi-whatsapp"></i></a>
      </div>
      <div class="fullscreen-contact">
        <span>+52 33 1234 5678</span>
        <span>info@lanonnatrattoria.com</span>
      </div>
    </div>
  </div>
</div>
```

## CSS
```css
/* === HEADER === */
.site-header {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  padding: 20px 0;
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
}
.site-header.scrolled {
  background: rgba(234, 225, 214, 0.95);
  backdrop-filter: blur(12px);
  -webkit-backdrop-filter: blur(12px);
  padding: 12px 0;
  box-shadow: var(--shadow-navbar);
}
.header-inner {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.header-brand {
  font-size: 28px;
  color: var(--nonna-rojo);
  transition: var(--transition-smooth);
}
.hamburger {
  background: none;
  border: none;
  cursor: pointer;
  display: flex;
  align-items: center;
  gap: 8px;
  color: var(--nonna-rojo);
  padding: 8px;
  transition: var(--transition-smooth);
}
.hamburger-label {
  font-family: 'Inter', sans-serif;
  font-size: 14px;
  font-weight: 500;
  letter-spacing: 1px;
  text-transform: uppercase;
}
.hamburger-icon { transition: var(--transition-smooth); }
.header-order-btn {
  background: var(--nonna-whatsapp);
  color: white;
  padding: 8px 18px;
  border-radius: var(--radius-sm);
  font-size: 13px;
  font-weight: 600;
  display: flex;
  align-items: center;
  gap: 6px;
  transition: var(--transition-smooth);
}
.header-order-btn:hover {
  background: var(--nonna-whatsapp-dark);
  transform: translateY(-1px);
  color: white;
}

/* === FULLSCREEN MENU === */
.fullscreen-menu {
  position: fixed;
  inset: 0;
  background: var(--nonna-black);
  z-index: 999;
  height: 0;
  overflow: hidden;
  display: flex;
  align-items: center;
}
.fullscreen-menu-inner {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 24px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  min-height: 60vh;
}
.fullscreen-nav-list {
  list-style: none;
  padding: 0;
  margin: 0;
}
.nav-link-item {
  position: relative;
  border-bottom: 1px solid rgba(234, 225, 214, 0.08);
  padding: 16px 0;
}
.fullscreen-link {
  font-family: 'Playfair Display', serif;
  font-size: 48px;
  font-weight: 500;
  color: var(--nonna-beige);
  transition: var(--transition-smooth);
  display: inline-block;
}
.fullscreen-link:hover {
  color: var(--nonna-rojo);
  transform: translateX(16px);
}
.nav-hover-img {
  position: fixed;
  width: 300px;
  height: 380px;
  object-fit: cover;
  border-radius: var(--radius-md);
  pointer-events: none;
  opacity: 0;
  z-index: 1001;
  box-shadow: var(--shadow-medium);
  transition: opacity 0.3s ease;
}
.fullscreen-menu-footer {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-top: 48px;
  padding-top: 24px;
  border-top: 1px solid rgba(234, 225, 214, 0.08);
}
.fullscreen-social {
  display: flex;
  gap: 12px;
}
.fullscreen-social a {
  width: 40px;
  height: 40px;
  border: 1px solid rgba(234, 225, 214, 0.2);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  color: var(--nonna-beige);
  font-size: 16px;
  transition: var(--transition-smooth);
}
.fullscreen-social a:hover {
  background: var(--nonna-beige);
  color: var(--nonna-black);
  border-color: var(--nonna-beige);
  transform: translateY(-3px);
}
.fullscreen-contact {
  display: flex;
  flex-direction: column;
  align-items: flex-end;
  gap: 4px;
  font-size: 14px;
  color: rgba(234, 225, 214, 0.5);
}

/* Mobile fullscreen nav */
@media (max-width: 768px) {
  .fullscreen-link { font-size: 32px; }
  .nav-hover-img { display: none !important; }
  .fullscreen-menu-footer { flex-direction: column; align-items: center; gap: 16px; }
  .fullscreen-contact { align-items: center; }
  .hamburger-label { display: none; }
}
```

## JS
```javascript
function initNavigation() {
  const header = document.getElementById('siteHeader');
  const hamburger = document.getElementById('hamburgerBtn');
  const menu = document.getElementById('fullscreenMenu');
  const navLinks = menu.querySelectorAll('.fullscreen-link');
  const navItems = menu.querySelectorAll('.nav-link-item');

  // GSAP timeline for menu open/close
  const menuTl = gsap.timeline({ paused: true, reversed: true });
  menuTl
    .to(menu, { height: '100vh', duration: 0.5, ease: 'expo.inOut' })
    .fromTo(navItems,
      { opacity: 0, y: 40 },
      { opacity: 1, y: 0, stagger: 0.08, duration: 0.4, ease: 'power3.out' },
      '-=0.2'
    )
    .fromTo('.fullscreen-menu-footer',
      { opacity: 0, y: 20 },
      { opacity: 1, y: 0, duration: 0.4 },
      '-=0.2'
    );

  // Hamburger morph animation
  const hamTl = gsap.timeline({ paused: true, reversed: true });
  hamTl
    .to('.ham-line-1', { attr: { d: 'M4 1 L20 15' }, duration: 0.3, ease: 'power2.inOut' }, 0)
    .to('.ham-line-2', { opacity: 0, duration: 0.2 }, 0)
    .to('.ham-line-3', { attr: { d: 'M4 15 L20 1' }, duration: 0.3, ease: 'power2.inOut' }, 0);

  hamburger.addEventListener('click', () => {
    if (menuTl.reversed()) {
      menuTl.play();
      hamTl.play();
      hamburger.setAttribute('aria-expanded', 'true');
      menu.setAttribute('aria-hidden', 'false');
      document.body.style.overflow = 'hidden';
    } else {
      menuTl.reverse();
      hamTl.reverse();
      hamburger.setAttribute('aria-expanded', 'false');
      menu.setAttribute('aria-hidden', 'true');
      document.body.style.overflow = '';
    }
  });

  // Close on nav link click + smooth scroll
  navLinks.forEach(link => {
    link.addEventListener('click', (e) => {
      e.preventDefault();
      const target = link.getAttribute('href');
      menuTl.reverse();
      hamTl.reverse();
      document.body.style.overflow = '';
      hamburger.setAttribute('aria-expanded', 'false');
      menu.setAttribute('aria-hidden', 'true');
      setTimeout(() => {
        gsap.to(window, { scrollTo: target, duration: 1, ease: 'power3.inOut' });
      }, 500);
    });
  });

  // Hover images follow cursor (desktop only)
  if (window.innerWidth > 991) {
    navItems.forEach(item => {
      const img = item.querySelector('.nav-hover-img');
      if (!img) return;
      item.addEventListener('mousemove', (e) => {
        gsap.to(img, {
          opacity: 1,
          left: e.clientX + 30,
          top: e.clientY - 190,
          duration: 0.4,
          ease: 'power3.out'
        });
      });
      item.addEventListener('mouseleave', () => {
        gsap.to(img, { opacity: 0, duration: 0.3 });
      });
    });
  }

  // Navbar scroll transition
  ScrollTrigger.create({
    start: 'top -100',
    onEnter: () => header.classList.add('scrolled'),
    onLeaveBack: () => header.classList.remove('scrolled')
  });
}
```

---

# PART 8: HERO SECTION

## HTML
```html
<section class="hero-section" id="hero">
  <div class="swiper hero-swiper">
    <div class="swiper-wrapper">

      <!-- Slide 1 -->
      <div class="swiper-slide">
        <!-- REPLACE: hero background image 1 (rec: 1920x1080, restaurant exterior/interior) -->
        <div class="hero-bg" style="background-image: url('img/hero-1.jpg')"></div>
        <div class="hero-overlay"></div>
        <div class="hero-content">
          <span class="hero-eyebrow">EST. 1962 · GUADALAJARA</span>
          <h1 class="hero-brand brand-script anim-title-hero">La Nonna</h1>
          <p class="hero-subtitle-text">T R A T T O R I A</p>
          <p class="hero-tagline">Where every meal feels like coming home to Nonna's kitchen</p>
          <div class="hero-cta-group">
            <a href="#menu" class="btn-nonna-hero-outline">Explore Menu</a>
            <a href="https://wa.me/523312345678?text=Hello%20La%20Nonna!%20I%27d%20like%20to%20place%20an%20order.%20%F0%9F%8D%9D"
               class="btn-whatsapp" target="_blank" rel="noopener">
              <i class="bi bi-whatsapp"></i> Order Now
            </a>
          </div>
        </div>
      </div>

      <!-- Slide 2 -->
      <div class="swiper-slide">
        <!-- REPLACE: hero background image 2 (rec: 1920x1080, signature dish close-up) -->
        <div class="hero-bg" style="background-image: url('img/hero-2.jpg')"></div>
        <div class="hero-overlay"></div>
        <div class="hero-content">
          <span class="hero-eyebrow">AUTHENTIC ITALIAN CUISINE</span>
          <h1 class="hero-brand brand-script">La Nonna</h1>
          <p class="hero-subtitle-text">T R A T T O R I A</p>
          <p class="hero-tagline">Recipes passed down through three generations of family</p>
          <div class="hero-cta-group">
            <a href="#about" class="btn-nonna-hero-outline">Our Story</a>
            <a href="#menu" class="btn-nonna-hero-outline">View Menu</a>
          </div>
        </div>
      </div>

      <!-- Slide 3 -->
      <div class="swiper-slide">
        <!-- REPLACE: hero background image 3 (rec: 1920x1080, family dining or chef cooking) -->
        <div class="hero-bg" style="background-image: url('img/hero-3.jpg')"></div>
        <div class="hero-overlay"></div>
        <div class="hero-content">
          <span class="hero-eyebrow">MORE THAN A RESTAURANT</span>
          <h1 class="hero-brand brand-script">La Nonna</h1>
          <p class="hero-subtitle-text">T R A T T O R I A</p>
          <p class="hero-tagline">A place where family, flavor, and tradition come together</p>
          <div class="hero-cta-group">
            <a href="https://wa.me/523312345678?text=Hello%20La%20Nonna!%20I%27d%20like%20to%20place%20an%20order.%20%F0%9F%8D%9D"
               class="btn-whatsapp" target="_blank" rel="noopener">
              <i class="bi bi-whatsapp"></i> Order via WhatsApp
            </a>
          </div>
        </div>
      </div>

    </div>

    <!-- Custom navigation -->
    <div class="hero-nav-controls">
      <button class="hero-arrow hero-prev" aria-label="Previous slide">
        <i class="bi bi-chevron-left"></i>
      </button>
      <div class="hero-counter">
        <span class="hero-current">01</span>
        <span class="hero-sep">/</span>
        <span class="hero-total">03</span>
      </div>
      <button class="hero-arrow hero-next" aria-label="Next slide">
        <i class="bi bi-chevron-right"></i>
      </button>
    </div>

    <!-- Scroll indicator -->
    <div class="scroll-indicator">
      <span>Scroll</span>
      <div class="scroll-line"></div>
    </div>
  </div>
</section>
```

## CSS
```css
.hero-section {
  height: 100vh;
  position: relative;
  overflow: hidden;
}
.hero-bg {
  position: absolute;
  inset: 0;
  background-size: cover;
  background-position: center;
  transition: transform 6s ease;
}
.swiper-slide-active .hero-bg {
  transform: scale(1.08);
}
.hero-overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(180deg, rgba(26,26,26,0.25) 0%, rgba(26,26,26,0.55) 100%);
}
.hero-content {
  position: relative;
  z-index: 2;
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: center;
  color: var(--nonna-beige);
  padding: 0 24px;
}
.hero-eyebrow {
  font-family: 'Inter', sans-serif;
  font-size: 13px;
  font-weight: 500;
  letter-spacing: 4px;
  text-transform: uppercase;
  opacity: 0.75;
  margin-bottom: 12px;
}
.hero-brand {
  font-size: 72px;
  color: var(--nonna-beige);
  margin: 0;
  line-height: 1;
}
.hero-subtitle-text {
  font-family: 'Inter', sans-serif;
  font-size: 16px;
  letter-spacing: 8px;
  opacity: 0.6;
  margin: 10px 0 0;
}
.hero-tagline {
  font-family: 'Playfair Display', serif;
  font-style: italic;
  font-size: 20px;
  opacity: 0.85;
  max-width: 500px;
  margin: 24px auto 32px;
  line-height: 1.5;
}
.hero-cta-group {
  display: flex;
  gap: 16px;
  flex-wrap: wrap;
  justify-content: center;
}

/* Hero controls */
.hero-nav-controls {
  position: absolute;
  bottom: 80px;
  left: 50%;
  transform: translateX(-50%);
  z-index: 3;
  display: flex;
  align-items: center;
  gap: 24px;
}
.hero-arrow {
  background: none;
  border: 1px solid rgba(234,225,214,0.3);
  border-radius: 50%;
  width: 44px;
  height: 44px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: var(--nonna-beige);
  font-size: 18px;
  cursor: pointer;
  transition: var(--transition-smooth);
}
.hero-arrow:hover {
  background: rgba(234,225,214,0.15);
  border-color: rgba(234,225,214,0.6);
}
.hero-counter {
  font-family: 'Inter', sans-serif;
  font-size: 14px;
  color: rgba(234,225,214,0.7);
}
.hero-current { color: var(--nonna-beige); font-weight: 600; }
.hero-sep { margin: 0 4px; }

/* Scroll indicator */
.scroll-indicator {
  position: absolute;
  bottom: 24px;
  left: 50%;
  transform: translateX(-50%);
  z-index: 3;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 6px;
}
.scroll-indicator span {
  font-family: 'Inter', sans-serif;
  font-size: 10px;
  letter-spacing: 2px;
  text-transform: uppercase;
  color: rgba(234,225,214,0.5);
}
.scroll-line {
  width: 1px;
  height: 32px;
  background: rgba(234,225,214,0.2);
  position: relative;
  overflow: hidden;
}
.scroll-line::after {
  content: '';
  position: absolute;
  top: -100%;
  left: 0;
  width: 100%;
  height: 100%;
  background: var(--nonna-beige);
  animation: scrollLine 1.6s ease-in-out infinite;
}
@keyframes scrollLine {
  0% { top: -100%; }
  100% { top: 100%; }
}

/* Mobile hero */
@media (max-width: 768px) {
  .hero-brand { font-size: 44px; }
  .hero-tagline { font-size: 17px; }
  .hero-nav-controls { bottom: 64px; gap: 16px; }
  .hero-arrow { width: 36px; height: 36px; font-size: 14px; }
}
```

## JS
```javascript
function initHeroSwiper() {
  const heroSwiper = new Swiper('.hero-swiper', {
    loop: true,
    speed: 1200,
    autoplay: { delay: 5000, disableOnInteraction: false },
    effect: 'fade',
    fadeEffect: { crossFade: true },
    navigation: {
      nextEl: '.hero-next',
      prevEl: '.hero-prev'
    },
    on: {
      slideChange: function () {
        const current = this.realIndex + 1;
        document.querySelector('.hero-current').textContent = String(current).padStart(2, '0');
      }
    }
  });
}

function initHeroAnimations() {
  const tl = gsap.timeline({ defaults: { ease: 'power3.out' } });
  tl.from('.hero-eyebrow', { opacity: 0, y: 20, duration: 0.6 })
    .from('.hero-brand', { opacity: 0, scale: 0.85, duration: 0.8 }, '-=0.3')
    .from('.hero-subtitle-text', { opacity: 0, y: 15, duration: 0.5 }, '-=0.4')
    .from('.hero-tagline', { opacity: 0, y: 20, duration: 0.6 }, '-=0.3')
    .from('.hero-cta-group > *', { opacity: 0, y: 15, stagger: 0.15, duration: 0.5 }, '-=0.3')
    .from('.hero-nav-controls', { opacity: 0, duration: 0.5 }, '-=0.2')
    .from('.scroll-indicator', { opacity: 0, y: -10, duration: 0.5 }, '-=0.2');
}
```

---

# PART 9: ABOUT SECTION

## HTML
```html
<section class="about-section section-padding" id="about" style="background: var(--nonna-white);">
  <div class="container">
    <div class="row align-items-center g-5">

      <!-- Left: Text content -->
      <div class="col-lg-6">
        <span class="section-eyebrow" data-aos="fade-up">OUR STORY</span>
        <h2 class="anim-title" style="color: var(--nonna-rojo); margin-bottom: 24px;">A Tradition of Flavor Since 1962</h2>

        <p data-aos="fade-up" data-aos-delay="100">
          More than just an Italian restaurant, La Nonna Trattoria is a place that captures the essence of Italy's rich cultural heritage. Founded in 1962, our doors have been open for over six decades, welcoming families and friends to share in the joy of authentic Italian dining. Here, food is more than sustenance — it's a celebration of love, tradition, and togetherness.
        </p>

        <p data-aos="fade-up" data-aos-delay="200">
          We believe in doing things the Italian way: with passion, patience, and above all, heart. Every recipe has been passed down through generations, every ingredient is carefully selected, and every dish is prepared with the same care your grandmother would put into a Sunday meal.
        </p>

        <!-- Counters -->
        <div class="row g-3 my-4" data-aos="fade-up" data-aos-delay="300">
          <div class="col-4">
            <div class="counter-card">
              <span class="counter-number" data-target="60">0</span><span class="counter-suffix">+</span>
              <span class="counter-label">Years of tradition</span>
            </div>
          </div>
          <div class="col-4">
            <div class="counter-card">
              <span class="counter-number" data-target="35">0</span><span class="counter-suffix">+</span>
              <span class="counter-label">Signature dishes</span>
            </div>
          </div>
          <div class="col-4">
            <div class="counter-card">
              <span class="counter-number" data-target="3">0</span>
              <span class="counter-label">Generations</span>
            </div>
          </div>
        </div>

        <!-- Values -->
        <div class="about-values" data-aos="fade-up" data-aos-delay="400">
          <span class="value-pill">Authenticity</span>
          <span class="value-pill">Warmth</span>
          <span class="value-pill">Family</span>
          <span class="value-pill">Tradition</span>
          <span class="value-pill">Passion</span>
        </div>
      </div>

      <!-- Right: Photos -->
      <div class="col-lg-6">
        <div class="about-photos">
          <div class="img-reveal-container" data-aos="fade-left">
            <div class="img-reveal-overlay"></div>
            <!-- REPLACE: restaurant interior photo (rec: 600x400px) -->
            <img src="img/about-1.jpg" alt="La Nonna Trattoria interior" class="img-zoom-scroll" loading="lazy"/>
          </div>
          <div class="img-reveal-container" data-aos="fade-left" data-aos-delay="200">
            <div class="img-reveal-overlay"></div>
            <!-- REPLACE: food/kitchen photo (rec: 600x400px) -->
            <img src="img/about-2.jpg" alt="Traditional Italian cooking at La Nonna" class="img-zoom-scroll" loading="lazy"/>
          </div>
        </div>
      </div>
    </div>

    <!-- Quote -->
    <div class="about-quote" data-aos="fade-up">
      <hr class="anim-line quote-line">
      <blockquote>
        "Nonna means grandmother in Italian — representing heritage, generational knowledge, and the love poured into every recipe we serve."
      </blockquote>
    </div>
  </div>
</section>
```

## CSS
```css
.section-eyebrow {
  font-family: 'Inter', sans-serif;
  font-size: 13px;
  font-weight: 600;
  color: var(--nonna-rojo);
  letter-spacing: 3px;
  text-transform: uppercase;
  display: block;
  margin-bottom: 12px;
}
.counter-card {
  background: var(--nonna-beige);
  border-radius: var(--radius-md);
  padding: 20px 12px;
  text-align: center;
}
.counter-number {
  font-family: 'Playfair Display', serif;
  font-size: 40px;
  font-weight: 700;
  color: var(--nonna-rojo);
  display: inline;
}
.counter-suffix {
  font-family: 'Playfair Display', serif;
  font-size: 40px;
  font-weight: 700;
  color: var(--nonna-rojo);
}
.counter-label {
  display: block;
  font-size: 13px;
  color: var(--nonna-text-muted);
  margin-top: 4px;
}
.value-pill {
  display: inline-block;
  background: var(--nonna-beige);
  color: var(--nonna-rojo);
  padding: 8px 20px;
  border-radius: var(--radius-full);
  font-size: 14px;
  font-weight: 500;
  margin: 4px;
  transition: var(--transition-smooth);
}
.value-pill:hover {
  background: var(--nonna-rojo);
  color: var(--nonna-beige);
  transform: translateY(-2px);
}

/* Photos */
.about-photos {
  display: flex;
  flex-direction: column;
  gap: 16px;
}
.img-reveal-container {
  position: relative;
  overflow: hidden;
  border-radius: var(--radius-lg);
}
.img-reveal-container img {
  width: 100%;
  height: 280px;
  object-fit: cover;
  display: block;
}
.img-reveal-overlay {
  position: absolute;
  inset: 0;
  background: var(--nonna-beige);
  z-index: 2;
  transform-origin: right;
}

/* Quote */
.about-quote {
  text-align: center;
  margin-top: 64px;
  max-width: 700px;
  margin-left: auto;
  margin-right: auto;
}
.quote-line {
  width: 60px;
  height: 2px;
  background: var(--nonna-rojo);
  border: none;
  margin: 0 auto 24px;
  opacity: 1;
}
.about-quote blockquote {
  font-family: 'Playfair Display', serif;
  font-style: italic;
  font-size: 22px;
  color: var(--nonna-rojo);
  line-height: 1.6;
  margin: 0;
}

@media (max-width: 768px) {
  .counter-number, .counter-suffix { font-size: 28px; }
  .about-quote blockquote { font-size: 18px; }
  .img-reveal-container img { height: 200px; }
}
```

## JS
```javascript
function initAboutAnimations() {
  // Image reveal overlays
  document.querySelectorAll('.img-reveal-overlay').forEach(overlay => {
    gsap.to(overlay, {
      scrollTrigger: { trigger: overlay.parentElement, start: 'top 70%' },
      scaleX: 0,
      duration: 1.2,
      ease: 'expo.inOut'
    });
  });

  // Image zoom on scroll
  document.querySelectorAll('.img-zoom-scroll').forEach(img => {
    gsap.fromTo(img, { scale: 1 }, {
      scale: 1.1,
      scrollTrigger: { trigger: img, start: 'top 80%', end: 'bottom 20%', scrub: 1 },
      ease: 'none'
    });
  });

  // Counter count-up
  document.querySelectorAll('.counter-number').forEach(num => {
    const target = parseInt(num.getAttribute('data-target'));
    gsap.from(num, {
      scrollTrigger: { trigger: num, start: 'top 85%' },
      innerText: 0,
      duration: 2.5,
      ease: 'power1.out',
      snap: { innerText: 1 },
      onUpdate: function() {
        num.textContent = Math.round(parseFloat(num.textContent));
      }
    });
  });

  // Animated lines
  document.querySelectorAll('.anim-line').forEach(line => {
    gsap.fromTo(line, { width: '0px' }, {
      width: '60px',
      scrollTrigger: { trigger: line, start: 'top 85%' },
      duration: 1,
      ease: 'power2.out'
    });
  });
}
```

---

# PART 10: MENU SECTION

## HTML
```html
<section class="menu-section section-padding" id="menu" style="background: var(--nonna-beige);">
  <div class="container">
    <div class="text-center mb-5">
      <span class="section-eyebrow" data-aos="fade-up">SPECIAL SELECTION</span>
      <h2 class="anim-title" style="color: var(--nonna-rojo);">Our Menu</h2>
      <p class="section-subtitle" data-aos="fade-up" data-aos-delay="100" style="font-family: 'Playfair Display'; font-style: italic; color: var(--nonna-text-muted); font-size: 18px;">Crafted with love, served with tradition</p>
    </div>

    <!-- Category Tabs -->
    <div class="menu-tabs-wrapper" data-aos="fade-up" data-aos-delay="150">
      <div class="menu-tabs">
        <button class="menu-tab active" data-category="antipasti">Antipasti</button>
        <button class="menu-tab" data-category="pasta">Pasta</button>
        <button class="menu-tab" data-category="pizza">Pizza</button>
        <button class="menu-tab" data-category="dolci">Dolci</button>
        <button class="menu-tab" data-category="beverages">Beverages</button>
      </div>
    </div>

    <!-- Menu List Container -->
    <div class="menu-list-container">

      <!-- ===== ANTIPASTI ===== -->
      <div class="menu-category" data-category="antipasti">
        <h3 class="menu-category-title">Antipasti</h3>

        <div class="menu-list-item">
          <div class="menu-item-row">
            <h4 class="menu-item-name">Bruschetta al Pomodoro</h4>
            <span class="menu-tag tag-vegan" title="Vegan">V</span>
            <span class="menu-dots"></span>
            <span class="menu-price">$145</span>
            <button class="add-btn" onclick="toggleOrderItem('Bruschetta al Pomodoro', 145, this)">+ Add</button>
          </div>
          <p class="menu-desc">Grilled bread topped with fresh tomatoes, basil, garlic, and extra virgin olive oil</p>
          <!-- REPLACE: dish photo (rec: 300x300 square) -->
          <img class="menu-hover-img" src="img/menu/bruschetta.jpg" alt="" aria-hidden="true"/>
        </div>
        <hr class="menu-separator anim-line">

        <div class="menu-list-item">
          <div class="menu-item-row">
            <h4 class="menu-item-name">Carpaccio di Manzo</h4>
            <span class="menu-dots"></span>
            <span class="menu-price">$210</span>
            <button class="add-btn" onclick="toggleOrderItem('Carpaccio di Manzo', 210, this)">+ Add</button>
          </div>
          <p class="menu-desc">Thinly sliced raw beef with arugula, capers, shaved Parmigiano, and lemon dressing</p>
          <img class="menu-hover-img" src="img/menu/carpaccio.jpg" alt="" aria-hidden="true"/>
        </div>
        <hr class="menu-separator anim-line">

        <div class="menu-list-item">
          <div class="menu-item-row">
            <h4 class="menu-item-name">Calamari Fritti</h4>
            <span class="menu-dots"></span>
            <span class="menu-price">$185</span>
            <button class="add-btn" onclick="toggleOrderItem('Calamari Fritti', 185, this)">+ Add</button>
          </div>
          <p class="menu-desc">Crispy fried squid rings served with house-made lemon aioli</p>
          <img class="menu-hover-img" src="img/menu/calamari.jpg" alt="" aria-hidden="true"/>
        </div>
        <hr class="menu-separator anim-line">

        <div class="menu-list-item nonnas-pick">
          <div class="menu-item-row">
            <h4 class="menu-item-name">Burrata con Prosciutto</h4>
            <span class="menu-badge-pick">Nonna's pick</span>
            <span class="menu-dots"></span>
            <span class="menu-price">$235</span>
            <button class="add-btn" onclick="toggleOrderItem('Burrata con Prosciutto', 235, this)">+ Add</button>
          </div>
          <p class="menu-desc">Creamy burrata cheese with San Daniele prosciutto and roasted cherry tomatoes</p>
          <img class="menu-hover-img" src="img/menu/burrata.jpg" alt="" aria-hidden="true"/>
        </div>
        <hr class="menu-separator anim-line">

        <div class="menu-list-item">
          <div class="menu-item-row">
            <h4 class="menu-item-name">Caprese Salad</h4>
            <span class="menu-tag tag-vegan" title="Vegan option">V</span>
            <span class="menu-dots"></span>
            <span class="menu-price">$165</span>
            <button class="add-btn" onclick="toggleOrderItem('Caprese Salad', 165, this)">+ Add</button>
          </div>
          <p class="menu-desc">Fresh buffalo mozzarella, vine tomatoes, basil, and balsamic glaze</p>
          <img class="menu-hover-img" src="img/menu/caprese.jpg" alt="" aria-hidden="true"/>
        </div>
        <hr class="menu-separator anim-line">

        <div class="menu-list-item">
          <div class="menu-item-row">
            <h4 class="menu-item-name">Arancini Siciliani</h4>
            <span class="menu-dots"></span>
            <span class="menu-price">$155</span>
            <button class="add-btn" onclick="toggleOrderItem('Arancini Siciliani', 155, this)">+ Add</button>
          </div>
          <p class="menu-desc">Golden fried risotto balls stuffed with mozzarella and ragù</p>
          <img class="menu-hover-img" src="img/menu/arancini.jpg" alt="" aria-hidden="true"/>
        </div>
      </div>

      <!-- ===== PASTA ===== -->
      <div class="menu-category" data-category="pasta" style="display:none;">
        <h3 class="menu-category-title">Pasta</h3>

        <div class="menu-list-item">
          <div class="menu-item-row">
            <h4 class="menu-item-name">Spaghetti alla Carbonara</h4>
            <span class="menu-dots"></span>
            <span class="menu-price">$225</span>
            <button class="add-btn" onclick="toggleOrderItem('Spaghetti alla Carbonara', 225, this)">+ Add</button>
          </div>
          <p class="menu-desc">Classic Roman recipe with guanciale, pecorino, egg yolk, and black pepper</p>
          <img class="menu-hover-img" src="img/menu/carbonara.jpg" alt="" aria-hidden="true"/>
        </div>
        <hr class="menu-separator anim-line">

        <div class="menu-list-item">
          <div class="menu-item-row">
            <h4 class="menu-item-name">Penne all'Arrabbiata</h4>
            <span class="menu-tag tag-vegan" title="Vegan">V</span>
            <span class="menu-tag tag-spicy" title="Spicy">S</span>
            <span class="menu-dots"></span>
            <span class="menu-price">$195</span>
            <button class="add-btn" onclick="toggleOrderItem('Penne all Arrabbiata', 195, this)">+ Add</button>
          </div>
          <p class="menu-desc">Penne in a spicy tomato sauce with garlic and red chili flakes</p>
          <img class="menu-hover-img" src="img/menu/arrabbiata.jpg" alt="" aria-hidden="true"/>
        </div>
        <hr class="menu-separator anim-line">

        <div class="menu-list-item">
          <div class="menu-item-row">
            <h4 class="menu-item-name">Fettuccine Alfredo</h4>
            <span class="menu-dots"></span>
            <span class="menu-price">$215</span>
            <button class="add-btn" onclick="toggleOrderItem('Fettuccine Alfredo', 215, this)">+ Add</button>
          </div>
          <p class="menu-desc">Silky egg fettuccine in a rich Parmigiano cream sauce</p>
          <img class="menu-hover-img" src="img/menu/alfredo.jpg" alt="" aria-hidden="true"/>
        </div>
        <hr class="menu-separator anim-line">

        <div class="menu-list-item nonnas-pick">
          <div class="menu-item-row">
            <h4 class="menu-item-name">Lasagna della Nonna</h4>
            <span class="menu-badge-pick">Nonna's pick</span>
            <span class="menu-dots"></span>
            <span class="menu-price">$265</span>
            <button class="add-btn" onclick="toggleOrderItem('Lasagna della Nonna', 265, this)">+ Add</button>
          </div>
          <p class="menu-desc">Nonna's signature layered lasagna with Bolognese ragù, béchamel, and three cheeses</p>
          <img class="menu-hover-img" src="img/menu/lasagna.jpg" alt="" aria-hidden="true"/>
        </div>
        <hr class="menu-separator anim-line">

        <div class="menu-list-item">
          <div class="menu-item-row">
            <h4 class="menu-item-name">Ravioli di Ricotta e Spinaci</h4>
            <span class="menu-dots"></span>
            <span class="menu-price">$240</span>
            <button class="add-btn" onclick="toggleOrderItem('Ravioli di Ricotta e Spinaci', 240, this)">+ Add</button>
          </div>
          <p class="menu-desc">Handmade ravioli filled with ricotta and spinach in sage brown butter</p>
          <img class="menu-hover-img" src="img/menu/ravioli.jpg" alt="" aria-hidden="true"/>
        </div>
        <hr class="menu-separator anim-line">

        <div class="menu-list-item">
          <div class="menu-item-row">
            <h4 class="menu-item-name">Pappardelle al Ragù di Cinghiale</h4>
            <span class="menu-tag tag-alcohol" title="Contains alcohol">A</span>
            <span class="menu-dots"></span>
            <span class="menu-price">$280</span>
            <button class="add-btn" onclick="toggleOrderItem('Pappardelle al Ragu di Cinghiale', 280, this)">+ Add</button>
          </div>
          <p class="menu-desc">Wide ribbon pasta with slow-braised wild boar ragù</p>
          <img class="menu-hover-img" src="img/menu/pappardelle.jpg" alt="" aria-hidden="true"/>
        </div>
        <hr class="menu-separator anim-line">

        <div class="menu-list-item">
          <div class="menu-item-row">
            <h4 class="menu-item-name">Cacio e Pepe</h4>
            <span class="menu-dots"></span>
            <span class="menu-price">$205</span>
            <button class="add-btn" onclick="toggleOrderItem('Cacio e Pepe', 205, this)">+ Add</button>
          </div>
          <p class="menu-desc">Tonnarelli pasta in a pecorino and black pepper sauce — simple perfection</p>
          <img class="menu-hover-img" src="img/menu/cacio.jpg" alt="" aria-hidden="true"/>
        </div>
        <hr class="menu-separator anim-line">

        <div class="menu-list-item">
          <div class="menu-item-row">
            <h4 class="menu-item-name">Gnocchi alla Sorrentina</h4>
            <span class="menu-dots"></span>
            <span class="menu-price">$220</span>
            <button class="add-btn" onclick="toggleOrderItem('Gnocchi alla Sorrentina', 220, this)">+ Add</button>
          </div>
          <p class="menu-desc">Potato gnocchi baked with tomato sauce, mozzarella, and fresh basil</p>
          <img class="menu-hover-img" src="img/menu/gnocchi.jpg" alt="" aria-hidden="true"/>
        </div>
      </div>

      <!-- ===== PIZZA ===== -->
      <div class="menu-category" data-category="pizza" style="display:none;">
        <h3 class="menu-category-title">Pizza</h3>

        <div class="menu-list-item nonnas-pick">
          <div class="menu-item-row"><h4 class="menu-item-name">Margherita</h4><span class="menu-badge-pick">Nonna's pick</span><span class="menu-dots"></span><span class="menu-price">$195</span><button class="add-btn" onclick="toggleOrderItem('Pizza Margherita', 195, this)">+ Add</button></div>
          <p class="menu-desc">San Marzano tomato sauce, fior di latte mozzarella, fresh basil, extra virgin olive oil</p>
          <img class="menu-hover-img" src="img/menu/margherita.jpg" alt="" aria-hidden="true"/>
        </div><hr class="menu-separator anim-line">

        <div class="menu-list-item">
          <div class="menu-item-row"><h4 class="menu-item-name">Diavola</h4><span class="menu-tag tag-spicy">S</span><span class="menu-dots"></span><span class="menu-price">$225</span><button class="add-btn" onclick="toggleOrderItem('Pizza Diavola', 225, this)">+ Add</button></div>
          <p class="menu-desc">Tomato sauce, mozzarella, spicy salami calabrese, and Calabrian chili oil</p>
          <img class="menu-hover-img" src="img/menu/diavola.jpg" alt="" aria-hidden="true"/>
        </div><hr class="menu-separator anim-line">

        <div class="menu-list-item">
          <div class="menu-item-row"><h4 class="menu-item-name">Quattro Formaggi</h4><span class="menu-dots"></span><span class="menu-price">$235</span><button class="add-btn" onclick="toggleOrderItem('Pizza Quattro Formaggi', 235, this)">+ Add</button></div>
          <p class="menu-desc">Mozzarella, gorgonzola, fontina, and Parmigiano</p>
          <img class="menu-hover-img" src="img/menu/quattro.jpg" alt="" aria-hidden="true"/>
        </div><hr class="menu-separator anim-line">

        <div class="menu-list-item">
          <div class="menu-item-row"><h4 class="menu-item-name">Prosciutto e Rucola</h4><span class="menu-dots"></span><span class="menu-price">$245</span><button class="add-btn" onclick="toggleOrderItem('Pizza Prosciutto e Rucola', 245, this)">+ Add</button></div>
          <p class="menu-desc">Tomato, mozzarella, topped with prosciutto crudo and wild arugula</p>
          <img class="menu-hover-img" src="img/menu/prosciutto-pizza.jpg" alt="" aria-hidden="true"/>
        </div><hr class="menu-separator anim-line">

        <div class="menu-list-item">
          <div class="menu-item-row"><h4 class="menu-item-name">Funghi e Tartufo</h4><span class="menu-dots"></span><span class="menu-price">$265</span><button class="add-btn" onclick="toggleOrderItem('Pizza Funghi e Tartufo', 265, this)">+ Add</button></div>
          <p class="menu-desc">Mozzarella, mixed wild mushrooms, and truffle cream</p>
          <img class="menu-hover-img" src="img/menu/funghi.jpg" alt="" aria-hidden="true"/>
        </div><hr class="menu-separator anim-line">

        <div class="menu-list-item">
          <div class="menu-item-row"><h4 class="menu-item-name">Marinara</h4><span class="menu-tag tag-vegan">V</span><span class="menu-dots"></span><span class="menu-price">$165</span><button class="add-btn" onclick="toggleOrderItem('Pizza Marinara', 165, this)">+ Add</button></div>
          <p class="menu-desc">San Marzano tomatoes, garlic, oregano, olive oil — no cheese, pure tradition</p>
          <img class="menu-hover-img" src="img/menu/marinara.jpg" alt="" aria-hidden="true"/>
        </div>
      </div>

      <!-- ===== DOLCI ===== -->
      <div class="menu-category" data-category="dolci" style="display:none;">
        <h3 class="menu-category-title">Dolci</h3>

        <div class="menu-list-item nonnas-pick">
          <div class="menu-item-row"><h4 class="menu-item-name">Tiramisù della Casa</h4><span class="menu-badge-pick">Nonna's pick</span><span class="menu-tag tag-alcohol">A</span><span class="menu-dots"></span><span class="menu-price">$145</span><button class="add-btn" onclick="toggleOrderItem('Tiramisu della Casa', 145, this)">+ Add</button></div>
          <p class="menu-desc">Signature tiramisù with espresso-soaked ladyfingers, mascarpone cream, and cocoa</p>
          <img class="menu-hover-img" src="img/menu/tiramisu.jpg" alt="" aria-hidden="true"/>
        </div><hr class="menu-separator anim-line">

        <div class="menu-list-item">
          <div class="menu-item-row"><h4 class="menu-item-name">Panna Cotta ai Frutti di Bosco</h4><span class="menu-dots"></span><span class="menu-price">$135</span><button class="add-btn" onclick="toggleOrderItem('Panna Cotta', 135, this)">+ Add</button></div>
          <p class="menu-desc">Vanilla bean panna cotta with mixed berry compote</p>
          <img class="menu-hover-img" src="img/menu/pannacotta.jpg" alt="" aria-hidden="true"/>
        </div><hr class="menu-separator anim-line">

        <div class="menu-list-item">
          <div class="menu-item-row"><h4 class="menu-item-name">Cannoli Siciliani</h4><span class="menu-dots"></span><span class="menu-price">$125</span><button class="add-btn" onclick="toggleOrderItem('Cannoli Siciliani', 125, this)">+ Add</button></div>
          <p class="menu-desc">Crispy shells filled with sweet ricotta, chocolate chips, and candied orange peel</p>
          <img class="menu-hover-img" src="img/menu/cannoli.jpg" alt="" aria-hidden="true"/>
        </div><hr class="menu-separator anim-line">

        <div class="menu-list-item">
          <div class="menu-item-row"><h4 class="menu-item-name">Affogato al Caffè</h4><span class="menu-dots"></span><span class="menu-price">$110</span><button class="add-btn" onclick="toggleOrderItem('Affogato al Caffe', 110, this)">+ Add</button></div>
          <p class="menu-desc">Vanilla gelato drowned in a shot of hot espresso</p>
          <img class="menu-hover-img" src="img/menu/affogato.jpg" alt="" aria-hidden="true"/>
        </div><hr class="menu-separator anim-line">

        <div class="menu-list-item">
          <div class="menu-item-row"><h4 class="menu-item-name">Torta della Nonna</h4><span class="menu-dots"></span><span class="menu-price">$140</span><button class="add-btn" onclick="toggleOrderItem('Torta della Nonna', 140, this)">+ Add</button></div>
          <p class="menu-desc">Nonna's custard tart with pine nuts and powdered sugar</p>
          <img class="menu-hover-img" src="img/menu/torta.jpg" alt="" aria-hidden="true"/>
        </div>
      </div>

      <!-- ===== BEVERAGES ===== -->
      <div class="menu-category" data-category="beverages" style="display:none;">
        <h3 class="menu-category-title">Beverages</h3>

        <div class="menu-list-item">
          <div class="menu-item-row"><h4 class="menu-item-name">Limonata della Casa</h4><span class="menu-tag tag-vegan">V</span><span class="menu-dots"></span><span class="menu-price">$75</span><button class="add-btn" onclick="toggleOrderItem('Limonata della Casa', 75, this)">+ Add</button></div>
          <p class="menu-desc">House-made Italian lemonade with fresh mint</p>
          <img class="menu-hover-img" src="img/menu/limonata.jpg" alt="" aria-hidden="true"/>
        </div><hr class="menu-separator anim-line">

        <div class="menu-list-item">
          <div class="menu-item-row"><h4 class="menu-item-name">Espresso</h4><span class="menu-tag tag-vegan">V</span><span class="menu-dots"></span><span class="menu-price">$55</span><button class="add-btn" onclick="toggleOrderItem('Espresso', 55, this)">+ Add</button></div>
          <p class="menu-desc">Traditional Italian espresso</p>
          <img class="menu-hover-img" src="img/menu/espresso.jpg" alt="" aria-hidden="true"/>
        </div><hr class="menu-separator anim-line">

        <div class="menu-list-item">
          <div class="menu-item-row"><h4 class="menu-item-name">Cappuccino</h4><span class="menu-dots"></span><span class="menu-price">$70</span><button class="add-btn" onclick="toggleOrderItem('Cappuccino', 70, this)">+ Add</button></div>
          <p class="menu-desc">Espresso with steamed milk foam</p>
          <img class="menu-hover-img" src="img/menu/cappuccino.jpg" alt="" aria-hidden="true"/>
        </div><hr class="menu-separator anim-line">

        <div class="menu-list-item">
          <div class="menu-item-row"><h4 class="menu-item-name">San Pellegrino (500ml)</h4><span class="menu-tag tag-vegan">V</span><span class="menu-dots"></span><span class="menu-price">$65</span><button class="add-btn" onclick="toggleOrderItem('San Pellegrino', 65, this)">+ Add</button></div>
          <p class="menu-desc">Italian sparkling mineral water</p>
          <img class="menu-hover-img" src="img/menu/pellegrino.jpg" alt="" aria-hidden="true"/>
        </div><hr class="menu-separator anim-line">

        <div class="menu-list-item">
          <div class="menu-item-row"><h4 class="menu-item-name">Chianti Classico (glass)</h4><span class="menu-tag tag-alcohol">A</span><span class="menu-dots"></span><span class="menu-price">$155</span><button class="add-btn" onclick="toggleOrderItem('Chianti Classico', 155, this)">+ Add</button></div>
          <p class="menu-desc">Tuscan red wine, DOCG</p>
          <img class="menu-hover-img" src="img/menu/chianti.jpg" alt="" aria-hidden="true"/>
        </div><hr class="menu-separator anim-line">

        <div class="menu-list-item">
          <div class="menu-item-row"><h4 class="menu-item-name">Prosecco (glass)</h4><span class="menu-tag tag-alcohol">A</span><span class="menu-dots"></span><span class="menu-price">$145</span><button class="add-btn" onclick="toggleOrderItem('Prosecco', 145, this)">+ Add</button></div>
          <p class="menu-desc">Italian sparkling wine from Veneto</p>
          <img class="menu-hover-img" src="img/menu/prosecco.jpg" alt="" aria-hidden="true"/>
        </div><hr class="menu-separator anim-line">

        <div class="menu-list-item nonnas-pick">
          <div class="menu-item-row"><h4 class="menu-item-name">Aperol Spritz</h4><span class="menu-badge-pick">Nonna's pick</span><span class="menu-tag tag-alcohol">A</span><span class="menu-dots"></span><span class="menu-price">$175</span><button class="add-btn" onclick="toggleOrderItem('Aperol Spritz', 175, this)">+ Add</button></div>
          <p class="menu-desc">Aperol, prosecco, soda water — the classic Italian aperitivo</p>
          <img class="menu-hover-img" src="img/menu/aperol.jpg" alt="" aria-hidden="true"/>
        </div><hr class="menu-separator anim-line">

        <div class="menu-list-item">
          <div class="menu-item-row"><h4 class="menu-item-name">Negroni</h4><span class="menu-tag tag-alcohol">A</span><span class="menu-dots"></span><span class="menu-price">$185</span><button class="add-btn" onclick="toggleOrderItem('Negroni', 185, this)">+ Add</button></div>
          <p class="menu-desc">Gin, Campari, sweet vermouth — stirred, not shaken</p>
          <img class="menu-hover-img" src="img/menu/negroni.jpg" alt="" aria-hidden="true"/>
        </div>
      </div>

    </div>

    <!-- Tag legend -->
    <div class="menu-legend" data-aos="fade-up">
      <span><strong class="tag-vegan">V</strong> Vegan</span>
      <span><strong class="tag-spicy">S</strong> Spicy</span>
      <span><strong class="tag-alcohol">A</strong> Contains alcohol</span>
      <span class="menu-legend-note">All prices in MXN. Tax included.</span>
    </div>

  </div>
</section>
```

## CSS (Menu-specific)
```css
.menu-tabs-wrapper {
  overflow-x: auto;
  -webkit-overflow-scrolling: touch;
  padding-bottom: 8px;
  margin-bottom: 32px;
  scrollbar-width: none;
}
.menu-tabs-wrapper::-webkit-scrollbar { display: none; }
.menu-tabs {
  display: flex;
  gap: 8px;
  justify-content: center;
  white-space: nowrap;
}
.menu-tab {
  background: var(--nonna-white);
  color: var(--nonna-rojo);
  border: 1.5px solid var(--nonna-beige-dark);
  padding: 10px 24px;
  border-radius: var(--radius-full);
  font-family: 'Inter', sans-serif;
  font-size: 14px;
  font-weight: 500;
  cursor: pointer;
  transition: var(--transition-smooth);
}
.menu-tab.active {
  background: var(--nonna-rojo);
  color: var(--nonna-beige);
  border-color: var(--nonna-rojo);
}
.menu-tab:hover:not(.active) {
  background: var(--nonna-rojo-light);
  border-color: var(--nonna-rojo);
}

.menu-list-container {
  background: var(--nonna-white);
  border-radius: var(--radius-lg);
  padding: 32px;
  max-width: 900px;
  margin: 0 auto;
}
.menu-category-title {
  font-family: 'Inter', sans-serif;
  font-size: 13px;
  font-weight: 600;
  color: var(--nonna-rojo);
  letter-spacing: 3px;
  text-transform: uppercase;
  margin-bottom: 24px;
  padding-bottom: 12px;
  border-bottom: 1px solid var(--nonna-beige);
}
.menu-list-item {
  padding: 12px 0;
  position: relative;
  transition: var(--transition-fast);
}
.menu-list-item:hover { background: var(--nonna-beige-light); margin: 0 -16px; padding: 12px 16px; border-radius: var(--radius-sm); }
.menu-item-row {
  display: flex;
  align-items: baseline;
  gap: 8px;
}
.menu-item-name {
  font-family: 'Playfair Display', serif;
  font-size: 20px;
  font-weight: 600;
  color: var(--nonna-text);
  margin: 0;
  flex-shrink: 0;
}
.menu-dots {
  flex: 1;
  border-bottom: 1px dotted var(--nonna-beige-dark);
  position: relative;
  bottom: 4px;
  min-width: 20px;
}
.menu-price {
  font-family: 'Inter', sans-serif;
  font-size: 18px;
  font-weight: 700;
  color: var(--nonna-rojo);
  flex-shrink: 0;
}
.menu-desc {
  font-size: 14px;
  color: var(--nonna-text-muted);
  margin: 4px 0 0;
}
.menu-separator {
  border: none;
  height: 1px;
  background: var(--nonna-beige);
  margin: 0;
}

/* Tags */
.menu-tag {
  font-family: 'Inter', sans-serif;
  font-size: 11px;
  font-weight: 700;
  padding: 2px 8px;
  border-radius: 4px;
  flex-shrink: 0;
}
.tag-vegan { background: rgba(152,14,30,0.08); color: var(--nonna-rojo); }
.tag-spicy { background: rgba(152,14,30,0.08); color: var(--nonna-rojo); }
.tag-alcohol { background: rgba(152,14,30,0.08); color: var(--nonna-rojo); }

/* Nonna's pick badge */
.menu-badge-pick {
  background: var(--nonna-rojo);
  color: var(--nonna-beige);
  font-size: 10px;
  font-weight: 600;
  padding: 3px 10px;
  border-radius: 4px;
  flex-shrink: 0;
  font-family: 'Inter', sans-serif;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

/* + Add button */
.add-btn {
  background: none;
  border: 1.5px solid var(--nonna-whatsapp);
  color: var(--nonna-whatsapp);
  padding: 4px 14px;
  border-radius: var(--radius-full);
  font-size: 13px;
  font-weight: 600;
  font-family: 'Inter', sans-serif;
  cursor: pointer;
  transition: var(--transition-fast);
  flex-shrink: 0;
  white-space: nowrap;
}
.add-btn:hover, .add-btn.added {
  background: var(--nonna-whatsapp);
  color: white;
}

/* Hover image (desktop) */
.menu-hover-img {
  position: fixed;
  width: 260px;
  height: 260px;
  object-fit: cover;
  border-radius: var(--radius-md);
  pointer-events: none;
  opacity: 0;
  z-index: 100;
  box-shadow: var(--shadow-medium);
}

/* Legend */
.menu-legend {
  display: flex;
  gap: 20px;
  justify-content: center;
  align-items: center;
  margin-top: 24px;
  font-size: 13px;
  color: var(--nonna-text-muted);
  flex-wrap: wrap;
}
.menu-legend-note {
  font-style: italic;
  opacity: 0.7;
}

@media (max-width: 768px) {
  .menu-item-name { font-size: 17px; }
  .menu-price { font-size: 16px; }
  .menu-list-container { padding: 20px 16px; }
  .menu-hover-img { display: none !important; }
  .menu-tabs { justify-content: flex-start; }
}
```

## JS (Menu)
```javascript
// === ORDER BUILDER ===
let orderItems = [];

function toggleOrderItem(name, price, button) {
  const index = orderItems.findIndex(i => i.name === name);
  if (index > -1) {
    orderItems.splice(index, 1);
    button.classList.remove('added');
    button.textContent = '+ Add';
  } else {
    orderItems.push({ name, price });
    button.classList.add('added');
    button.textContent = 'Added ✓';
  }
  updateWhatsAppLinks();
}

function updateWhatsAppLinks() {
  const phone = '523312345678'; // REPLACE with actual WhatsApp number
  let message = 'Hello La Nonna! I\'d like to order:\n\n';
  if (orderItems.length === 0) {
    message = 'Hello La Nonna! I\'d like to place an order. 🍝';
  } else {
    let total = 0;
    orderItems.forEach(item => {
      message += `• ${item.name} — $${item.price} MXN\n`;
      total += item.price;
    });
    message += `\nTotal: $${total} MXN\nThank you! 🍝`;
  }
  const encoded = encodeURIComponent(message);
  const url = `https://wa.me/${phone}?text=${encoded}`;
  document.querySelectorAll('.wa-order-link').forEach(el => {
    el.href = url;
  });
}

// === TAB FILTERING ===
function initMenuTabs() {
  const tabs = document.querySelectorAll('.menu-tab');
  const categories = document.querySelectorAll('.menu-category');

  tabs.forEach(tab => {
    tab.addEventListener('click', () => {
      const cat = tab.getAttribute('data-category');

      tabs.forEach(t => t.classList.remove('active'));
      tab.classList.add('active');

      categories.forEach(c => {
        if (c.getAttribute('data-category') === cat) {
          c.style.display = 'block';
          // Animate items in
          gsap.fromTo(c.querySelectorAll('.menu-list-item'),
            { opacity: 0, y: 20 },
            { opacity: 1, y: 0, stagger: 0.06, duration: 0.4, ease: 'power2.out' }
          );
        } else {
          c.style.display = 'none';
        }
      });
    });
  });
}

// === HOVER IMAGES (desktop) ===
function initMenuHoverImages() {
  if (window.innerWidth <= 991) return;

  document.querySelectorAll('.menu-list-item').forEach(item => {
    const img = item.querySelector('.menu-hover-img');
    if (!img) return;

    item.addEventListener('mousemove', (e) => {
      gsap.to(img, {
        opacity: 1,
        left: e.clientX + 24,
        top: e.clientY - 130,
        duration: 0.35,
        ease: 'power3.out'
      });
    });
    item.addEventListener('mouseleave', () => {
      gsap.to(img, { opacity: 0, duration: 0.3 });
    });
  });
}
```

---

# PART 11: ORDER SECTION

## HTML
```html
<section class="order-section section-padding" id="order" style="background: var(--nonna-white);">
  <div class="container">
    <div class="text-center mb-5">
      <span class="section-eyebrow" data-aos="fade-up">RESERVE OR ORDER</span>
      <h2 class="anim-title" style="color: var(--nonna-rojo);">Ready to Order?</h2>
      <p class="section-subtitle" data-aos="fade-up" data-aos-delay="100" style="font-family: 'Playfair Display'; font-style: italic; color: var(--nonna-text-muted); font-size: 18px;">Choose how you'd like to enjoy La Nonna</p>
    </div>

    <!-- Service cards -->
    <div class="row g-4 justify-content-center mb-4">
      <div class="col-md-5" data-aos="fade-up">
        <div class="order-card">
          <!-- REPLACE: dine-in illustration (rec: 64x64px SVG or PNG) -->
          <div class="order-card-icon img-placeholder" style="width:64px;height:64px;border-radius:50%;margin:0 auto 16px;">Dine-in icon</div>
          <h3 style="font-size: 24px; color: var(--nonna-text);">Dine with Us</h3>
          <p style="color: var(--nonna-text-muted); font-size: 15px; margin: 8px 0 20px;">Visit us and experience the warmth of La Nonna in person. Walk-ins welcome, reservations recommended for groups of 6+.</p>
          <a href="https://maps.google.com/?q=C.+Pedro+Moreno+1567,+Col.+Americana,+Lafayette,+44160+Guadalajara,+Jal."
             class="btn-nonna-primary" target="_blank" rel="noopener">
            <i class="bi bi-geo-alt"></i> Get Directions
          </a>
        </div>
      </div>
      <div class="col-md-5" data-aos="fade-up" data-aos-delay="150">
        <div class="order-card order-card-featured">
          <span class="order-popular-badge">Most popular</span>
          <!-- REPLACE: takeout illustration (rec: 64x64px SVG or PNG) -->
          <div class="order-card-icon img-placeholder" style="width:64px;height:64px;border-radius:50%;margin:0 auto 16px;">Takeout icon</div>
          <h3 style="font-size: 24px; color: var(--nonna-text);">Order Takeout</h3>
          <p style="color: var(--nonna-text-muted); font-size: 15px; margin: 8px 0 20px;">Browse our menu above, tap "+ Add" on your favorites, then send your order directly via WhatsApp.</p>
          <a href="https://wa.me/523312345678?text=Hello%20La%20Nonna!%20I%27d%20like%20to%20place%20an%20order.%20%F0%9F%8D%9D"
             class="btn-whatsapp wa-order-link" target="_blank" rel="noopener">
            <i class="bi bi-whatsapp"></i> Order via WhatsApp
          </a>
        </div>
      </div>
    </div>

    <!-- Main WhatsApp CTA -->
    <div class="text-center my-5" data-aos="fade-up">
      <a href="https://wa.me/523312345678?text=Hello%20La%20Nonna!%20I%27d%20like%20to%20place%20an%20order.%20%F0%9F%8D%9D"
         class="btn-whatsapp btn-whatsapp-lg wa-order-link" target="_blank" rel="noopener">
        <i class="bi bi-whatsapp"></i> Order now via WhatsApp
      </a>
    </div>

    <!-- Location & Hours -->
    <div class="row g-4 mt-4">
      <div class="col-md-6" data-aos="fade-up">
        <h4 style="color: var(--nonna-rojo); font-size: 20px; margin-bottom: 16px;">Find Us</h4>
        <p style="color: var(--nonna-text-muted); line-height: 1.8; font-size: 15px;">
          <i class="bi bi-geo-alt" style="color: var(--nonna-rojo);"></i> C. Pedro Moreno 1567, Col. Americana, Lafayette, 44160 Guadalajara, Jal.<br>
          <i class="bi bi-telephone" style="color: var(--nonna-rojo);"></i> +52 33 1234 5678<br>
          <i class="bi bi-envelope" style="color: var(--nonna-rojo);"></i> info@lanonnatrattoria.com<br>
          <i class="bi bi-globe" style="color: var(--nonna-rojo);"></i> www.lanonnatrattoria.com
        </p>
        <!-- REPLACE: Update the Google Maps embed src with actual coordinates -->
        <div class="map-container" style="border-radius: var(--radius-md); overflow: hidden; margin-top: 16px;">
          <iframe
            src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3732.5!2d-103.365!3d20.675!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x0%3A0x0!2zMjDCsDQwJzMwLjAiTiAxMDPCsDIxJzU0LjAiVw!5e0!3m2!1sen!2smx!4v1234567890"
            width="100%" height="220" style="border:0;" allowfullscreen="" loading="lazy" referrerpolicy="no-referrer-when-downgrade">
          </iframe>
        </div>
      </div>
      <div class="col-md-6" data-aos="fade-up" data-aos-delay="150">
        <h4 style="color: var(--nonna-rojo); font-size: 20px; margin-bottom: 16px;">Opening Hours</h4>
        <div class="hours-table">
          <div class="hours-row"><span class="hours-day">Monday</span><span class="hours-time hours-closed">Closed</span></div>
          <div class="hours-row"><span class="hours-day">Tuesday — Thursday</span><span class="hours-time">1:00 PM — 10:00 PM</span></div>
          <div class="hours-row"><span class="hours-day">Friday — Saturday</span><span class="hours-time">1:00 PM — 11:00 PM</span></div>
          <div class="hours-row"><span class="hours-day">Sunday</span><span class="hours-time">12:00 PM — 9:00 PM</span></div>
        </div>
        <!-- Live open/closed badge -->
        <div class="open-status" id="openStatus">Checking...</div>
      </div>
    </div>
  </div>
</section>
```

## CSS (Order-specific)
```css
.order-card {
  background: var(--nonna-beige-light);
  border-radius: var(--radius-lg);
  padding: 40px 32px;
  text-align: center;
  border: 2px solid transparent;
  transition: var(--transition-smooth);
}
.order-card:hover {
  transform: translateY(-4px);
  box-shadow: var(--shadow-medium);
}
.order-card-featured {
  border-color: var(--nonna-whatsapp);
  position: relative;
}
.order-popular-badge {
  position: absolute;
  top: -12px;
  left: 50%;
  transform: translateX(-50%);
  background: var(--nonna-whatsapp);
  color: white;
  font-size: 12px;
  font-weight: 600;
  padding: 4px 16px;
  border-radius: var(--radius-full);
}
.btn-whatsapp-lg {
  font-size: 20px;
  padding: 18px 48px;
}
.hours-table {
  background: var(--nonna-beige);
  border-radius: var(--radius-md);
  padding: 20px 24px;
  border-left: 3px solid var(--nonna-rojo);
}
.hours-row {
  display: flex;
  justify-content: space-between;
  padding: 8px 0;
  font-size: 15px;
}
.hours-row + .hours-row { border-top: 1px solid var(--nonna-beige-dark); }
.hours-day { color: var(--nonna-text-muted); }
.hours-time { font-weight: 500; }
.hours-closed { color: var(--nonna-rojo); font-weight: 600; }
.open-status {
  margin-top: 16px;
  padding: 10px 20px;
  border-radius: var(--radius-sm);
  font-size: 14px;
  font-weight: 600;
  text-align: center;
  background: rgba(220, 53, 69, 0.1);
  color: #dc3545;
}
.open-status.open {
  background: rgba(37, 211, 102, 0.1);
  color: #1a9e4d;
}
```

## JS (Order)
```javascript
function initOpenStatus() {
  function update() {
    const now = new Date();
    const day = now.getDay();
    const time = now.getHours() + now.getMinutes() / 60;
    const schedule = {
      0: [12, 21],     // Sunday
      1: null,          // Monday closed
      2: [13, 22], 3: [13, 22], 4: [13, 22],  // Tue-Thu
      5: [13, 23], 6: [13, 23]                  // Fri-Sat
    };
    const today = schedule[day];
    const isOpen = today && time >= today[0] && time < today[1];
    const badge = document.getElementById('openStatus');
    if (isOpen) {
      badge.textContent = '● Currently open';
      badge.className = 'open-status open';
    } else {
      badge.textContent = '● Currently closed';
      badge.className = 'open-status';
    }
  }
  update();
  setInterval(update, 60000);
}
```

---

# PART 12: FAQ SECTION

## HTML
```html
<section class="faq-section section-padding" id="faq" style="background: var(--nonna-beige);">
  <div class="container">
    <div class="text-center mb-5">
      <span class="section-eyebrow" data-aos="fade-up">NEED HELP?</span>
      <h2 class="anim-title" style="color: var(--nonna-rojo);">Frequently Asked Questions</h2>
    </div>

    <div class="faq-container" style="max-width: 800px; margin: 0 auto;">

      <div class="faq-item" data-aos="fade-up">
        <button class="faq-question" aria-expanded="false">
          <span>What are your opening hours?</span>
          <span class="faq-icon">+</span>
        </button>
        <div class="faq-answer">
          <p>We're open Tuesday through Thursday from 1:00 PM to 10:00 PM, Friday and Saturday from 1:00 PM to 11:00 PM, and Sunday from 12:00 PM to 9:00 PM. We are closed every Monday.</p>
        </div>
      </div>

      <div class="faq-item" data-aos="fade-up" data-aos-delay="50">
        <button class="faq-question" aria-expanded="false">
          <span>Do you accommodate dietary restrictions or allergies?</span>
          <span class="faq-icon">+</span>
        </button>
        <div class="faq-answer">
          <p>Absolutely. We offer several vegan options and can accommodate most dietary needs. Our menu clearly marks vegan (V), spicy (S), and alcohol-containing (A) dishes with tags. Please let your server know about any allergies, and our kitchen will do their best to accommodate you.</p>
        </div>
      </div>

      <div class="faq-item" data-aos="fade-up" data-aos-delay="100">
        <button class="faq-question" aria-expanded="false">
          <span>Is there parking available?</span>
          <span class="faq-icon">+</span>
        </button>
        <div class="faq-answer">
          <p>Yes, we have a private parking lot behind the restaurant with space for approximately 20 vehicles. Street parking is also available along Pedro Moreno and surrounding streets in the Americana neighborhood.</p>
        </div>
      </div>

      <div class="faq-item" data-aos="fade-up" data-aos-delay="150">
        <button class="faq-question" aria-expanded="false">
          <span>Do you accept reservations?</span>
          <span class="faq-icon">+</span>
        </button>
        <div class="faq-answer">
          <p>Walk-ins are always welcome! For groups of 6 or more, or for special occasions, we recommend making a reservation by calling us at +52 33 1234 5678 or sending a message through WhatsApp.</p>
        </div>
      </div>

      <div class="faq-item" data-aos="fade-up" data-aos-delay="200">
        <button class="faq-question" aria-expanded="false">
          <span>Can I order takeout?</span>
          <span class="faq-icon">+</span>
        </button>
        <div class="faq-answer">
          <p>Yes! Simply browse our menu on this page, tap the "+ Add" button on the dishes you'd like, then click any of the WhatsApp order buttons. Your order will be pre-filled and ready to send to our kitchen.</p>
        </div>
      </div>

      <div class="faq-item" data-aos="fade-up" data-aos-delay="250">
        <button class="faq-question" aria-expanded="false">
          <span>Do you offer catering or private events?</span>
          <span class="faq-icon">+</span>
        </button>
        <div class="faq-answer">
          <p>While we don't currently offer catering services, we'd love to hear from you about special requests. Contact us via phone or WhatsApp and we'll see what we can arrange for your occasion.</p>
        </div>
      </div>

      <div class="faq-item" data-aos="fade-up" data-aos-delay="300">
        <button class="faq-question" aria-expanded="false">
          <span>What forms of payment do you accept?</span>
          <span class="faq-icon">+</span>
        </button>
        <div class="faq-answer">
          <p>We accept cash (MXN), all major credit and debit cards (Visa, Mastercard, American Express), and digital payments through contactless methods. We do not currently accept cryptocurrency.</p>
        </div>
      </div>

      <div class="faq-item" data-aos="fade-up" data-aos-delay="350">
        <button class="faq-question" aria-expanded="false">
          <span>Is the restaurant family-friendly?</span>
          <span class="faq-icon">+</span>
        </button>
        <div class="faq-answer">
          <p>Absolutely! La Nonna is a family restaurant at heart — it's right there in our name. We welcome children of all ages and offer a warm, relaxed atmosphere perfect for family meals. High chairs are available upon request.</p>
        </div>
      </div>

    </div>
  </div>
</section>
```

## CSS
```css
.faq-item {
  background: var(--nonna-white);
  border-radius: var(--radius-md);
  margin-bottom: 12px;
  overflow: hidden;
  border: 1px solid var(--nonna-beige-dark);
  transition: var(--transition-smooth);
}
.faq-item:hover { border-color: var(--nonna-rojo-medium); }
.faq-question {
  width: 100%;
  background: none;
  border: none;
  padding: 20px 24px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  cursor: pointer;
  font-family: 'Inter', sans-serif;
  font-size: 16px;
  font-weight: 500;
  color: var(--nonna-text);
  text-align: left;
  transition: var(--transition-smooth);
}
.faq-icon {
  color: var(--nonna-rojo);
  font-size: 24px;
  font-weight: 300;
  transition: transform 0.3s ease;
  flex-shrink: 0;
  margin-left: 16px;
  line-height: 1;
}
.faq-item.active .faq-icon { transform: rotate(45deg); }
.faq-item.active .faq-question { color: var(--nonna-rojo); }
.faq-answer {
  max-height: 0;
  overflow: hidden;
  transition: max-height 0.4s cubic-bezier(0.4, 0, 0.2, 1), padding 0.4s cubic-bezier(0.4, 0, 0.2, 1);
  padding: 0 24px;
}
.faq-item.active .faq-answer {
  max-height: 300px;
  padding: 0 24px 20px;
}
.faq-answer p {
  font-size: 15px;
  color: var(--nonna-text-muted);
  line-height: 1.7;
  border-top: 1px solid var(--nonna-beige);
  padding-top: 16px;
  margin: 0;
}
```

## JS
```javascript
function initFaqAccordion() {
  document.querySelectorAll('.faq-question').forEach(btn => {
    btn.addEventListener('click', () => {
      const item = btn.parentElement;
      const isActive = item.classList.contains('active');
      const expanded = !isActive;
      // Close all
      document.querySelectorAll('.faq-item.active').forEach(i => {
        i.classList.remove('active');
        i.querySelector('.faq-question').setAttribute('aria-expanded', 'false');
      });
      // Toggle current
      if (!isActive) {
        item.classList.add('active');
        btn.setAttribute('aria-expanded', 'true');
      }
    });
  });
}
```

---

# PART 13: FOOTER

## HTML
```html
<footer class="site-footer" id="footer">
  <hr class="footer-top-line anim-line" style="width:0%; max-width:100%; height:1px; background: rgba(234,225,214,0.15); border:none; margin:0;">

  <div class="container" style="padding: 64px 0 32px;">
    <div class="text-center">
      <p class="brand-script" style="font-size: 32px; color: var(--nonna-beige); margin-bottom: 6px;">La Nonna trattoria</p>
      <p style="font-size: 12px; color: rgba(234,225,214,0.5); letter-spacing: 3px; text-transform: uppercase; margin-bottom: 32px;">Authentic Italian Cuisine Since 1962</p>

      <div class="row justify-content-center mb-4" style="font-size: 14px; color: rgba(234,225,214,0.6);">
        <div class="col-md-4 mb-3 mb-md-0">
          <p style="color: rgba(234,225,214,0.3); font-size: 11px; letter-spacing: 2px; text-transform: uppercase; margin-bottom: 6px;">Address</p>
          <p style="margin:0;">C. Pedro Moreno 1567, Col. Americana<br>44160 Guadalajara, Jal.</p>
        </div>
        <div class="col-md-4 mb-3 mb-md-0">
          <p style="color: rgba(234,225,214,0.3); font-size: 11px; letter-spacing: 2px; text-transform: uppercase; margin-bottom: 6px;">Contact</p>
          <p style="margin:0;">+52 33 1234 5678<br>info@lanonnatrattoria.com</p>
        </div>
        <div class="col-md-4">
          <p style="color: rgba(234,225,214,0.3); font-size: 11px; letter-spacing: 2px; text-transform: uppercase; margin-bottom: 6px;">Hours</p>
          <p style="margin:0;">Tue–Sat: 1:00 PM – 11:00 PM<br>Sun: 12:00 PM – 9:00 PM</p>
        </div>
      </div>

      <div class="footer-social-links mb-4">
        <a href="#" target="_blank" rel="noopener" aria-label="Instagram"><i class="bi bi-instagram"></i></a>
        <!-- REPLACE: actual Instagram URL above -->
        <a href="#" target="_blank" rel="noopener" aria-label="Facebook"><i class="bi bi-facebook"></i></a>
        <!-- REPLACE: actual Facebook URL above -->
        <a href="#" target="_blank" rel="noopener" aria-label="TikTok"><i class="bi bi-tiktok"></i></a>
        <!-- REPLACE: actual TikTok URL above -->
        <a href="https://wa.me/523312345678" target="_blank" rel="noopener" aria-label="WhatsApp"><i class="bi bi-whatsapp"></i></a>
      </div>

      <!-- Back to top -->
      <button class="back-to-top-btn" id="backToTopBtn" aria-label="Back to top">
        <i class="bi bi-chevron-up"></i>
      </button>

      <p style="font-size: 12px; color: rgba(234,225,214,0.25); margin-top: 32px;">&copy; 2026 La Nonna Trattoria. All rights reserved.</p>
    </div>
  </div>
</footer>
```

## CSS
```css
.site-footer {
  background: var(--nonna-black);
  color: var(--nonna-beige);
}
.footer-social-links {
  display: flex;
  gap: 12px;
  justify-content: center;
}
.footer-social-links a {
  width: 42px;
  height: 42px;
  border: 1px solid rgba(234, 225, 214, 0.2);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  color: var(--nonna-beige);
  font-size: 17px;
  transition: var(--transition-smooth);
}
.footer-social-links a:hover {
  background: var(--nonna-beige);
  color: var(--nonna-black);
  border-color: var(--nonna-beige);
  transform: translateY(-3px);
}
.back-to-top-btn {
  width: 44px;
  height: 44px;
  border: 1px solid rgba(234, 225, 214, 0.2);
  border-radius: 50%;
  background: none;
  color: var(--nonna-beige);
  font-size: 18px;
  cursor: pointer;
  transition: var(--transition-smooth);
  margin: 24px auto 0;
  display: flex;
  align-items: center;
  justify-content: center;
}
.back-to-top-btn:hover {
  background: rgba(234, 225, 214, 0.1);
  transform: translateY(-3px);
}
.back-to-top-overlay {
  position: fixed;
  inset: 0;
  background: var(--nonna-beige);
  z-index: 9998;
  pointer-events: none;
  transform: translateY(100%);
}
```

## JS
```javascript
function initFooter() {
  // Animated top line
  gsap.fromTo('.footer-top-line', { width: '0%' }, {
    width: '100%',
    scrollTrigger: { trigger: '.site-footer', start: 'top 90%' },
    duration: 1,
    ease: 'power2.out'
  });

  // Back to top with overlay transition
  document.getElementById('backToTopBtn').addEventListener('click', () => {
    const overlay = document.getElementById('backToTopOverlay');
    const tl = gsap.timeline();
    tl.to(overlay, { y: 0, duration: 0.4, ease: 'expo.inOut', pointerEvents: 'all' })
      .call(() => { window.scrollTo({ top: 0 }); })
      .to(overlay, { y: '-100%', duration: 0.4, ease: 'expo.inOut', delay: 0.1 })
      .set(overlay, { y: '100%', pointerEvents: 'none' });
  });
}
```

---

# PART 14: FLOATING SOCIAL BAR

## HTML
```html
<div class="floating-social" id="floatingSocial">
  <a href="https://wa.me/523312345678?text=Hello%20La%20Nonna!%20I%27d%20like%20to%20place%20an%20order.%20%F0%9F%8D%9D"
     class="float-btn float-wa wa-order-link" target="_blank" rel="noopener" aria-label="WhatsApp">
    <i class="bi bi-whatsapp"></i>
    <span class="float-tooltip">WhatsApp</span>
  </a>
  <a href="#" class="float-btn float-ig" target="_blank" rel="noopener" aria-label="Instagram">
    <!-- REPLACE: actual Instagram URL -->
    <i class="bi bi-instagram"></i>
    <span class="float-tooltip">Instagram</span>
  </a>
  <a href="#" class="float-btn float-fb" target="_blank" rel="noopener" aria-label="Facebook">
    <!-- REPLACE: actual Facebook URL -->
    <i class="bi bi-facebook"></i>
    <span class="float-tooltip">Facebook</span>
  </a>
  <a href="#" class="float-btn float-tt" target="_blank" rel="noopener" aria-label="TikTok">
    <!-- REPLACE: actual TikTok URL -->
    <i class="bi bi-tiktok"></i>
    <span class="float-tooltip">TikTok</span>
  </a>
</div>
```

## CSS
```css
.floating-social {
  position: fixed;
  bottom: 24px;
  right: 24px;
  display: flex;
  flex-direction: column;
  gap: 10px;
  z-index: 9999;
  opacity: 0;
  transform: translateX(80px);
  transition: all 0.5s cubic-bezier(0.34, 1.56, 0.64, 1);
}
.floating-social.visible {
  opacity: 1;
  transform: translateX(0);
}
.float-btn {
  width: 44px;
  height: 44px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  font-size: 18px;
  text-decoration: none;
  transition: var(--transition-spring);
  position: relative;
  box-shadow: var(--shadow-medium);
}
.float-btn:hover {
  transform: scale(1.15);
  color: white;
}
.float-wa {
  width: 52px;
  height: 52px;
  background: var(--nonna-whatsapp);
  font-size: 22px;
  animation: pulseGlow 2s ease-in-out infinite;
}
.float-ig { background: var(--nonna-instagram); }
.float-fb { background: var(--nonna-facebook); }
.float-tt { background: var(--nonna-tiktok); border: 1.5px solid #333; }
.float-tooltip {
  position: absolute;
  right: calc(100% + 12px);
  background: var(--nonna-text);
  color: white;
  padding: 6px 12px;
  border-radius: 6px;
  font-family: 'Inter', sans-serif;
  font-size: 13px;
  font-weight: 500;
  white-space: nowrap;
  opacity: 0;
  pointer-events: none;
  transform: translateX(8px);
  transition: var(--transition-fast);
}
.float-btn:hover .float-tooltip {
  opacity: 1;
  transform: translateX(0);
}

@media (max-width: 768px) {
  .floating-social {
    flex-direction: row;
    bottom: 16px;
    right: auto;
    left: 50%;
    transform: translateX(-50%) translateY(80px);
    gap: 8px;
    background: rgba(255,255,255,0.95);
    backdrop-filter: blur(10px);
    padding: 8px 14px;
    border-radius: var(--radius-full);
    box-shadow: var(--shadow-medium);
  }
  .floating-social.visible {
    transform: translateX(-50%) translateY(0);
  }
  .float-tooltip { display: none; }
  .float-wa { width: 48px; height: 48px; }
  .float-btn:not(.float-wa) { width: 40px; height: 40px; font-size: 16px; }
}
```

## JS
```javascript
function initFloatingSocial() {
  const floatingBar = document.getElementById('floatingSocial');
  ScrollTrigger.create({
    trigger: '#hero',
    start: 'bottom top',
    onEnter: () => floatingBar.classList.add('visible'),
    onLeaveBack: () => floatingBar.classList.remove('visible')
  });
}
```

---

# PART 15: GLOBAL ANIMATION SYSTEM

## SplitText Manual Implementation (free, no plugin needed)

```javascript
function splitTextToChars(element) {
  const text = element.textContent;
  element.innerHTML = '';
  element.style.overflow = 'hidden';
  text.split('').forEach(char => {
    const span = document.createElement('span');
    span.style.display = 'inline-block';
    span.textContent = char === ' ' ? '\u00A0' : char;
    element.appendChild(span);
  });
  return element.querySelectorAll('span');
}

function initSplitTextAnimations() {
  document.querySelectorAll('.anim-title').forEach(el => {
    const chars = splitTextToChars(el);
    gsap.from(chars, {
      scrollTrigger: { trigger: el, start: 'top 82%' },
      duration: 0.7,
      y: 60,
      opacity: 0,
      rotationX: 80,
      transformOrigin: '0% 50% -50',
      ease: 'expo.out',
      stagger: 0.035
    });
  });
}
```

## Smooth Scroll (Lenis)

```javascript
function initSmoothScroll() {
  const lenis = new Lenis({
    duration: 1.2,
    easing: (t) => Math.min(1, 1.001 - Math.pow(2, -10 * t)),
    smooth: true,
    smoothTouch: false
  });

  lenis.on('scroll', ScrollTrigger.update);
  gsap.ticker.add((time) => { lenis.raf(time * 1000); });
  gsap.ticker.lagSmoothing(0);
}
```

## Master Init Function

```javascript
document.addEventListener('DOMContentLoaded', () => {
  // Register GSAP plugins
  gsap.registerPlugin(ScrollTrigger, ScrollToPlugin);

  // Init everything
  initPreloader();
  initSmoothScroll();
  initNavigation();
  initHeroSwiper();
  initSplitTextAnimations();
  initAboutAnimations();
  initMenuTabs();
  initMenuHoverImages();
  initOpenStatus();
  initFaqAccordion();
  initFooter();
  initFloatingSocial();

  // Update WhatsApp links on load
  updateWhatsAppLinks();
});
```

---

# PART 16: IMAGE PLACEHOLDERS CHECKLIST

| # | Location | ID/Class | Size | Format | Description |
|---|----------|----------|------|--------|-------------|
| 1 | Hero slide 1 | `img/hero-1.jpg` | 1920x1080px | JPG | Restaurant exterior or interior |
| 2 | Hero slide 2 | `img/hero-2.jpg` | 1920x1080px | JPG | Signature dish close-up |
| 3 | Hero slide 3 | `img/hero-3.jpg` | 1920x1080px | JPG | Family dining or chef cooking |
| 4 | Nav hover - About | `img/nav-about.jpg` | 400x500px | JPG | Restaurant interior |
| 5 | Nav hover - Menu | `img/nav-menu.jpg` | 400x500px | JPG | Food close-up |
| 6 | Nav hover - Order | `img/nav-order.jpg` | 400x500px | JPG | Takeout packaging |
| 7 | Nav hover - FAQ | `img/nav-faq.jpg` | 400x500px | JPG | Cozy table scene |
| 8 | About photo 1 | `img/about-1.jpg` | 600x400px | JPG | Restaurant interior |
| 9 | About photo 2 | `img/about-2.jpg` | 600x400px | JPG | Kitchen/family/food |
| 10 | OG image | `img/og-image.jpg` | 1200x630px | JPG | Social share image |
| 11 | Favicon | `img/favicon.ico` | 32x32px | ICO | Browser tab icon |
| 12-46 | Menu items (35) | `img/menu/[name].jpg` | 300x300px | JPG | Square dish photos |
| 47 | Order dine-in icon | in order section | 64x64px | SVG/PNG | Dine-in illustration |
| 48 | Order takeout icon | in order section | 64x64px | SVG/PNG | Takeout illustration |

All marked with `<!-- REPLACE: description -->` comments in the HTML.

---

# PART 17: RESPONSIVE BREAKPOINTS SUMMARY

| Breakpoint | Layout changes |
|------------|---------------|
| `≥1200px` | Full layout. Fullscreen nav with hover images. Menu list view. Floating social vertical right. |
| `992–1199px` | Same layout, reduced padding. |
| `768–991px` | About section stacks to 1 column. Nav hover images disabled. Menu stays list view. |
| `<768px` | Single column everything. Hamburger (no label). Fullscreen nav without images. Menu tabs scroll horizontal. Floating social = horizontal centered pill bar at bottom. Hero brand 44px. Section padding 56px. Full-width buttons. |

---

# PART 18: FILE STRUCTURE

```
/
├── index.html              ← Single file (HTML + CSS + JS)
├── /img                    ← Add images manually
│   ├── favicon.ico
│   ├── og-image.jpg
│   ├── hero-1.jpg
│   ├── hero-2.jpg
│   ├── hero-3.jpg
│   ├── nav-about.jpg
│   ├── nav-menu.jpg
│   ├── nav-order.jpg
│   ├── nav-faq.jpg
│   ├── about-1.jpg
│   ├── about-2.jpg
│   └── /menu
│       ├── bruschetta.jpg
│       ├── carpaccio.jpg
│       ├── calamari.jpg
│       ├── burrata.jpg
│       ├── caprese.jpg
│       ├── arancini.jpg
│       ├── carbonara.jpg
│       ├── arrabbiata.jpg
│       ├── alfredo.jpg
│       ├── lasagna.jpg
│       ├── ravioli.jpg
│       ├── pappardelle.jpg
│       ├── cacio.jpg
│       ├── gnocchi.jpg
│       ├── margherita.jpg
│       ├── diavola.jpg
│       ├── quattro.jpg
│       ├── prosciutto-pizza.jpg
│       ├── funghi.jpg
│       ├── marinara.jpg
│       ├── tiramisu.jpg
│       ├── pannacotta.jpg
│       ├── cannoli.jpg
│       ├── affogato.jpg
│       ├── torta.jpg
│       ├── limonata.jpg
│       ├── espresso.jpg
│       ├── cappuccino.jpg
│       ├── pellegrino.jpg
│       ├── chianti.jpg
│       ├── prosecco.jpg
│       ├── aperol.jpg
│       └── negroni.jpg
└── README.md
```

---

# PART 19: THINGS TO REPLACE BEFORE GOING LIVE

Search for `REPLACE` in the HTML to find all items that need real data:

1. **WhatsApp number**: Replace all instances of `523312345678` with the actual number
2. **Social media URLs**: Instagram, Facebook, TikTok — replace all `href="#"` on social links
3. **All images**: Replace placeholder images with real photos (see Part 16 for sizes)
4. **Google Maps embed**: Update the iframe `src` with the actual restaurant coordinates
5. **OG image**: Create and add a social share image at `img/og-image.jpg`
6. **Favicon**: Add a favicon at `img/favicon.ico`
7. **Email**: Verify `info@lanonnatrattoria.com` is correct
8. **Phone**: Verify `+52 33 1234 5678` is correct
9. **Address**: Verify `C. Pedro Moreno 1567` is correct
