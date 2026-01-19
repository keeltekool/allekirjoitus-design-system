# Allekirjoitus.fi Website Rebuild PRD
## Product Requirements Document - Copy Guidelines & Web Development Specifications

**Version:** 1.2
**Date:** January 19, 2026
**Status:** Ready for Copy Development & Implementation

---

## Document Purpose

This PRD serves as the **master reference** for:
1. **Copy Development** - Guidelines for writing final page copy
2. **Front-End Implementation** - Concrete specs for building the updated webpage

**IMPORTANT:** This document is a guide, not a rigid spec. Final implementation should optimize for logic, clarity, and conciseness. Avoid overly wordy copy.

---

## Project Context

### What Exists
- **Current page:** Transitional landing page at www.allekirjoitus.fi
- **Design System:** Fully documented in `allekirjoitus-fi-web.md` (v1.13)
- **Skill available:** `/allekirjoitus-fi-web` - loads design guidelines
- **Cloned pages:** `website/index.html` (FI) and `website/en/index.html` (EN)

### What We're Building
Transform the transitional page into a **full enterprise-focused product page** while:
- **Building exactly on top of the existing page structure** - maintain header, footer, login button placement, language switch, contact form
- Reusing the established design system completely
- Extending with new component patterns where needed (must align with existing style)
- Shifting content focus from SMB portal packages → Enterprise platform

### Key Constraint
**NOT overly wordy** - the page gains significant new content due to enterprise focus. Keep copy concise:
- Short, punchy headlines
- Bullet points over paragraphs
- Let structure/visuals work, minimize text walls
- 3-4 bullet points per feature card maximum

---

## PART 1: FRONT-END IMPLEMENTATION GUIDE

### Design System Reference

**MANDATORY:** Use the existing design system skill and documentation.

```
Skill: /allekirjoitus-fi-web
Design Doc: G:\My Drive\SK_RE\Allekirjoitus_DesignSystem\allekirjoitus-fi-web.md
Base Template: G:\My Drive\SK_RE\Allekirjoitus_DesignSystem\website\en\index.html
```

### What MUST Remain Unchanged

These elements from the existing page stay exactly as they are:

| Element | Keep As-Is |
|---------|-----------|
| Header structure | Logo left, nav center, login+lang right |
| Login button | Same placement, same style |
| Language switch | FI / EN toggle, same position |
| Contact form | Keep existing form structure and fields |
| Footer | Keep existing |

### Navigation Structure

**Updated navigation items:**

```
Platform | Pricing | FAQ | API | Contact | [Login button] | [FI|EN]
```

| Nav Item | Action |
|----------|--------|
| Platform | Scrolls to Enterprise Platform Capabilities section |
| Pricing | Scrolls to Pricing section (summary on main page) |
| FAQ | Scrolls to FAQ section |
| API | Links to API documentation (placeholder URL - to be provided) |
| Contact | Scrolls to Contact section |
| Login | External link to login portal (existing) |

### Page Structure (Section Order)

```
1. HEADER (existing - unchanged)
2. HERO (with single "Contact Us" CTA)
3. SERVICE EXPLAINER (What is Allekirjoitus.fi - Send/Sign/Done flow)
4. ENTERPRISE PLATFORM CAPABILITIES (4 feature cards)
5. SIGNING METHODS (AES vs SES)
6. PRICING (Enterprise summary + Portal packages, link to full pricing subpage)
7. TECHNICAL & LEGAL ASSURANCE
8. CLIENT LOGOS (lower position, subtle)
9. FAQ (placeholder - content to be provided separately)
10. CONTACT SECTION (existing form - unchanged)
11. FOOTER (existing - unchanged)
```

### Section Background Alternation

**MAINTAIN the existing pattern** - sections alternate white/gray:

```
Header              → WHITE (#ffffff)  [Fixed - unchanged]
Hero                → GRAY (#f2f2f2)
Service Explainer   → WHITE (#ffffff)
Enterprise Platform → GRAY (#f2f2f2)
Signing Methods     → WHITE (#ffffff)
Pricing             → GRAY (#f2f2f2)
Trust/Technical     → WHITE (#ffffff)
Client Logos        → GRAY (#f2f2f2)
FAQ                 → WHITE (#ffffff)
Contact             → DARK (#170703)   [Fixed - unchanged]
Footer              → WHITE (#ffffff)  [Fixed - unchanged]
```

### Existing Components to Reuse

| Component | Design Doc Reference | Usage |
|-----------|---------------------|-------|
| Hero Section | Lines 626-647 | Adapt for new headline, single CTA |
| Section Titles (H2) | 51px, Barlow Condensed, weight 500 | All main sections |
| Pricing Cards | Lines 262-305, 20px border-radius, LEFT-aligned | Enterprise + Portal packages |
| CTA Buttons | Lines 203-258, pill-shaped, 2px border | All CTAs → contact form |
| FAQ Accordion | Lines 330-357, plus (+) icon | FAQ section |
| Contact Section | Lines 386-427, dark bg + light form wrapper | Keep existing form |

### New Components Needed

These components don't exist in current design - **must be created in alignment with existing style**.

#### 1. Client Logo Bar
**Purpose:** Display 5 client reference logos (subtle, not prominent)

```css
.client-logos {
  background-color: #f2f2f2;
  padding: 3rem 0;
  text-align: center;
}

.client-logos-heading {
  font-family: 'Metropolis', sans-serif;
  font-size: 14px;
  font-weight: 500;
  color: #6b7280;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  margin-bottom: 2rem;
}

.client-logos-grid {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 3rem;
  flex-wrap: wrap;
}

.client-logo img {
  height: 40px;
  width: auto;
  filter: grayscale(100%);
  opacity: 0.7;
  transition: all 0.2s ease;
}

.client-logo img:hover {
  filter: grayscale(0%);
  opacity: 1;
}
```

#### 2. Feature Grid (Enterprise Platform Capabilities)
**Purpose:** Display 4 enterprise capability blocks in 2x2 grid

```css
.feature-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 2rem;
}

@media (max-width: 768px) {
  .feature-grid {
    grid-template-columns: 1fr;
  }
}

.feature-card {
  background: #ffffff;
  border: 1.6px solid #bebebe;
  border-radius: 20px;
  padding: 2rem;
  text-align: left;
}

.feature-card-icon {
  width: 48px;
  height: 48px;
  margin-bottom: 1rem;
  color: #ef4224;
}

.feature-card h3 {
  font-family: 'Barlow Condensed', sans-serif;
  font-size: 24px;
  font-weight: 500;
  color: #000000;
  margin-bottom: 0.75rem;
}

.feature-card p {
  font-family: 'Metropolis', sans-serif;
  font-size: 16px;
  line-height: 1.6;
  color: #010101;
  margin-bottom: 1rem;
}

.feature-card ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.feature-card li {
  font-size: 15px;
  color: #010101;
  padding-left: 1.25rem;
  position: relative;
  margin-bottom: 0.5rem;
}

.feature-card li::before {
  content: "›";
  position: absolute;
  left: 0;
  color: #ef4224;
}
```

#### 3. Signing Methods Comparison
**Purpose:** Show AES vs SES side by side

```css
.signing-methods {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 2rem;
}

@media (max-width: 768px) {
  .signing-methods {
    grid-template-columns: 1fr;
  }
}

.signing-method-card {
  background: #ffffff;
  border: 1.6px solid #bebebe;
  border-radius: 20px;
  padding: 2rem;
}

.signing-method-card.primary {
  border-color: #ef4224;
  border-width: 2px;
}

.signing-method-badge {
  display: inline-block;
  font-family: 'Metropolis', sans-serif;
  font-size: 12px;
  font-weight: 600;
  text-transform: uppercase;
  padding: 4px 12px;
  border-radius: 20px;
  margin-bottom: 1rem;
}

.signing-method-badge.standard {
  background-color: #ef4224;
  color: #ffffff;
}

.signing-method-badge.flexible {
  background-color: #f2f2f2;
  color: #010101;
}
```

#### 4. Two-Tier Pricing Layout
**Purpose:** Enterprise prominent, Portal packages de-emphasized

```
┌─────────────────────────────────────────────────────────────┐
│  ENTERPRISE PLATFORM (Full width, prominent)                │
│  ┌─────────────────────────────────────────────────────┐   │
│  │  Platform Fee: €275/mo                               │   │
│  │  • Unlimited Users  • API Access  • SSO             │   │
│  │  Transaction pricing summary                         │   │
│  │  [Contact Us] ← scrolls to contact form             │   │
│  │  "View full pricing →" ← links to pricing subpage   │   │
│  └─────────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│  SELF-SERVICE PACKAGES (Smaller, 3-column grid)             │
│  ┌───────────┐  ┌───────────┐  ┌───────────┐              │
│  │  S €15    │  │  M €45    │  │  L €85    │              │
│  │  10 sigs  │  │  35 sigs  │  │  80 sigs  │              │
│  │[Contact]  │  │[Contact]  │  │[Contact]  │              │
│  └───────────┘  └───────────┘  └───────────┘              │
└─────────────────────────────────────────────────────────────┘
```

**All buttons scroll to contact form.**

```css
.pricing-enterprise {
  background: #ffffff;
  border: 2px solid #ef4224;
  border-radius: 20px;
  padding: 3rem;
  margin-bottom: 3rem;
}

.pricing-portal-section {
  margin-top: 2rem;
}

.pricing-portal-heading {
  font-family: 'Metropolis', sans-serif;
  font-size: 14px;
  font-weight: 500;
  color: #6b7280;
  margin-bottom: 1.5rem;
}

.pricing-portal-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1.5rem;
}

@media (max-width: 768px) {
  .pricing-portal-grid {
    grid-template-columns: 1fr;
  }
}

.pricing-portal-card {
  background: #ffffff;
  border: 1.6px solid #bebebe;
  border-radius: 20px;
  padding: 1.5rem;
  text-align: left;
}
```

---

## PART 2: COPY DEVELOPMENT GUIDELINES

### Language

**English only** - Finnish version handled via existing language switch mechanism.

### Source Materials for Copy Writing

| Document | Contains | Location |
|----------|----------|----------|
| Price List 2026 | Exact pricing, tier definitions | `Enterprise_focused_copy/2026-3_Approval_of_Price_List...docx` |
| Service Terms | Technical definitions, legal terms | `Enterprise_focused_copy/Allekirjoitus_fi_Service_terms...docx` |
| Ideation Dump | Strategic direction, messaging | `Enterprise_focused_copy/Raw_ideating_dump.txt` |

### Copy Requirements Per Section

---

#### Section 1: HERO

**Elements:**
- Headline (H1): AES + Finnish Trust Network focus
- Sub-headline: 1-2 lines max
- Single CTA button: "Contact Us" → scrolls to contact form

**Constraints:**
- Finnish market primary
- No Telia Sign mention
- Lead with legal certainty

---

#### Section 2: CORE VALUE PROPOSITION

**Elements:**
- Section heading
- Brief lead paragraph (2-3 sentences max)
- 3-4 key trust points as short bullets:
  - Finnish Trust Network (Bank IDs, Mobile ID)
  - eIDAS AES compliance
  - PAdES format / independent verification
  - Nordic/Baltic coverage (secondary mention)

---

#### Section 3: ENTERPRISE PLATFORM CAPABILITIES

**4 Feature Cards (each card: title + 1 sentence + 3-4 bullets max):**

1. **System Integration**
   - REST API & Webhooks
   - Automated dispatch
   - Document templating
   - Real-time updates

2. **Security & Access**
   - SSO (Microsoft Entra ID)
   - Department hierarchy
   - Data isolation

3. **Brand Ownership**
   - Custom domains
   - White-label UI/emails/PDFs

4. **Smart Forms**
   - Online Forms (PDF → web)
   - Metadata extraction
   - Open Links

**CRITICAL:** Do NOT frame as comparison to Portal. These are core platform capabilities.

---

#### Section 4: SIGNING METHODS

**Two cards side by side:**

**AES Card (Primary - orange border):**
- Badge: "Standard"
- Title: "Advanced Electronic Signature"
- 2-3 bullet points (methods, use cases)
- Price: €0.80/signatory

**SES Card (Secondary - gray border):**
- Badge: "Flexible"
- Title: "Simple Electronic Signature"
- 2-3 bullet points (methods, use cases)
- Price: €0.65/signatory
- Note: Enterprise only

---

#### Section 5: PRICING

**Enterprise Block (prominent):**
- Heading
- Platform fee: €275/month
- What's included (3-4 bullets)
- Transaction pricing (brief table or list)
- CTA: "Contact Us" → contact form
- Link: "View full pricing" → pricing subpage

**Portal Packages Block (de-emphasized):**
- Small heading: "Self-Service Packages" or similar
- 3 cards: S €15, M €45, L €85
- Each with signatures/users
- CTA on each: "Contact Us" → contact form
- Footnote: Additional signatures €1.50, VAT 0%

---

#### Section 6: TECHNICAL & LEGAL ASSURANCE

**4-5 short trust points (can be icons + text or simple list):**
- EU eIDAS Regulation
- PDF/A → PAdES format
- Offline verification (Adobe Reader)
- GDPR: Customer = Controller, SK = Processor
- 90-day retention

---

#### Section 7: CLIENT LOGOS

**Subtle heading:** "Trusted by" or similar understated

**5 logos:**
1. LähiTapiola
2. Aktia
3. KPMG
4. Keyloop
5. Fennia

**LOGO FILES STATUS:** PLACEHOLDER - Logo files to be sourced separately and saved to `assets/client-logos/`. Use grayscale versions with hover-to-color effect.

---

#### Section 8: FAQ

**PLACEHOLDER** - Content to be provided separately.

Structure ready: Accordion with + icons (existing component)

Suggest 5-7 Q&A slots for enterprise-focused questions.

---

#### Section 9: CONTACT

**Keep existing form structure.**

Update heading/sub-text to align with enterprise focus if needed.

---

## PART 3: SUBPAGES

### Pricing Subpage

**URL:** `/pricing` or `/hinnasto`

**Content:** Full detailed pricing from Price List 2026:
- Enterprise Tier complete breakdown
  - Platform fee
  - All transaction fees
  - Add-ons (Nordic-Baltic auth, Online Forms, etc.)
  - Professional services hourly rates
- Basic Tier packages (S/M/L) details
- Terms footnotes

**Source:** `2026-3_Approval_of_Price_List...docx`

---

## PART 4: IMPLEMENTATION TASKS

### Pre-Development
- [ ] **Fetch client logos** and save to `assets/client-logos/`:
  - LähiTapiola
  - Aktia
  - KPMG
  - Keyloop
  - Fennia

### Copy Tasks
- [ ] Write Hero copy (headline, sub-headline, CTA)
- [ ] Write Core Value Proposition copy
- [ ] Write Enterprise Platform Capabilities (4 cards)
- [ ] Write Signing Methods copy (2 cards)
- [ ] Write Pricing section copy
- [ ] Write Technical Assurance copy
- [ ] Write Client Logos heading
- [ ] FAQ - placeholder structure only (content TBD)
- [ ] Update Contact section heading if needed
- [ ] Create Pricing subpage content

### Front-End Tasks
- [ ] Load design system skill (`/allekirjoitus-fi-web`)
- [ ] Update navigation (add Platform, API links)
- [ ] Build new sections following structure
- [ ] Create new components (logo bar, feature grid, signing cards, pricing layout)
- [ ] Create pricing subpage
- [ ] Ensure all CTAs scroll to contact form (except Login)
- [ ] Test responsive breakpoints

---

## Quick Reference

### Colors
```css
--allekirjoitus-orange: #ef4224;
--allekirjoitus-orange-alt: #e23013;
--text-black: #000000;
--allekirjoitus-text: #010101;
--gray-section: #f2f2f2;
--dark-section: #170703;
```

### Typography
```css
/* Body */ font-family: 'Metropolis'; font-size: 17px;
/* H1 Hero */ font-family: 'Barlow Condensed'; font-size: 78px; weight: 500;
/* H2 Section */ font-family: 'Barlow Condensed'; font-size: 51px; weight: 500;
/* H3 Feature */ font-family: 'Barlow Condensed'; font-size: 24px; weight: 500;
```

### Key Pricing (2026)
| Item | Price |
|------|-------|
| Enterprise Platform | €275/mo |
| AES Signing | €0.80/sig |
| SES Signing | €0.65/sig |
| SMS | €0.10/msg |
| Package S | €15/mo (10 sigs) |
| Package M | €45/mo (35 sigs) |
| Package L | €85/mo (80 sigs) |
| Additional sig | €1.50 |

### CTA Behavior
| Button | Action |
|--------|--------|
| Hero "Contact Us" | Scroll to contact form |
| Enterprise "Contact Us" | Scroll to contact form |
| Portal package buttons | Scroll to contact form |
| Nav "Contact" | Scroll to contact form |
| Nav "Login" | External link (unchanged) |
| "View full pricing" | Link to /pricing subpage |
| Nav "API" | Link to API docs (URL TBD) |

---

## Revision History

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | 2026-01-19 | Initial PRD |
| 1.1 | 2026-01-19 | Added front-end specs, component CSS |
| 1.2 | 2026-01-19 | Major update: Clarified build on existing page, single "Contact Us" CTA, all buttons → contact form, English only, FAQ placeholder, pricing subpage, navigation structure, removed ambiguities |

---

*This PRD is the master reference for copy development and web implementation.*
