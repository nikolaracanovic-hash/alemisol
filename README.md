# Alemisol — Studio Website

Professional single-page website for a web design and development studio brand.

## Structure

```
Alemisol/
├── index.html      — Main page structure
├── styles.css      — Theme system and all styling
├── script.js       — Mobile menu and theme transitions
└── README.md       — This file
```

## Theme System

The site uses 3 distinct visual modes through scroll:

1. **Intro** (Hero) — Clean, precise, minimal, premium
   - Light background
   - Soft shadows
   - Rounded elements
   - Subtle interactions

2. **Bold** (Services, Work, Process) — Technical, sharp, energetic
   - Dark background
   - Sharp corners
   - Stronger contrast
   - Direct interactions

3. **Refined** (About, Contact) — Calm, trustworthy, warm
   - Warm light background
   - Softer edges
   - Premium surfaces
   - Smooth transitions

All themes share the same brand DNA: typography, grid, spacing logic, and overall quality.

## Theme Variables

Each theme controls these CSS variables:
- Background colors (`--bg`, `--surface`, `--surface-alt`)
- Text colors (`--text`, `--muted`)
- Accent color (`--accent`)
- Border and shadow (`--border`, `--shadow`)
- Border radius values (`--radius-sm/md/lg`)
- Button height
- Transition speed

## Tech Stack

- Pure HTML/CSS/JS
- Inter font family
- Intersection Observer API for theme detection
- Mobile-first responsive design

## Running

Open `index.html` in a browser. No build step required.

For local testing with live reload:
```bash
# Using Python
python -m http.server 8000

# Or using Node
npx serve
```

Then open `http://localhost:8000` in your browser.

## Customization

1. **Change theme colors**: Edit CSS variables in `[data-theme="..."]` blocks
2. **Add content**: Replace placeholder case studies with real projects
3. **Adjust typography**: Modify font sizes in section-specific CSS
4. **Update copy**: Edit text in `index.html` to match your positioning

## Key Features

- Adaptive navigation that responds to current theme
- Smooth theme transitions while scrolling
- Mobile menu with clean animation
- Form ready for backend integration
- Subtle reveal animations
- Premium hover interactions
- Fully responsive design

## Notes

- Contact form logs to console; connect to backend when ready
- Case study placeholders have gradient backgrounds; replace with real images
- All copy written to avoid generic agency language
- Navigation adapts to dark sections automatically
