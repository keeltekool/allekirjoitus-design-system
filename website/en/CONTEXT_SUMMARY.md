# Allekirjoitus.fi V3 Build Context Summary

## Project Location
- **Main page**: `G:\My Drive\SK_RE\Allekirjoitus_DesignSystem\website\en\index.html`
- **Design System**: `G:\My Drive\SK_RE\Allekirjoitus_DesignSystem\allekirjoitus-fi-web.md`
- **Assets**: `G:\My Drive\SK_RE\Allekirjoitus_DesignSystem\assets/`

## Design System Colors
```css
--allekirjoitus-orange: #ef4224;
--allekirjoitus-orange-alt: #e23013;
--allekirjoitus-orange-hover: #bd2605;
--text-black: #000000;
--allekirjoitus-text: #010101;
--allekirjoitus-gray-light: #f2f2f2;
--gray-border: #e5e5e5;
--gray-500: #6b7280;
--gray-600: #4b5563;
```

## Typography
- **H1 Hero**: Barlow Condensed, 78px, weight 500
- **H2 Section**: Barlow Condensed, 51px, weight 500
- **H3 Feature**: Barlow Condensed, 24px, weight 500
- **Body**: Metropolis, 17px

## Key Pricing Data (from PRD)

### Enterprise Tier - €275/month
**Platform includes:**
- Unlimited users
- API & webhook access
- SSO (Microsoft Entra ID)
- Custom branding & domains
- Department hierarchy management

**Transaction Fees:**
| Service | Price |
|---------|-------|
| Strong Signing (AES) | €0.80/signatory |
| Light Signing (SES) | €0.65/signatory |
| SMS Messages | €0.10/message |
| File Conversion (Word→PDF) | €0.25/document |

**Add-ons:**
| Service | Price |
|---------|-------|
| Nordic-Baltic Authentication | €50/month |
| Online Forms | €25/month per template |
| Organization Seal | Contact us |

**Professional Services:**
| Service | Rate |
|---------|------|
| Integration support | €150/hour |
| Custom development | €150/hour |
| Form creation | €150/hour |

### Basic Tier (Portal Packages)
| Package | Signatures/mo | Users | Price/mo |
|---------|---------------|-------|----------|
| Small (S) | 10 | 1 | €15 |
| Medium (M) | 35 | Up to 5 | €45 |
| Large (L) | 80 | Up to 10 | €85 |

**Basic Tier Includes:**
- Web portal access
- Strong authentication (Bank ID/Mobile ID)
- SMS codes for document retrieval
- 90-day archive

**Additional signatures:** €1.50 each

### Terms
- All prices VAT 0%
- Signature Request charged when document is dispatched
- Annual price adjustment based on CPI
- Customer responsible for document export before retention ends

## Page Structure Components Already Built
1. Header (logo, nav, login, lang switch)
2. Hero section
3. Service Explainer (Send/Sign/Done flow with cards)
4. Enterprise Platform Capabilities (4 feature cards)
5. Signing Methods (AES vs SES cards)
6. Pricing (compact two-column Enterprise + Portal packages)
7. Technical & Legal Assurance (5 trust icons)
8. Client Logos (5 real logos)
9. FAQ (11 items with accordion)
10. Contact form
11. Footer

## CSS Components Available
- `.section`, `.section-white`, `.section-gray`
- `.container`, `.container-narrow`
- `.section-title` (H2 styling)
- `.btn-outline`, `.btn-outline-sm`, `.btn-filled-sm`
- `.btn-text-link`
- Pricing card styles
- Feature card styles
- Table styles

## Next Task: Build /pricing subpage
Create `G:\My Drive\SK_RE\Allekirjoitus_DesignSystem\website\en\pricing.html`

Should include:
1. Same header/footer as main page
2. Full Enterprise Tier breakdown
3. Full Basic Tier packages
4. All add-ons and professional services
5. Terms and conditions
