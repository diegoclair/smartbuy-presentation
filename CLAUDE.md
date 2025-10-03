# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

SmartBuy Presentation is a **static investor pitch deck** built with Reveal.js. This is NOT an interactive website - it's a presentation designed to be shown to investors. All design and interaction decisions must reflect this purpose.

## Development Commands

```bash
# Install dependencies
npm install

# Run local development server (fixed port 5000)
npm run dev
# Access at: http://localhost:5000

# Deploy to Surge.sh
npm run deploy
# Live at: https://smartbuy-pitch.surge.sh

# Prepare for GitHub Pages
npm run deploy:github
```

## Architecture

### Tech Stack
- **Reveal.js 4.6.1** - Presentation framework
- **Static HTML/CSS** - No build process, no JavaScript frameworks
- **Google Fonts (Inter)** - Typography
- **Font Awesome 6.5.1** - Icons
- **CDN-based** - All libraries loaded from CDN

### File Structure
```
smartbuy-presentation/
├── index.html              # Main presentation file (all slides)
├── styles/
│   └── main.css           # Primary stylesheet (56KB)
├── styles.css             # Legacy styles (may be deprecated)
├── assets/
│   ├── logo.png           # SmartBuy logo
│   ├── videos/            # Demo videos (3 files, optimized)
│   └── team-photos/       # Founder photos
├── package.json           # NPM scripts only (no build)
└── README.md              # Detailed slide structure & data
```

### Key Architecture Decisions

1. **Single HTML File**: All slides are in `index.html` - no routing, no components
2. **Dual CSS System**: `styles/main.css` (56KB primary) + `styles.css` (legacy, check before modifying)
3. **Video Strategy**: Optimized MP4s with `muted`, `playsinline`, and `preload="auto"` attributes
4. **Responsive Design**: Uses `clamp()` for fluid typography, CSS Grid/Flexbox for layout
5. **No JavaScript**: Reveal.js handles all interactions, no custom JS

## Design Philosophy - CRITICAL

### This is a PRESENTATION, not a website

**NEVER ADD:**
- ❌ Hover effects (`:hover`)
- ❌ Animations (`@keyframes`, `animation:`)
- ❌ Transitions (`transition:`)
- ❌ Interactive transforms (`transform` on hover)
- ❌ Backdrop filters
- ❌ Scrolling (everything must fit viewport)
- ❌ Colored shadows/glows (neon effects)
- ❌ `min-height: 100vh` (causes layout issues)

**ALWAYS MAINTAIN:**
- ✅ Clean, professional design
- ✅ Content fits in viewport (no scroll)
- ✅ High contrast typography
- ✅ Brand color palette (#4a90e2 primary, #6bb6ff secondary, #1a1a1a background)
- ✅ Subtle gradients on cards
- ✅ Discrete shadows (black/gray only)

### Brand Colors
```css
Primary:   #4a90e2  /* SmartBuy blue - titles */
Secondary: #6bb6ff  /* Light blue - accents */
Background: #1a1a1a /* Dark background */
Text:      #cccccc  /* Light gray - body text */
```

## Content Management Rules

### When Modifying Slide Data

**CRITICAL**: Any change to slide content MUST update [README.md](README.md) section "🎯 Estrutura da Apresentação"

1. **Update README.md** when changing:
   - Statistics or numbers
   - Business model data (TAM/SAM/SOM, revenue streams, unit economics)
   - Market data or sources
   - Slide objectives or messaging

2. **Maintain Consistency** across:
   - TAM/SAM/SOM must align with Business Model slide
   - Market data must match across all slides
   - Revenue streams must be consistent

3. **Validate Sources**: Always cite year (2024/2025) and source

4. **Test**: Run `npm run dev` after significant changes

### Data Integrity
- README.md contains extensive validated statistics with sources
- All numbers in slides must match README documentation
- Cross-reference Confluence SmartBuy data when available (see README section "📊 Dados Estatísticos Comprovados")

## Presentation Controls

- **Arrow keys / Space**: Navigate slides
- **ESC**: Overview mode
- **F**: Fullscreen
- **S**: Speaker notes (if implemented)

## Deployment

- **Primary**: Surge.sh at https://smartbuy-pitch.surge.sh
- **Alternative**: GitHub Pages (commit to main, enable in Settings)
- **Cache Control**: Headers configured in `index.html` for no-cache (force fresh content)

## Working with This Codebase

1. **Before editing styles**: Check both `styles/main.css` and `styles.css` to understand which is active
2. **Before changing slides**: Read corresponding section in README.md
3. **After content changes**: Update README.md structure section
4. **Test locally**: Always run `npm run dev` before deploying
5. **No build step**: Changes are immediate, refresh browser to see updates

---

*This is a static presentation for investor pitches. Keep it professional, clean, and distraction-free.*
