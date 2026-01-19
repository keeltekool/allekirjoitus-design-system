# Allekirjoitus.fi Website - Session Handoff

**Date:** January 19, 2026
**Status:** English clone COMPLETE and verified

---

## What's Done

### Files Ready
| File | Status | Path |
|------|--------|------|
| English clone | ✅ Complete | `website/en/index.html` |
| Finnish clone | ✅ Complete | `website/index.html` |
| Design docs | ✅ v1.13 | `allekirjoitus-fi-web.md` |
| Fonts | ✅ Ready | `assets/fonts/Metropolis-*.otf` |
| Logos | ✅ Ready | `assets/logos/` |

### English Clone Verified Against Live Site
- All text content matches https://allekirjoitus.fi/en/ exactly
- Package titles: "S package", "M package", etc. (lowercase)
- Section title: "Electronic Signature Packages" (capital S, P)
- Enterprise list: `›` arrow markers (black, not orange)
- Button text: "Send Message" (capital M)
- Descriptions end with periods

---

## Quick Start Commands

```bash
# Start local server
cd "G:\My Drive\SK_RE\Allekirjoitus_DesignSystem\website"
npx serve -l 3000

# View English: http://localhost:3000/en/
# View Finnish: http://localhost:3000/
```

---

## Next Task: Updated Copy

The English version (`website/en/index.html`) is the basis for new content.

**To edit copy:**
- Hero headline: line ~834-837
- About sections: lines ~855-875
- Benefits: lines ~893-922
- Pricing: lines ~937-988
- FAQ questions: lines ~1047-1095
- Contact: lines ~1103-1112

---

## Key Files to Reference

- **Skill:** `/allekirjoitus-fi-web` - loads design guidelines
- **Design docs:** `allekirjoitus-fi-web.md` (v1.13)
- **English HTML:** `website/en/index.html`

---

## CSS Quick Reference

```css
/* Colors */
--allekirjoitus-orange: #ef4224;
--allekirjoitus-orange-alt: #e23013;  /* Buttons */
--text-black: #000000;                /* Headings */
--allekirjoitus-text: #010101;        /* Body */

/* Fonts */
font-family: 'Metropolis'             /* Body */
font-family: 'Barlow Condensed'       /* Headings */
```

---

*Start new session, say: "Continue Allekirjoitus project - updating copy for English page"*

---

## GitHub Sync (Home PC Only)

> **Note:** This section only applies when working from the **home PC** (with GitHub access).
> If you're on the **work laptop**, ignore this completely - just work locally as normal.

**Repository:** https://github.com/keeltekool/allekirjoitus-design-system

**Live preview:** https://keeltekool.github.io/allekirjoitus-design-system/website/en/index.html

**Workflow (home PC only):**
1. Make changes locally in Google Drive folder
2. Tell Claude: "sync to GitHub" or "push latest changes"
3. Claude detects changes, commits, and pushes
4. Live GitHub Pages URL updates automatically

**Why this exists:** GitHub hosting allows sharing the prototype with external parties via a public URL, without needing to send files or set up hosting.
