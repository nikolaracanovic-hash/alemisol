# Implementation Examples

## Example 1: Hero Section Transformation

### Before (Template-Like)

```html
<section class="hero">
  <div class="container">
    <h1>We Build Digital Experiences</h1>
    <p>Innovative solutions for modern businesses</p>
    <button>Get Started</button>
  </div>
</section>
```

**Problems:**
- Generic marketing copy
- No brand character
- Template structure
- No theme system

### After (Premium Studio)

```html
<section data-theme="precise" class="hero">
  <div class="container">
    <div class="hero-content">
      <h1 class="hero-title">
        Web studio for<br>
        brands with clarity
      </h1>
      <p class="hero-subtitle">
        Design systems, digital products, and brand platforms<br>
        built with precision and contemporary craft.
      </p>
      <a href="#contact" class="btn btn-primary">Start a project</a>
    </div>
  </div>
</section>
```

**Improvements:**
- Clear positioning
- Concrete language
- Theme system in place
- Professional tone
- Specific value proposition

## Example 2: Services Section with Theme Transition

```html
<section data-theme="bold" class="services">
  <div class="container">
    <div class="section-header">
      <span class="section-label">What we do</span>
      <h2>Services built for control and scale</h2>
    </div>
    
    <div class="services-grid">
      <article class="service-card">
        <h3>Brand Systems</h3>
        <p>Visual identity, guidelines, and digital application</p>
      </article>
      
      <article class="service-card">
        <h3>Web Platforms</h3>
        <p>Marketing sites, web apps, and product interfaces</p>
      </article>
      
      <article class="service-card">
        <h3>Design Systems</h3>
        <p>Component libraries, tokens, and documentation</p>
      </article>
    </div>
  </div>
</section>
```

**Key points:**
- Theme changes from "precise" to "bold"
- Copy is concrete, not generic
- Structure is clear
- No unnecessary decoration

## Example 3: Case Study Grid

### Good Implementation

```html
<section data-theme="refined" class="work">
  <div class="container">
    <div class="section-header">
      <h2>Selected work</h2>
    </div>
    
    <div class="cases-grid">
      <article class="case-preview">
        <div class="case-visual">
          <img src="cases/monolith.jpg" alt="Monolith Ventures">
        </div>
        <div class="case-info">
          <div class="case-meta">
            <span class="tag">Brand</span>
            <span class="tag">Digital</span>
          </div>
          <h3>Monolith Ventures</h3>
          <p>Investment platform identity and web presence</p>
        </div>
      </article>
      
      <article class="case-preview">
        <div class="case-visual">
          <img src="cases/archive.jpg" alt="Archive">
        </div>
        <div class="case-info">
          <div class="case-meta">
            <span class="tag">Platform</span>
            <span class="tag">UX</span>
          </div>
          <h3>Archive</h3>
          <p>Document management system for legal teams</p>
        </div>
      </article>
    </div>
  </div>
</section>
```

**Why this works:**
- Project names sound real
- Descriptions are specific
- Tags indicate actual disciplines
- No generic "Project One" naming
- Structure supports premium presentation

## Example 4: CSS Theme System Implementation

```css
/* Global base */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: var(--font-body);
  color: var(--text);
  background: var(--bg);
  line-height: 1.6;
  -webkit-font-smoothing: antialiased;
}

/* Section theming */
section {
  background: var(--bg);
  color: var(--text);
  transition: background-color 0.4s ease, color 0.4s ease;
}

/* Component theming */
.btn {
  background: var(--surface);
  color: var(--text);
  border: 1px solid var(--border);
  border-radius: var(--radius-md);
  padding: 0 32px;
  height: var(--button-height);
  font-weight: 500;
  transition: all var(--transition-speed) ease;
  cursor: pointer;
}

.btn:hover {
  transform: translateY(-1px);
  box-shadow: var(--shadow);
}

.card {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: var(--radius-lg);
  padding: 32px;
  transition: all var(--transition-speed) ease;
}
```

## Example 5: Minimal JavaScript Theme Control

```javascript
// Detect active section and apply theme
const sections = document.querySelectorAll('section[data-theme]');
const themeContainer = document.body;

const observer = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting && entry.intersectionRatio > 0.5) {
      const theme = entry.target.getAttribute('data-theme');
      themeContainer.setAttribute('data-theme', theme);
    }
  });
}, {
  threshold: [0.5]
});

sections.forEach(section => observer.observe(section));
```

## Example 6: Responsive Section

```html
<section data-theme="precise" class="about">
  <div class="container">
    <div class="about-grid">
      <div class="about-content">
        <h2>Studio focused on<br>clarity and craft</h2>
        <p>We work with clients who value precise execution, clear systems, and long-term quality over trend-chasing.</p>
        <p>Our approach combines brand thinking, interface design, and technical architecture.</p>
      </div>
      
      <div class="about-details">
        <div class="detail-item">
          <h4>Established</h4>
          <p>2021</p>
        </div>
        <div class="detail-item">
          <h4>Location</h4>
          <p>Belgrade</p>
        </div>
        <div class="detail-item">
          <h4>Team</h4>
          <p>4 people</p>
        </div>
      </div>
    </div>
  </div>
</section>
```

**CSS:**
```css
.about-grid {
  display: grid;
  gap: 64px;
}

@media (min-width: 1024px) {
  .about-grid {
    grid-template-columns: 1.5fr 1fr;
    gap: 80px;
  }
}

.about-content h2 {
  font-size: var(--text-h2);
  margin-bottom: 32px;
  line-height: 1.2;
}

.about-content p {
  font-size: var(--text-body-lg);
  color: var(--muted);
  margin-bottom: 20px;
}

.detail-item {
  padding: 24px 0;
  border-bottom: 1px solid var(--border);
}

.detail-item h4 {
  font-size: 14px;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  color: var(--muted);
  margin-bottom: 8px;
}

.detail-item p {
  font-size: 18px;
  font-weight: 500;
}
```

## Example 7: Before/After Copy Quality

### Before (Forbidden)
```
Hero: "Elevating brands through cutting-edge digital solutions"
Services: "We craft pixel-perfect experiences"
About: "Our passionate team delivers transformative design"
CTA: "Ready to take your brand to the next level?"
```

### After (Professional)
```
Hero: "Web studio for brands with clarity"
Services: "Design systems, digital products, and brand platforms"
About: "Studio focused on clarity and craft"
CTA: "Start a project"
```

## Example 8: Navigation System

```html
<nav class="nav">
  <div class="nav-container">
    <a href="#" class="nav-logo">Studio</a>
    
    <div class="nav-links">
      <a href="#work">Work</a>
      <a href="#services">Services</a>
      <a href="#about">About</a>
      <a href="#contact" class="btn btn-small">Contact</a>
    </div>
    
    <button class="nav-toggle" aria-label="Menu">
      <span></span>
      <span></span>
    </button>
  </div>
</nav>
```

**CSS:**
```css
.nav {
  position: fixed;
  top: 0;
  width: 100%;
  z-index: 1000;
  background: var(--bg);
  border-bottom: 1px solid var(--border);
  backdrop-filter: blur(10px);
}

.nav-container {
  max-width: var(--container-max);
  margin: 0 auto;
  padding: 0 var(--container-padding);
  height: 80px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.nav-links {
  display: none;
  gap: 40px;
}

@media (min-width: 768px) {
  .nav-links {
    display: flex;
  }
  
  .nav-toggle {
    display: none;
  }
}
```

## Common Mistakes to Avoid

### Mistake 1: Over-Styling Without System
```css
/* Bad - random values without system */
.hero { padding: 137px 0; }
.services { padding: 93px 0; }
.work { padding: 156px 0; }
```

```css
/* Good - systematic spacing */
.section { padding: var(--section-padding) 0; }

[data-theme="precise"] { --section-padding: 120px; }
[data-theme="bold"] { --section-padding: 140px; }
[data-theme="refined"] { --section-padding: 100px; }
```

### Mistake 2: Too Many Font Sizes

```css
/* Bad - too many arbitrary sizes */
.title-1 { font-size: 72px; }
.title-2 { font-size: 68px; }
.title-3 { font-size: 64px; }
.subtitle-1 { font-size: 22px; }
.subtitle-2 { font-size: 20px; }
```

```css
/* Good - clear hierarchy */
h1 { font-size: var(--text-h1); }
h2 { font-size: var(--text-h2); }
h3 { font-size: var(--text-h3); }
.body-large { font-size: var(--text-body-lg); }
```

### Mistake 3: Aggressive Animation

```css
/* Bad - too much motion */
.card {
  transition: all 0.3s cubic-bezier(0.68, -0.55, 0.265, 1.55);
}

.card:hover {
  transform: scale(1.15) rotate(2deg);
  box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
}
```

```css
/* Good - subtle and controlled */
.card {
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}

.card:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.06);
}
```

## HTML Structure Best Practice

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Studio Name</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body data-theme="precise">
  
  <nav class="nav">
    <!-- Navigation -->
  </nav>
  
  <main>
    <section data-theme="precise" class="hero">
      <!-- Hero content -->
    </section>
    
    <section data-theme="bold" class="services">
      <!-- Services content -->
    </section>
    
    <!-- More sections -->
  </main>
  
  <footer class="footer">
    <!-- Footer -->
  </footer>
  
  <script src="script.js"></script>
</body>
</html>
```

## Real-World Case Names (Good Examples)

Instead of generic names, use believable project names:

**Good:**
- Monolith Ventures (investment platform)
- Archive (document management)
- Stride (fitness tracking platform)
- Kaleido (event management system)
- Foundry (manufacturing operations)
- Meridian (logistics platform)
- Vantage (analytics dashboard)
- Nexus Labs (research portal)

**Bad:**
- Project One
- Client Website
- Startup App
- Business Portal
- Modern Brand
- Creative Project

## File Organization Example

```
project/
├── index.html
├── styles/
│   ├── base.css          # Reset, variables
│   ├── themes.css        # Theme definitions
│   ├── components.css    # Buttons, cards, etc.
│   ├── sections.css      # Section-specific styles
│   └── responsive.css    # Media queries
├── scripts/
│   └── theme.js         # Theme detection
└── assets/
    ├── images/
    └── fonts/
```

## Minimal JavaScript Pattern

Keep JavaScript minimal and purposeful:

```javascript
// Theme detection
const applyTheme = () => {
  const sections = document.querySelectorAll('section[data-theme]');
  
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting && entry.intersectionRatio > 0.5) {
        const theme = entry.target.getAttribute('data-theme');
        document.body.setAttribute('data-theme', theme);
      }
    });
  }, { threshold: [0.5] });
  
  sections.forEach(section => observer.observe(section));
};

// Mobile menu
const initMobileMenu = () => {
  const toggle = document.querySelector('.nav-toggle');
  const menu = document.querySelector('.nav-links');
  
  toggle?.addEventListener('click', () => {
    menu?.classList.toggle('active');
  });
};

// Initialize
document.addEventListener('DOMContentLoaded', () => {
  applyTheme();
  initMobileMenu();
});
```

## Process Section Example

```html
<section data-theme="refined" class="process">
  <div class="container">
    <h2>Clear process</h2>
    
    <div class="process-steps">
      <div class="step">
        <span class="step-number">01</span>
        <h3>Discovery</h3>
        <p>Understanding goals, constraints, and opportunities</p>
      </div>
      
      <div class="step">
        <span class="step-number">02</span>
        <h3>Strategy</h3>
        <p>Defining direction, positioning, and system architecture</p>
      </div>
      
      <div class="step">
        <span class="step-number">03</span>
        <h3>Execution</h3>
        <p>Design, development, and refinement</p>
      </div>
      
      <div class="step">
        <span class="step-number">04</span>
        <h3>Launch</h3>
        <p>Delivery, documentation, and ongoing support</p>
      </div>
    </div>
  </div>
</section>
```

## Contact CTA Example

```html
<section data-theme="precise" class="contact">
  <div class="container">
    <div class="contact-content">
      <h2>Start a project</h2>
      <p>Reach out to discuss your needs and timeline.</p>
      
      <div class="contact-methods">
        <a href="mailto:studio@example.com" class="contact-link">
          studio@example.com
        </a>
        <a href="https://instagram.com/studio" class="contact-link">
          Instagram
        </a>
      </div>
    </div>
  </div>
</section>
```

**Key principles:**
- Direct and clear
- No aggressive sales language
- Professional tone
- Simple structure
- Easy to act on

## Footer Example

```html
<footer class="footer">
  <div class="container">
    <div class="footer-grid">
      <div class="footer-brand">
        <h3>Studio</h3>
        <p>Web and brand systems</p>
      </div>
      
      <div class="footer-links">
        <a href="#work">Work</a>
        <a href="#services">Services</a>
        <a href="#about">About</a>
        <a href="#contact">Contact</a>
      </div>
      
      <div class="footer-social">
        <a href="#">Instagram</a>
        <a href="#">LinkedIn</a>
      </div>
    </div>
    
    <div class="footer-bottom">
      <p>© 2026 Studio. All rights reserved.</p>
    </div>
  </div>
</footer>
```

## Visual Hierarchy Example

```css
/* Clear hierarchy through size and weight */
.section-label {
  font-size: 12px;
  text-transform: uppercase;
  letter-spacing: 0.1em;
  color: var(--muted);
  font-weight: 500;
  margin-bottom: 16px;
  display: block;
}

.section-title {
  font-size: var(--text-h2);
  line-height: 1.2;
  margin-bottom: 24px;
  font-weight: 600;
}

.section-description {
  font-size: var(--text-body-lg);
  color: var(--muted);
  max-width: 640px;
}
```

## Mobile-First Responsive Pattern

```css
/* Mobile base (default) */
.services-grid {
  display: grid;
  gap: 24px;
}

.service-card {
  padding: 24px;
}

/* Tablet */
@media (min-width: 640px) {
  .services-grid {
    grid-template-columns: repeat(2, 1fr);
    gap: 32px;
  }
}

/* Desktop */
@media (min-width: 1024px) {
  .services-grid {
    grid-template-columns: repeat(3, 1fr);
    gap: 40px;
  }
  
  .service-card {
    padding: 32px;
  }
}
```
