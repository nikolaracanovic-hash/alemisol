---
name: multilingual-website
description: Build bilingual websites with Serbian and English support, Serbian as default. Use when creating multilingual sites, implementing language switchers, or when user mentions multiple languages, i18n, or translation features.
---

# Multilingual Website (Serbian/English)

Build professional bilingual websites with Serbian as default language and seamless English switching.

## Core Requirements

Every multilingual implementation must have:
- Serbian as default language on first load
- Clean language switcher UI
- Persistent language choice (localStorage)
- All text content in both languages
- No broken layout when switching languages
- Professional UX without flags or awkward UI

## Implementation Pattern

### 1. Language Data Structure

Store translations in clean data objects:

```javascript
const translations = {
  sr: {
    nav: {
      home: "Početna",
      about: "O nama",
      services: "Usluge",
      contact: "Kontakt"
    },
    hero: {
      title: "Kreiramo digitalna rešenja",
      subtitle: "Studio za web dizajn i razvoj"
    }
  },
  en: {
    nav: {
      home: "Home",
      about: "About",
      services: "Services",
      contact: "Contact"
    },
    hero: {
      title: "We create digital solutions",
      subtitle: "Web design and development studio"
    }
  }
};
```

### 2. Language State Management

```javascript
let currentLang = localStorage.getItem('lang') || 'sr';

function setLanguage(lang) {
  currentLang = lang;
  localStorage.setItem('lang', lang);
  updateContent();
}

function updateContent() {
  document.querySelectorAll('[data-i18n]').forEach(el => {
    const key = el.getAttribute('data-i18n');
    const keys = key.split('.');
    let value = translations[currentLang];
    keys.forEach(k => value = value[k]);
    el.textContent = value;
  });
}
```

### 3. HTML Structure

```html
<nav>
  <a href="#" data-i18n="nav.home">Početna</a>
  <a href="#" data-i18n="nav.about">O nama</a>
  
  <div class="lang-switcher">
    <button class="lang-btn active" data-lang="sr">SR</button>
    <button class="lang-btn" data-lang="en">EN</button>
  </div>
</nav>

<section>
  <h1 data-i18n="hero.title">Kreiramo digitalna rešenja</h1>
  <p data-i18n="hero.subtitle">Studio za web dizajn i razvoj</p>
</section>
```

## Language Switcher Design

The switcher must be:
- Visible but not intrusive
- Clear about current language
- Simple to use
- Consistent with site design system

Preferred placement:
- Top right corner of navigation
- Footer for secondary access
- Both locations for maximum accessibility

Style guidance:
- Use language codes (SR/EN) not flags
- Clear active state
- Smooth transition
- Matches theme system

```css
.lang-switcher {
  display: flex;
  gap: 0.5rem;
}

.lang-btn {
  padding: 0.5rem 1rem;
  border: 1px solid var(--border);
  background: transparent;
  color: var(--text);
  cursor: pointer;
  transition: all 0.2s;
}

.lang-btn.active {
  background: var(--accent);
  color: var(--bg);
  border-color: var(--accent);
}
```

## Content Strategy

### Serbian Content
- Default language
- Professional tone
- Clear and concise
- No machine translation feel
- Natural phrasing

### English Content
- Professional international tone
- Clean grammar
- Equivalent meaning (not word-for-word)
- Culturally appropriate

### Translation Quality Rules
- Never use obvious machine translation
- Keep brand voice consistent across languages
- Adjust idioms and phrases culturally
- Maintain same content structure
- Same heading hierarchy
- Same call-to-action strength

## Technical Checklist

Before completing multilingual implementation:

- [ ] Serbian is default on first load
- [ ] Language choice persists on refresh
- [ ] All visible text has translations
- [ ] Switcher works on all pages/sections
- [ ] No layout breaks when switching
- [ ] Active language is clearly indicated
- [ ] Both languages sound natural
- [ ] Mobile switcher is accessible
- [ ] Theme changes work in both languages

## Common Mistakes to Avoid

**Don't:**
- Use flags instead of language codes
- Make English the default
- Leave untranslated strings
- Use Google Translate copy-paste
- Create separate HTML files per language
- Break mobile layout with switcher
- Make switcher too prominent
- Use confusing language labels

**Do:**
- Keep it simple and clean
- Test both languages thoroughly
- Maintain visual consistency
- Write natural-sounding copy
- Use semantic HTML structure
- Keep switcher accessible

## Integration with Theme System

Language switcher must respect current theme:

```css
[data-theme="minimal"] .lang-btn {
  border-radius: var(--radius-sm);
}

[data-theme="bold"] .lang-btn {
  border-radius: 0;
  border-width: 2px;
}

[data-theme="refined"] .lang-btn {
  border-radius: var(--radius-md);
  box-shadow: var(--shadow);
}
```

## Initialization

Load and apply language immediately:

```javascript
document.addEventListener('DOMContentLoaded', () => {
  const savedLang = localStorage.getItem('lang') || 'sr';
  setLanguage(savedLang);
  
  document.querySelectorAll('.lang-btn').forEach(btn => {
    btn.addEventListener('click', () => {
      setLanguage(btn.dataset.lang);
    });
  });
});
```

## Final Rule

The multilingual system must be:
- Invisible to Serbian users (it just works)
- One click away for English users
- Professional and polished
- Integrated with existing design
- Not feeling like an afterthought
- Not breaking premium feel

If language switching feels clunky, complicated, or cheap—it's not good enough.
