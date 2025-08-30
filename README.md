# Brand Guide — Quick Start

A clean, aquatic identity built around bright blues and soft gradients.

- Primary: `#4A9CFF`, Secondary: `#4DDCFF`
- Text: `#111827` (light), `#F9FAFB` (dark), Secondary text: `#6B7280`
- Backgrounds: `#F9FAFB` (light), `#1A044C → #0F0133` (dark gradient)
- Typography: Inter (Bold for headings, Regular for body) or Poppins (SemiBold/Regular)
- Components: rounded blue buttons, clean forms with blue focus, white cards in light mode and deep‑purple cards in dark mode. CTA is always brand blue.

---

## How to use

### 1) Add fonts (choose one)
```html
<!-- Inter (recommended) -->
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap" rel="stylesheet">
<!-- Or Poppins -->
<!-- <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&display=swap"> -->
```

### 2) Drop tokens into `styles/brand.css`
```css
:root {
  /* Brand colors */
  --color-primary: #4A9CFF;
  --color-secondary: #4DDCFF;

  --text-dark: #111827;
  --text-light: #F9FAFB;
  --text-secondary: #6B7280;

  --bg-light: #F9FAFB;
  --bg-dark: #1A044C;

  /* Gradients */
  --gradient-light: linear-gradient(180deg, #ffffff 0%, rgba(77, 220, 255, 0.12) 100%);
  --gradient-dark: linear-gradient(180deg, #1A044C 0%, #0F0133 100%);

  /* Effects */
  --focus-ring: 0 0 0 3px rgba(74, 156, 255, 0.35);
  --shadow-soft: 0 8px 24px rgba(0, 0, 0, 0.08);
  --radius-md: 12px;
  --radius-lg: 16px;
}

/* Theme scopes: set <html data-theme="light|dark"> */
[data-theme="light"] {
  --bg: var(--bg-light);
  --text: var(--text-dark);
  --card-bg: #ffffff;
}

[data-theme="dark"] {
  --bg: var(--bg-dark);
  --text: var(--text-light);
  --card-bg: #1A044C;
}

/* Base + typography */
body {
  margin: 0;
  background: var(--bg);
  color: var(--text);
  font-family: Inter, ui-sans-serif, system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial, "Noto Sans", sans-serif;
}
h1, h2, h3 { font-weight: 700; }
/* If using Poppins, swap the font-family above to "Poppins" */

.text-secondary { color: var(--text-secondary); }

/* Components */
.btn {
  display: inline-flex; align-items: center; justify-content: center;
  padding: 0.75rem 1rem; border: 0; border-radius: var(--radius-md);
  font-weight: 600; cursor: pointer; transition: transform .05s ease, filter .2s ease;
}
.btn-primary { background: var(--color-primary); color: #ffffff; }
.btn-primary:hover { filter: brightness(0.95); }
.btn-primary:active { transform: translateY(1px); }
.btn-primary:focus-visible { outline: none; box-shadow: var(--focus-ring); }

.card {
  background: var(--card-bg);
  border-radius: var(--radius-lg);
  box-shadow: var(--shadow-soft);
  padding: 1.25rem;
}

.input, input, textarea, select {
  width: 100%;
  padding: 0.625rem 0.75rem;
  border: 1px solid rgba(0,0,0,0.12);
  border-radius: var(--radius-md);
  background: #ffffff;
}
[data-theme="dark"] .input,
[data-theme="dark"] input,
[data-theme="dark"] textarea,
[data-theme="dark"] select {
  background: rgba(255,255,255,0.02);
  color: var(--text);
  border-color: rgba(255,255,255,0.16);
}
.input:focus, input:focus, textarea:focus, select:focus {
  outline: none;
  box-shadow: var(--focus-ring);
  border-color: var(--color-primary);
}

/* Navbar + hero */
.navbar {
  display: flex; align-items: center; justify-content: space-between;
  padding: 0.75rem 1rem; position: sticky; top: 0; z-index: 50;
  background: #ffffff;
}
[data-theme="dark"] .navbar { background: var(--gradient-dark); }

.hero-light { background: var(--gradient-light); }
.hero-dark  { background: var(--gradient-dark); color: var(--text-light); }
```

### 3) Use the components
```html
<header class="navbar">
  <div>Brand</div>
  <button class="btn btn-primary">Get Started</button>
</header>

<section class="hero-light" role="banner" style="padding: 4rem 1rem; text-align:center;">
  <!-- Swap to class="hero-dark" when in dark mode -->
  <img src="whale-logo.svg" alt="Brand whale logo" width="96" height="96">
  <h1>Whale-powered apps</h1>
  <p class="text-secondary">Fast, clean, and ocean-calm UI.</p>
  <button class="btn btn-primary">Try it free</button>
</section>

<div class="card" style="max-width: 480px; margin: 2rem auto;">
  <label for="email" class="text-secondary">Email</label>
  <input id="email" class="input" placeholder="you@example.com">
  <div style="margin-top: 0.75rem;">
    <button class="btn btn-primary">Subscribe</button>
  </div>
</div>
```

### 4) Enable light/dark mode
```html
<button id="theme-toggle" class="btn btn-primary">Toggle theme</button>
<script>
  const root = document.documentElement;
  // Default to system preference
  root.dataset.theme = matchMedia('(prefers-color-scheme: dark)').matches ? 'dark' : 'light';
  // Toggle on click
  document.getElementById('theme-toggle').addEventListener('click', () => {
    root.dataset.theme = root.dataset.theme === 'dark' ? 'light' : 'dark';
  });
</script>
```

---

## Notes and accessibility

- Homepage: gradient hero matching the current theme, whale logo centered; CTA in `#4A9CFF`.
- App: offer both themes; white cards in light mode, deep‑purple cards in dark mode; CTA always brand blue.
- Contrast: use `#111827` on light surfaces and `#F9FAFB` on dark; target WCAG AA (4.5:1 for body, 3:1 for large/semibold text).