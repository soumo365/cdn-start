# Standard Operating Procedure (SOP): Section & Component Code Generation (Pure CSS + Bootstrap)

> [!IMPORTANT]
> **100% PIXEL-PERFECT ACCURACY MANDATE:** All code generated under this SOP from any design input (Image, Screenshot, or Figma link) must achieve **100% visual fidelity and pixel-perfect accuracy**. Every font size, line height, color hex code, element spacing, padding, margin, border-radius, box shadow, and grid alignment must match the provided design input down to the exact pixel. Code outputs must be delivered in your exact coding style using **Bootstrap** and **Pure Vanilla CSS** (or SCSS when explicitly requested), providing **ONLY the code for that requested section**.

---

## 1. Core Mandates & Rules

When requested to create any section or frame from an image or design link:

1. **Output ONLY Section Code:** Do not include full project directory setups or HTML document wrappers (`<html>`, `<head>`, `<body>`). Provide only the standalone section code.
2. **Stylesheet Format Rule (CSS Default / SCSS on Request):**
   - If you explicitly ask for **SCSS**, output the stylesheet code block as **SCSS** (following your signature `style.scss` nesting rules and parent `&` references).
   - If you explicitly ask for **CSS**, output the stylesheet code block as **Pure Vanilla CSS**.
   - If the stylesheet format is **NOT specified** in your prompt, **CSS IS THE DEFAULT**.
3. **NO CSS/SCSS Variables Rule:**
   - **NEVER** declare or generate CSS variables (`:root { --var: ... }`) or SCSS variables (`$var: ...`).
   - Use color hex values directly inside the stylesheet rules (e.g. `color: #151515;`, `background-color: #bf8f2d;`).
4. **Native Bootstrap Navbar:** For headers or navigation components, always use standard Bootstrap Navbar markup (`navbar`, `navbar-expand-lg`, `.navbar-toggler`, `.collapse.navbar-collapse`, `.navbar-nav`, `.dropdown-menu`).
5. **Default Bootstrap Container Sizing:** Always use native Bootstrap `.container` (or `.container-fluid`) max-widths without forcing artificial container max-width overrides.
6. **100% Pixel-Perfect Visual Accuracy:**
   - **Colors:** Match exact color hex values for text, backgrounds, buttons, borders, shadows, and hover states.
   - **Typography:** Match exact font families, font weights, font sizes, line heights, and letter-spacings.
   - **Spacings & Padding:** Match exact vertical/horizontal paddings, margins, flex gaps, and alignment offsets.
   - **Component Styles:** Match exact border radii, box shadows, button dimensions, icon sizes, and card arrangements.
7. **Signature Class Naming:**
   - **Buttons:** `.glb-btn` (with modifiers: `.fill`, `.bd`, `.green`, `.wh`, `.transparent-btn`).
   - **Badges / Subheadings:** `.sub-heading` (with `.wh` modifier).
8. **Unordered List `<li>` Image + Text Wrapping Rule (`<span>` Standard):**
   - **EXCLUSIVE SCOPE:** This rule applies **ONLY** to `<li>` elements inside `<ul>` (unordered lists) when an `<img>` tag is directly present. **Do NOT apply to other places** (e.g. standard nav links, buttons, headers, or text blocks).
   - Inside a `<ul> <li>`, if an `<img>` tag is followed directly by independent text (or inside a link wrapper), **wrap that independent text inside a `<span>` tag**.
   - ✅ **Correct:** `<ul><li><img src="https://picsum.photos/20/20" alt=""> <span>Raviprakash Agrewal</span></li></ul>`
   - ✅ **Correct (Link Wrapper):** `<ul><li><img src="https://picsum.photos/20/20" alt=""><a href="#"> <span>info@cgigroup.com</span></a></li></ul>`
   - ❌ **Do NOT use on standard nav links:** `<a class="nav-link" href="#">Home</a>` (Keep simple, no `<span>` wrapper unless design requires).
9. **Working CDN Images for Dummy/Placeholder Assets:**
   - Whenever dummy, demonstration, or placeholder images/icons are used in generated HTML code blocks, **ALWAYS use live, working CDN image URLs** (e.g. `https://images.unsplash.com/...`, `https://picsum.photos/...`, `https://dummyimage.com/...`, `https://cdn.jsdelivr.net/...`).
   - **NEVER** output broken or non-existent local image paths like `images/placeholder.jpg` for dummy demonstrations.
10. **Compact & Beautiful Mobile Spacing:**
    - On mobile viewports (`@media (max-width: 767px)` and `@media (max-width: 575px)`), **AVOID excessive gaps, large vertical padding, or wide whitespace**.
    - Keep section paddings tight and compact (e.g. `2rem 0` to `2.5rem 0` max).
    - Keep element margins, card gaps, list item spacing, and button group gaps tight and well-proportioned so mobile layouts look sleek, compact, elegant, and beautiful.
11. **Carousel / Slider Library Rule (Owl Carousel is DEFAULT):**
    - When a section or frame contains a carousel or slider, use **Owl Carousel** or **Swiper Slider** formatted in your exact signature style.
    - **Owl Carousel is the DEFAULT** if you do not specify which slider library to use.
    - If you explicitly specify **Swiper**, Swiper Slider will be used instead.
12. **No CSS `background-image` Rule (HTML `<img>` Tag & Dynamic Positioning Standard):**
    - **NEVER** write `background-image: url(...)` inside `.css` files. This ensures backend developers can seamlessly render dynamic images from database/CMS inputs.
    - **HTML Markup:** Always place background images in the HTML markup via an `<img class="bg-img" src="..." alt="">` tag (or inline `style="background-image: url(...)"` on the element).
    - **Positioning Architecture Logic:**
      - **If Content Height < Background Image:** The background `<img>` is positioned `relative` (block) driving natural section height, and the content container (`.sec-content` / `.tx`) is set to `position: absolute; z-index: 2;`.
      - **If Content Height >= Background Image:** The content container is `relative` driving natural section height, and the background `<img>` is set to `position: absolute; top: 0; left: 0; width: 100%; height: 100%; object-fit: cover; z-index: -1;`.
      - **Mobile / Smaller Devices Rule:** Whenever section content gains more height on smaller devices (`@media (max-width: 991px)` or `@media (max-width: 767px)`), **ALWAYS switch the background `<img>` to `position: absolute; top: 0; left: 0; width: 100%; height: 100%; object-fit: cover; z-index: -1;`** and content container to `position: relative;` so content flows naturally without clipping or overflowing.
13. **Responsive Text Legibility & Contrast Highlight Rule:**
    - On smaller devices / mobile viewports (`@media (max-width: 991px)` and `@media (max-width: 767px)`), if any text, link, or subheading element loses contrast or visual visibility over backgrounds, **ALWAYS assign a clear, high-contrast highlight color or backdrop overlay** matching the section's design palette (e.g. primary brand gold `#bf8f2d`, solid white, or high-contrast overlay background).
    - Ensure 100% text legibility across all screen sizes.
14. **Standardized Responsive Typography Scale Protocol:**
    - Always follow a strict, standardized responsive typography scale for headings (`h1`–`h6`) and body paragraphs (`p`) across breakpoints:
    - **Desktop Base (`> 991px`):**
      - `h1`: `2.875rem` (46px) / line-height: `3.375rem`
      - `h2`: `2.25rem` (36px) / line-height: `2.75rem`
      - `h3`: `1.75rem` (28px) / line-height: `2.25rem`
      - `h4`: `1.375rem` (22px) / line-height: `1.875rem`
      - `h5`: `1.125rem` (18px) / line-height: `1.625rem`
      - `h6` / `.sub-heading`: `0.875rem` (14px) / line-height: `1.25rem`
      - `p`: `1rem` (16px) / line-height: `1.5rem`
    - **Tablet (`@media (max-width: 991px)`):**
      - `h1`: `2.25rem` (36px) / line-height: `2.75rem`
      - `h2`: `1.875rem` (30px) / line-height: `2.375rem`
      - `h3`: `1.5rem` (24px) / line-height: `2rem`
      - `h4`: `1.25rem` (20px) / line-height: `1.625rem`
      - `p`: `0.9375rem` (15px) / line-height: `1.45rem`
    - **Mobile (`@media (max-width: 767px)`):**
      - `h1`: `1.875rem` (30px) / line-height: `2.3rem`
      - `h2`: `1.625rem` (26px) / line-height: `2.1rem`
      - `h3`: `1.375rem` (22px) / line-height: `1.8rem`
      - `h4`: `1.125rem` (18px) / line-height: `1.5rem`
      - `p`: `0.875rem` (14px) / line-height: `1.375rem`

---

## 2. Root `html` Font-Size & Responsive Breakpoint Protocol

Maintain a precise multi-tier font-scaling system across breakpoints:

```
┌─────────────────────────┬─────────────────────────────────────────────────────────────┐
│ Breakpoint              │ Root `html` Font-Size & Responsive Rule                      │
├─────────────────────────┼─────────────────────────────────────────────────────────────┤
│ Desktop Base (> 1399px) │ Standard base (100% / 16px). All rem measurements baseline.  │
│ Max-width: 1399px       │ html { font-size: 86.8%; }                                  │
│ Max-width: 1199px       │ Inherits root font-size from 1399px (no html font-size set).│
│ Max-width: 991px & Below│ html { font-size: 100%; }  (Reset to 100% for Tablet/Mobile)  │
└─────────────────────────┴─────────────────────────────────────────────────────────────┘
```

- **From `991px` down through `767px` and `575px`:**
  - `html { font-size: 100%; }` is enforced.
  - Heading and paragraph typography follow the Standardized Responsive Scale (`1.875rem` H2 on tablet, `1.625rem` H2 on mobile, `0.875rem` paragraph on mobile) to ensure 100% pixel-perfect legibility and proportion.

---

## 3. Code Generation Protocol

Every section output must be structured into 4 distinct code blocks:

```
[Design Input: Image / Figma]
       │
       ▼ (Enforce 100% Pixel-Perfect Accuracy & Standardized Responsive Scale)
 1. 📄 HTML Code Block: Bootstrap grid + Semantic tags + Bootstrap Navbar / Controls + Signature classes + <span> wrapped list text (UL LI IMG only) + Working CDN Images + HTML <img> background + Owl Carousel Markup (Default) / Swiper
 2. 🎨 Stylesheet Code Block (CSS Default / SCSS on request - NO VARIABLES): Matched with 100% precision + HTML <img> absolute positioning rules
 3. 📱 Responsive Stylesheet Code Block (responsive.css / SCSS responsive): Media queries (1399px @ 86.8%, 1199px inherited, 991px @ 100% + Standardized Heading/Paragraph Scale + mobile relative content / absolute bg img switch + high-contrast text highlights)
 4. ⚡ JavaScript Code Block (script.js): jQuery / Owl Carousel (Default) or Swiper initializations
```

---

## 4. Standard Code Blueprints & Reference Templates

### 4.1 Header / Navigation Section Blueprint (Bootstrap Navbar)

```html
<!-- ============================================
     SECTION: Header & Bootstrap Navbar
     ============================================ -->
<header class="main-header">
  <nav class="navbar navbar-expand-lg">
    <div class="container">
      <!-- Brand Logo (Working CDN Image) -->
      <a class="navbar-brand logo-sec" href="#">
        <img src="https://images.unsplash.com/photo-1618005182384-a83a8bd57fbe?w=160&auto=format&fit=crop&q=80" alt="Logo">
      </a>

      <!-- Mobile Navbar Toggler -->
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#headerNavbar" aria-controls="headerNavbar" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>

      <!-- Nav Links & Dropdowns -->
      <div class="collapse navbar-collapse" id="headerNavbar">
        <ul class="navbar-nav ms-auto mb-2 mb-lg-0">
          <li class="nav-item">
            <a class="nav-link active" href="#">Home</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#">About Us</a>
          </li>
          <li class="nav-item dropdown">
            <a class="nav-link dropdown-toggle" href="#" id="navbarDropdown" role="button" data-bs-toggle="dropdown" aria-expanded="false">
              Products
            </a>
            <ul class="dropdown-menu" aria-labelledby="navbarDropdown">
              <li><a class="dropdown-item" href="#">Category 1</a></li>
              <li><a class="dropdown-item" href="#">Category 2</a></li>
            </ul>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#">Contact</a>
          </li>
        </ul>

        <!-- Action Button -->
        <a href="#" class="glb-btn fill ms-lg-3">Get Started</a>
      </div>
    </div>
  </nav>
</header>
```

---

### 4.2 Hero Banner Section Blueprint (HTML Background Image & Dynamic Positioning Blueprint)

```html
<!-- ============================================
     SECTION: Hero Section (HTML <img> Background Tag Standard)
     ============================================ -->
<section class="hm-hero-sec">
  <!-- HTML Background Image (Never CSS background-image) -->
  <img src="https://images.unsplash.com/photo-1586528116311-ad8dd3c8310d?w=1600&auto=format&fit=crop&q=80" alt="Hero Background" class="bg-img">

  <!-- Floating Content Container -->
  <div class="container tx">
    <div class="row">
      <div class="col-lg-7 col-md-10">
        <h6 class="sub-heading">Welcome to CGI Group</h6>
        <h2>Delivering Quality & Trust Across Generations</h2>
        <p>With over 35+ years of industry experience, we specialize in high-grade processing, trading, and innovative agro-manufacturing solutions.</p>
        
        <div class="btn-sec">
          <a href="#" class="glb-btn fill">Explore Products</a>
          <a href="#" class="glb-btn bd">Contact Us</a>
        </div>
      </div>
    </div>
  </div>
</section>
```

---

### 4.3 Pure Vanilla CSS Blueprint (`style.css` Snippet - NO VARIABLES)

```css
/* ============================================
   HEADER & NAVBAR STYLES
   ============================================ */
.main-header {
  background-color: #ffffff;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.05);
}

.main-header .navbar {
  padding: 1rem 0;
}

.main-header .navbar-nav .nav-link {
  color: #151515;
  font-size: 1rem;
  font-weight: 500;
  padding: 0.5rem 1rem;
  transition: color 0.3s ease;
}

/* ============================================
   HERO SECTION STYLES (HTML BG <img> POSITIONING)
   ============================================ */
.hm-hero-sec {
  position: relative;
  overflow: hidden;
  min-height: 38rem;
  display: flex;
  align-items: center;
}

/* Background Image HTML Tag Rule */
.hm-hero-sec .bg-img {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  z-index: 1;
}

/* Content Container Over Background */
.hm-hero-sec .container.tx {
  position: relative;
  z-index: 2;
  padding: 5rem 0;
}

.hm-hero-sec .sub-heading {
  color: #ffffff;
  font-size: 0.875rem;
  font-weight: 400;
  padding: 0.4063rem 0.9375rem;
  background-color: #1d5c20;
  display: inline-flex;
  align-items: center;
  border-radius: 1.875rem;
  margin-bottom: 1rem;
}

.hm-hero-sec h2 {
  color: #ffffff;
  font-size: 2.25rem;
  font-weight: 600;
  line-height: 2.75rem;
  margin-bottom: 1.25rem;
}

.hm-hero-sec p {
  color: #f0f0f0;
  font-size: 1rem;
  line-height: 1.5rem;
  margin-bottom: 1.75rem;
}

.hm-hero-sec .btn-sec {
  display: flex;
  align-items: center;
  gap: 1rem;
}

/* Signature Button Component Styles */
.glb-btn {
  padding: 0.75rem 1.5rem;
  border-radius: 1.875rem;
  font-size: 1rem;
  font-weight: 600;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
  text-decoration: none;
  transition: all 0.3s ease;
}

.glb-btn.fill {
  background-color: #bf8f2d;
  color: #ffffff;
  border: 1px solid #bf8f2d;
}

.glb-btn.fill:hover {
  background-color: #a37824;
  color: #ffffff;
}

.glb-btn.bd {
  background-color: transparent;
  border: 1px solid #ffffff;
  color: #ffffff;
}

.glb-btn.bd:hover {
  background-color: #ffffff;
  color: #151515;
}
```

---

### 4.4 Responsive CSS Blueprint (`responsive.css` Snippet - STANDARDIZED TYPOGRAPHY SCALE)

```css
/* ============================================
   RESPONSIVE MEDIA QUERIES (STANDARDIZED TYPOGRAPHY SCALE)
   ============================================ */
@media (max-width: 1399px) {
  html {
    font-size: 86.8%;
  }
}

@media (max-width: 1199px) {
  .hm-hero-sec h2 {
    font-size: 2.125rem;
    line-height: 2.6rem;
  }
}

/* TABLET STANDARDIZED SCALE (991px) */
@media (max-width: 991px) {
  html {
    font-size: 100%;
  }
  
  .hm-hero-sec {
    min-height: auto;
    padding: 3.5rem 0;
  }
  
  .hm-hero-sec .bg-img {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    object-fit: cover;
    z-index: 1;
  }

  .hm-hero-sec .container.tx {
    position: relative;
    z-index: 2;
    padding: 0;
  }

  /* Standardized Tablet Heading & Paragraph Scale */
  .hm-hero-sec h2 {
    font-size: 1.875rem; /* 30px Tablet H2 Standard */
    line-height: 2.375rem;
  }

  .hm-hero-sec p {
    font-size: 0.9375rem; /* 15px Tablet Paragraph Standard */
    line-height: 1.45rem;
    color: #ffffff; /* High contrast overlay highlight */
    text-shadow: 0 1px 3px rgba(0, 0, 0, 0.4);
  }
}

/* MOBILE STANDARDIZED SCALE (767px) */
@media (max-width: 767px) {
  .hm-hero-sec {
    padding: 2.5rem 0;
  }
  
  /* Standardized Mobile Heading & Paragraph Scale */
  .hm-hero-sec h2 {
    font-size: 1.625rem; /* 26px Mobile H2 Standard */
    line-height: 2.1rem;
    margin-bottom: 0.875rem;
  }

  .hm-hero-sec p {
    font-size: 0.875rem; /* 14px Mobile Paragraph Standard */
    line-height: 1.375rem;
    margin-bottom: 1.25rem;
  }

  .hm-hero-sec .btn-sec {
    flex-direction: column;
    align-items: stretch;
    gap: 0.625rem;
  }

  .hm-hero-sec .glb-btn {
    width: 100%;
    text-align: center;
  }
}
```

---

### 4.5 JavaScript Blueprint (`script.js` Snippet)

```javascript
$(document).ready(function () {

  // 1. OWL CAROUSEL INITIALIZATION (DEFAULT)
  if ($('.partner-carousel').length) {
    $('.partner-carousel').owlCarousel({
      loop: true,
      margin: 20,
      nav: false,
      dots: true,
      autoplay: true,
      autoplayTimeout: 3500,
      responsive: {
        0: { items: 2 },
        600: { items: 3 },
        1000: { items: 5 }
      }
    });
  }

});
```

---

## 5. How to Request Code Under This SOP

Simply provide your image, screenshot, or Figma link and say:
> *"Create the section code for this image in my style."*

I will immediately generate the **HTML**, **Stylesheet (CSS by default, or SCSS on request - WITHOUT variables)**, **Responsive Stylesheet (`responsive.css` following the Standardized Responsive Typography Scale)**, and **JS** blocks for that exact section!
