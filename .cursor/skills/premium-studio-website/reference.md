# Visual System Reference

This document provides detailed specifications for implementing the premium multi-theme studio website system.

## Theme Variable System

### Core Variables Structure

```css
/* Theme Base */
[data-theme="precise"] {
  --bg: #fafafa;
  --surface: #ffffff;
  --surface-alt: #f5f5f5;
  --text: #1a1a1a;
  --muted: #666666;
  --accent: #0066ff;
  --border: rgba(0, 0, 0, 0.08);
  --shadow: 0 2px 8px rgba(0, 0, 0, 0.04);
  
  --radius-sm: 4px;
  --radius-md: 8px;
  --radius-lg: 12px;
  
  --button-height: 44px;
  --section-padding: 120px;
  --card-gap: 24px;
  --transition-speed: 0.2s;
}

[data-theme="bold"] {
  --bg: #0a0a0a;
  --surface: #141414;
  --surface-alt: #1a1a1a;
  --text: #ffffff;
  --muted: #999999;
  --accent: #00ff88;
  --border: rgba(255, 255, 255, 0.1);
  --shadow: 0 4px 16px rgba(0, 0, 0, 0.3);
  
  --radius-sm: 2px;
  --radius-md: 4px;
  --radius-lg: 6px;
  
  --button-height: 48px;
  --section-padding: 140px;
  --card-gap: 32px;
  --transition-speed: 0.15s;
}

[data-theme="refined"] {
  --bg: #f8f7f5;
  --surface: #ffffff;
  --surface-alt: #f2f1ee;
  --text: #2a2a2a;
  --muted: #707070;
  --accent: #8b6b4a;
  --border: rgba(0, 0, 0, 0.06);
  --shadow: 0 1px 4px rgba(0, 0, 0, 0.06);
  
  --radius-sm: 8px;
  --radius-md: 12px;
  --radius-lg: 16px;
  
  --button-height: 46px;
  --section-padding: 100px;
  --card-gap: 28px;
  --transition-speed: 0.25s;
}
```

## Typography Scale Examples

### Option 1: Single Font System
```css
:root {
  --font-primary: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
  
  --text-hero: clamp(48px, 8vw, 96px);
  --text-h1: clamp(40px, 6vw, 72px);
  --text-h2: clamp(32px, 4.5vw, 56px);
  --text-h3: clamp(24px, 3vw, 40px);
  --text-body-lg: clamp(18px, 2vw, 21px);
  --text-body: 16px;
  --text-small: 14px;
  
  --weight-normal: 400;
  --weight-medium: 500;
  --weight-bold: 600;
}
```

### Option 2: Dual Font System
```css
:root {
  --font-display: 'Sohne', 'Helvetica Neue', sans-serif;
  --font-body: 'Inter', -apple-system, sans-serif;
  
  /* Display scale */
  --text-hero: clamp(48px, 8vw, 96px);
  --text-h1: clamp(40px, 6vw, 72px);
  --text-h2: clamp(32px, 4.5vw, 56px);
  
  /* Body scale */
  --text-body-lg: clamp(18px, 2vw, 21px);
  --text-body: 16px;
  --text-small: 14px;
}
```

## Component Specifications

### Button System

```css
/* Base button structure */
.btn {
  height: var(--button-height);
  padding: 0 32px;
  border-radius: var(--radius-md);
  font-size: 15px;
  font-weight: 500;
  transition: all var(--transition-speed) ease;
  border: 1px solid var(--border);
}

/* Theme-aware variants */
[data-theme="precise"] .btn-primary {
  background: var(--text);
  color: var(--bg);
  border: none;
}

[data-theme="bold"] .btn-primary {
  background: var(--accent);
  color: var(--bg);
  border: 2px solid var(--accent);
  box-shadow: 0 0 20px rgba(0, 255, 136, 0.2);
}

[data-theme="refined"] .btn-primary {
  background: transparent;
  color: var(--text);
  border: 1px solid var(--text);
}
```

### Card System

```css
.card {
  background: var(--surface);
  border-radius: var(--radius-lg);
  border: 1px solid var(--border);
  padding: 32px;
  transition: all var(--transition-speed) ease;
}

[data-theme="precise"] .card:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.06);
}

[data-theme="bold"] .card:hover {
  border-color: var(--accent);
  box-shadow: 0 8px 32px rgba(0, 255, 136, 0.1);
}

[data-theme="refined"] .card:hover {
  background: var(--surface-alt);
  box-shadow: var(--shadow);
}
```

## Section Structure Template

```html
<section data-theme="precise" class="section-hero">
  <div class="container">
    <!-- Section content -->
  </div>
</section>

<section data-theme="bold" class="section-services">
  <div class="container">
    <!-- Section content -->
  </div>
</section>

<section data-theme="refined" class="section-work">
  <div class="container">
    <!-- Section content -->
  </div>
</section>
```

## Grid & Spacing System

```css
:root {
  --container-max: 1280px;
  --container-padding: clamp(20px, 5vw, 80px);
  
  --space-xs: 8px;
  --space-sm: 16px;
  --space-md: 24px;
  --space-lg: 48px;
  --space-xl: 80px;
  --space-2xl: 120px;
}

.container {
  max-width: var(--container-max);
  margin: 0 auto;
  padding: 0 var(--container-padding);
}

.section {
  padding: var(--section-padding) 0;
}
```

## Responsive Breakpoints

```css
/* Mobile first approach */
@media (min-width: 640px) {
  /* Tablet */
}

@media (min-width: 1024px) {
  /* Desktop */
}

@media (min-width: 1440px) {
  /* Large desktop */
}
```

## Animation Utilities

```css
/* Subtle reveal on scroll */
.reveal {
  opacity: 0;
  transform: translateY(20px);
  transition: opacity 0.6s ease, transform 0.6s ease;
}

.reveal.visible {
  opacity: 1;
  transform: translateY(0);
}

/* Theme transition */
section {
  transition: 
    background-color 0.4s ease,
    color 0.4s ease;
}
```

## Case Study Preview Component

```html
<article class="case-preview">
  <div class="case-visual">
    <!-- Image or visual frame -->
  </div>
  <div class="case-info">
    <div class="case-meta">
      <span class="discipline-tag">Brand</span>
      <span class="discipline-tag">Web</span>
    </div>
    <h3 class="case-title">Monolith Ventures</h3>
    <p class="case-description">
      Investment platform identity and digital presence
    </p>
  </div>
</article>
```

## Quality Indicators

### Premium indicators:
- Generous whitespace
- Precise alignment
- Controlled hierarchy
- Smooth interactions
- Clear typography
- Balanced contrast
- Intentional details

### Non-premium indicators (fix these):
- Cramped spacing
- Misalignment
- Too many styles
- Janky interactions
- Poor readability
- Harsh contrast jumps
- Random decorations
