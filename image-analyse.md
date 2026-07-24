# Standard Operating Procedure (SOP): Minimal Figma Globals Extraction

> [!NOTE]
> This Standard Operating Procedure (SOP) defines the streamlined method for inspecting a Figma design file/link or screenshot, extracting ONLY the essential global resets, font imports, global buttons (`.glb-btn`), and recurring subheadings (`.sub-heading`), while omitting CSS/SCSS variables.

---

## 1. Scope & Rules

When reading a Figma design file or link for global styles:

1. **3-Tier Font Resolution Protocol:**
   - **Tier 1 (Google Fonts):** If the font is on Google Fonts, import it directly at the top of the stylesheet (e.g. `@import url("https://fonts.googleapis.com/css2?family=Montserrat:wght@400;600;700&display=swap");`).
   - **Tier 2 (Free CDN Fonts):** If NOT on Google Fonts, check and import from free font CDNs (e.g., Fontshare, cdnjs, Google Web Fonts helpers).
   - **Tier 3 (Download Link Fallback):** If the font is custom or paid and NOT available on Google Fonts or free CDNs, provide a clear, valid download/webfont source link so you can download the `.woff2`/`.ttf` files for your `fonts/` directory.
2. **NO CSS/SCSS Variables:** Do NOT generate `$variable` lists or `:root { --variable: ... }` blocks. Use hex/color values directly inside CSS/SCSS rules.
3. **Target ONLY 3 Core Global Elements:**
   - **Global Reset & Media Defaults** (`*`, `body`, `a`, `ul`, `img`).
   - **Global Buttons (`.glb-btn`)** and its modifier classes.
   - **Global Subheadings (`.sub-heading`)** badges (if recurring across the design).
4. **Keep Code Minimal & Clean:** Omit unnecessary utility classes or bloated tokens.

---

## 2. Minimal Global Stylesheet Blueprints

### 2.1 Font Import & Global Reset

```css
/* ============================================
   TIER 1 & 2 FONT IMPORTS
   ============================================ */
@import url("https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@0,100..900;1,100..900&display=swap");

/* NOTE: If custom font is not on Google Fonts or CDN, valid download link will be provided below:
   - Example Download Source: https://www.fontshare.com/fonts/[font-name] */

/* ============================================
   GLOBAL RESET & BASE DEFAULTS
   ============================================ */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: "Montserrat", sans-serif;
  overflow-x: hidden;
  position: relative;
  color: #151515;
}

a {
  text-decoration: none;
  display: block;
  color: #151515;
  transition: color 0.3s ease;
}

a:hover {
  color: #bf8f2d;
}

ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

img {
  max-width: 100%;
  display: block;
}
```

---

### 2.2 Global Sub-Heading Badges (`.sub-heading`)

*(Extracted if used across multiple sections in Figma)*

```css
/* ============================================
   GLOBAL SUB-HEADING BADGES
   ============================================ */
.sub-heading {
  color: #ffffff;
  font-size: 0.875rem;
  font-weight: 400;
  line-height: normal;
  padding: 0.4063rem 0.9375rem;
  background-color: #1d5c20;
  display: inline-flex;
  justify-content: center;
  align-items: center;
  border-radius: 1.875rem;
  margin-bottom: 1rem;
}

.sub-heading.wh {
  border: 1px solid #ffffff;
  background-color: transparent;
}
```

---

### 2.3 Global Button Component Family (`.glb-btn`)

```css
/* ============================================
   GLOBAL BUTTON COMPONENTS (.glb-btn)
   ============================================ */
.glb-btn {
  padding: 0.75rem 1.5rem;
  border-radius: 1.875rem;
  color: #ffffff;
  text-align: center;
  font-size: 1rem;
  font-weight: 600;
  line-height: normal;
  background-color: #bf8f2d;
  display: inline-flex;
  justify-content: center;
  align-items: center;
  gap: 0.375rem;
  text-decoration: none;
  transition: all 0.3s ease;
}

.glb-btn:hover {
  color: #ffffff;
  background-color: #a37824;
}

.glb-btn.bd {
  background-color: transparent;
  border: 1px solid #bf8f2d;
  color: #bf8f2d;
}

.glb-btn.bd:hover {
  background-color: #bf8f2d;
  color: #ffffff;
}

.glb-btn.green {
  padding: 0.625rem 5rem;
  border-radius: 1.875rem;
  background-color: #1d5c20;
}

.glb-btn.transparent-btn {
  padding: 1.0313rem 2.4rem;
  border-radius: 1.875rem;
  backdrop-filter: blur(10px);
  background-color: rgba(255, 255, 255, 0.1);
  color: #ffffff;
  border: 1px solid rgba(255, 255, 255, 0.3);
}
```

---

## 3. Global Responsive Font Scaling (`responsive.css`)

```css
/* ============================================
   GLOBAL RESPONSIVE FONT SCALING
   ============================================ */
@media (max-width: 1399px) {
  html {
    font-size: 86.8%;
  }
}

/* 1199px INHERITS root font-size from 1399px (86.8%) */

@media (max-width: 991px) {
  html {
    font-size: 100%;
  }
}
```

---

## 4. How to Request Figma Globals Under This SOP

Simply prompt:
> *"Extract the global reset, font imports, .glb-btn styles, and .sub-heading from this Figma link."*

I will immediately return:
1. **Font Imports / Download Links** (Google Fonts / CDN / Download fallback).
2. **Global Reset**.
3. **`.glb-btn` & `.sub-heading` Component Styles**.
4. **Global Responsive Scaling**.
