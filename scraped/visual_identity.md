# Allied Telesis - Complete Visual Identity Extraction

> Extracted 2026-03-03 from https://www.alliedtelesis.com/us/en via Chrome DevTools MCP

---

## 1. Brand Colors

### Primary Palette (from CSS custom properties)

| Role | Hex | RGB | CSS Variable |
|------|-----|-----|-------------|
| **Primary Blue** | `#4D738A` | rgb(77, 115, 138) | `--bs-primary`, `--bs-blue`, `--bs-blue-600` |
| **Bold Blue** (Hero BG) | `#003865` | rgb(0, 56, 101) | `--bs-bold-blue` |
| **Dark Blue** | `#2B424C` | rgb(43, 66, 76) | `--bs-dark-blue` |
| **Slate Blue** | `#304C5D` | rgb(48, 76, 93) | `--bs-slate-blue` |
| **Medium Blue** | `#44687D` | rgb(68, 104, 125) | `--bs-medium-blue` |
| **Dark Red** (CTA Buttons) | `#983222` | rgb(152, 50, 34) | `--bs-dark-red` |
| **Primary Red** | `#BE3A34` | rgb(190, 58, 52) | `--bs-primary-red` |
| **Gold** | `#EFBD47` | rgb(239, 189, 71) | `--bs-gold` |
| **Orange** | `#EFA63E` | rgb(239, 166, 62) | `--bs-orange` |
| **Burnt Orange** | `#CA7700` | rgb(202, 119, 0) | `--bs-burnt-orange` |
| **Green (Success)** | `#008542` | rgb(0, 133, 66) | `--bs-success`, `--bs-green` |

### Secondary / Neutral Palette

| Role | Hex | RGB | CSS Variable |
|------|-----|-----|-------------|
| **Body Text** | `#333333` | rgb(51, 51, 51) | `--bs-body-color`, `--bs-gray-800` |
| **Primary Black** | `#25282A` | rgb(37, 40, 42) | `--bs-primary-black` |
| **Black 900** | `#131313` | rgb(19, 19, 19) | `--bs-gray-900` |
| **Primary Gray** | `#7C878E` | rgb(124, 135, 142) | `--bs-primary-gray` |
| **Gray 500** | `#ACACAC` | rgb(172, 172, 172) | `--bs-gray-500` |
| **Gray 400 / Border** | `#D1D1D1` | rgb(209, 209, 209) | `--bs-gray-400` |
| **Gray 200** | `#E3E3E3` | rgb(227, 227, 227) | `--bs-border-color` |
| **Gray 100** | `#EEEEEE` | rgb(238, 238, 238) | `--bs-gray-100` |
| **Body Background** | `#F7F7F7` | rgb(247, 247, 247) | `--bs-body-bg`, `--bs-light` |
| **White** | `#FFFFFF` | rgb(255, 255, 255) | `--bs-white` |

### Extended Blue Scale (full Drupal theme scale)

| Shade | Hex | CSS Variable |
|-------|-----|-------------|
| Blue 900 | `#1E3745` | `--bs-blue-900` |
| Blue 800 | `#304C5D` | `--bs-blue-800` |
| Blue 700 | `#3E5F73` | `--bs-blue-700` |
| Blue 600 | `#4D738A` | `--bs-blue-600` (primary) |
| Blue 500 | `#5A829C` | `--bs-blue-500` |
| Blue 400 | `#74A6BA` | `--bs-blue-400` |
| Blue 300 | `#8BB8CA` | `--bs-blue-300` |
| Blue 200 | `#A8CEDD` | `--bs-blue-200` |
| Blue 100 | `#C3E3EF` | `--bs-blue-100` |
| Blue 50 | `#DEF5FF` | `--bs-blue-50` |
| Calm Blue | `#A6BCC6` | `--bs-calm-blue` |
| Bright Blue | `#8CB8C6` | `--bs-bright-blue` |
| Light Blue | `#D7DFE3` | `--bs-light-blue` |

### Link Colors

| State | Hex | RGB |
|-------|-----|-----|
| Default link | `#4D738A` | rgb(77, 115, 138) |
| Link hover | `#3E5C6E` | rgb(62, 92, 110) |
| Nav link (dark) | `#131313` | rgb(19, 19, 19) |
| Gray link (footer) | `#7C878E` | rgb(124, 135, 142) |
| Red accent link | `#983222` | rgb(152, 50, 34) |

### Button Styles

| Button Class | Background | Text Color | Usage |
|-------------|-----------|------------|-------|
| `btn-dark-red` | `#983222` | `#FFFFFF` | Primary CTA ("See all Customer Successes", "Discover our Flexible Network") |
| `btn-primary` | `#4D738A` | `#FFFFFF` | Secondary CTA ("Accept all", "Save preferences") |
| `btn-white` | `#FFFFFF` | `#000000` | Tertiary CTA ("Talk to us today", "View Datasheet") |
| `btn-blue` | `#4D738A` | `#FFFFFF` | Alternative blue CTA |

### SVG Logo Internal Colors

| Element | Hex | Usage |
|---------|-----|-------|
| Logo text/mark (dark) | `#231F20` | Used in `logo_color.svg` for wordmark |
| Logo "E" globe (red) | `#DF3127` | Used in `logo_color.svg` for the "e" globe mark |

---

## 2. Typography

### Font Stack
```css
font-family: "Yu Gothic", Meiryo, Roboto, "Libre Franklin", "Source Sans Pro",
  "Noto Sans JP", "system-ui", -apple-system, "Segoe UI", "Helvetica Neue",
  Arial, "Noto Sans", "Liberation Sans", sans-serif, "Apple Color Emoji",
  "Segoe UI Emoji", "Segoe UI Symbol", "Noto Color Emoji";
```

### Google Fonts Import
```
https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;500;700&display=swap
```

### Primary Font: **Roboto**
Loaded weights: 300 (Light), 400 (Regular), 500 (Medium), 700 (Bold)

### Type Scale

| Element | Size | Weight | Color | Line Height |
|---------|------|--------|-------|-------------|
| H1 | 51px (3rem) | 300 (Light) | `#FFFFFF` (on dark bg) | 56.1px |
| H2 | 34px (2rem) | 400 (Regular) | `#333333` | -- |
| H3 | 25.5px (1.5rem) | 500 (Medium) | `#333333` | -- |
| Body / p | 17px (1rem) | 300 (Light) | `#333333` | 25.5px (1.4) |
| Root font size | 1.0625rem (17px) | 300 | `#333333` | 1.4 |

---

## 3. Logo Assets

### Available Logo Variants (all SVG)

| Variant | URL | Size | Status |
|---------|-----|------|--------|
| **Color logo** (wordmark + red globe) | `https://www.alliedtelesis.com/themes/custom/themekit/dist/svg/logo_color.svg` | 4,445 bytes | 200 OK |
| **Black text logo** (header/footer) | `https://www.alliedtelesis.com/themes/custom/themekit/dist/svg/logo_text_black.svg` | 4,763 bytes | 200 OK |
| **White text logo** | `https://www.alliedtelesis.com/themes/custom/themekit/dist/svg/logo_text_white.svg` | 4,778 bytes | 200 OK |
| **Favicon** | `https://www.alliedtelesis.com/themes/custom/themekit/favicon.ico` | -- | 200 OK |
| **OG Share Image** (JPG) | `https://www.alliedtelesis.com/sites/default/files/image/2022-01/share-default.jpg` | 509,290 bytes | 200 OK |

### Logo Description
- The Allied Telesis logo is a custom wordmark "Allied Telesis" with a stylized "AT" monogram preceding it
- The monogram features angular/triangular geometric shapes
- The "e" in "Telesis" is replaced with a globe/sphere icon made of horizontal stripes (colored `#DF3127` red in the color variant)
- viewBox of the main wordmark SVG: `0 0 375 39` (very wide horizontal wordmark)
- Used as CSS background-image on `.logo` and `.footer-logo` elements

### Logo Usage on Site
- **Header**: `logo_text_black.svg` displayed as CSS background-image on `.logo.d-block` element
- **Footer**: `logo_text_black.svg` displayed as CSS background-image on `.footer-logo` element
- **JSON-LD Schema**: References `logo_color.svg` for structured data

---

## 4. Complete Image Inventory

### CDN Details
- **CDN Base Domain**: `www.alliedtelesis.com` (no separate CDN; served directly from Drupal)
- **Image Path Pattern**: `/sites/default/files/styles/{style_name}/public/image/{YYYY-MM}/{filename}.{ext}.webp?itok={token}`
- **Original File Pattern**: `/sites/default/files/image/{YYYY-MM}/{filename}.{ext}`
- **Image Styles**: `small_hq`, `medium_hq`, `x_large_hq`, `xx_large_hq`
- **Format**: WebP served as default (with PNG/JPG originals available)
- **Hotlinking**: **NOT BLOCKED** -- All tests returned HTTP 200 with no User-Agent, Referer, or authentication requirements

### Homepage Images

| Image | URL (Original) | Styled Dimensions | Quality | Classification |
|-------|---------------|--------------------|---------|----------------|
| Maximize Availability | `/sites/default/files/image/2025-09/Maximize_availability.png` | 496x479 | KEEP - Product Feature | PRODUCT |
| Boost Productivity | `/sites/default/files/image/2025-09/Boost_productivity_0.png` | 496x479 | KEEP - Product Feature | PRODUCT |
| Ecosystem | `/sites/default/files/image/2025-09/Ecosystem.png` | 496x479 | KEEP - Product Feature | PRODUCT |
| Hospital Staff | `/sites/default/files/image/2025-09/hospital-staff-1280x800-corners.png` | 640x400 | KEEP - Hero/Lifestyle | HERO |
| Caritas-Klinik Logo | `/sites/default/files/image/2025-09/d3d82e2fc8aa89941183f892ad862f48f557f6cd.png` | 150x51 | FLAG - Customer Logo | THUMBNAIL |
| Blue Circuit Board | `/sites/default/files/image/2025-09/angled-blue-circuitboard-1280-corners.png` | 640x360 | KEEP - Hero/Lifestyle | HERO |
| Hand Holding Icons | `/sites/default/files/image/2025-09/hand-holding-circular-icons-1280-corners.png` | 640x360 | KEEP - Hero/Lifestyle | HERO |
| Blue Shield Padlock | `/sites/default/files/image/2025-09/blue-shield-padlock-1280-corners.png` | 640x360 | KEEP - Hero/Lifestyle | HERO |

### Product Page Images

#### x250-28XTm (Stackable Switch)
| Image | URL (Original) | Dimensions | Classification |
|-------|---------------|------------|----------------|
| Product Photo | `/sites/default/files/image/2024-11/x250-28xtm-3840.png` | 3840px wide original (496x279 styled) | KEEP - Product |

#### TQ6403 GEN2 (Wireless AP)
| Image | URL (Original) | Dimensions | Classification |
|-------|---------------|------------|----------------|
| Product Photo | `/sites/default/files/image/2024-06/tq6403-gen2-3840.png` | 3840px wide original (496x279 styled) | KEEP - Product |
| AWC Video Thumb | `/sites/default/files/image/2023-02/AWC-video.jpg` | 496x279 | KEEP - Video Thumbnail |
| Oembed Thumb 1 | `/sites/default/files/oembed_thumbnails/BKeC935C6oEYTr0CMR_zt4mHEaSnLIAAzXzKlrqiMzk.jpg` | 147x83 | FLAG - Low-res thumbnail |
| Oembed Thumb 2 | `/sites/default/files/oembed_thumbnails/sCROfOy1yKc0bUNVqhR7riBv-ipgr6C7edOeKZlydPE.` | 320x180 | FLAG - Low-res thumbnail |

#### ARX200S-GTX (Security Appliance)
| Image | URL (Original) | Dimensions | Classification |
|-------|---------------|------------|----------------|
| Product Photo | `/sites/default/files/image/2025-03/arx200s-gtx-3840.png` | 3840px wide original (496x279 styled) | KEEP - Product |
| Oembed Thumb 1 | `/sites/default/files/oembed_thumbnails/hFZ7OHKO-eK9pn5uG-7Dm6FmirTyD3awWbZrCpeGjmM.jpg` | 320x180 | FLAG - Low-res thumbnail |
| Oembed Thumb 2 | `/sites/default/files/oembed_thumbnails/VcUNGbOTnfi4UZ0l1zzGbIBNTdcPZi72_x3-Vx6pfnI.jpg` | 147x83 | FLAG - Low-res thumbnail |
| Oembed Thumb 3 | `/sites/default/files/oembed_thumbnails/ZZZxEMgcdqmeLvxn_LRhOrvSSnLU7cIX6GVE3CH_Fv4.jpg` | 147x83 | FLAG - Low-res thumbnail |

### Category/Listing Images

| Image | URL (Original) | Dimensions | Classification |
|-------|---------------|------------|----------------|
| Switches 100G | `/sites/default/files/image/2023-03/switches-100g.png` | 468x152 | KEEP - Category Banner |
| Kangan Case Study | `/sites/default/files/kangan_960px.png` | 480x288 | KEEP - Case Study |
| Blue Fishnet BG | `/sites/default/files/image/2021-07/blue-fishnet-bg.jpg` | Background | KEEP - Decorative BG |
| Additional Resources BG | `/sites/default/files/image/2021-06/additional-resources-bg.jpg` | Background | KEEP - Decorative BG |

### UI/Icon Assets (SKIP for storefront)

| Asset | URL | Purpose |
|-------|-----|---------|
| Quote Builder Icon | `/themes/custom/themekit/assets/images/svg/quote-builder-solid.svg?v=1` | Cart/quote UI icon |
| ATI Loader | `/sites/default/files/svg/2022-06/ati-loader.svg` | Loading spinner animation |

### Product Image Naming Convention
All product photos follow the pattern: `{model-name}-3840.png`
- Original resolution: 3840px wide (high-res for zoom)
- Served via Drupal image styles as WebP at various breakpoints
- itok parameter is an image style security token (does not block access)

---

## 5. CDN Hotlinking Test Results

| Test | URL | Headers | HTTP Status | Size | Result |
|------|-----|---------|-------------|------|--------|
| Product PNG (with UA) | `/image/2024-11/x250-28xtm-3840.png` | User-Agent | 200 | 1,021,906 bytes | **PASS** |
| Logo SVG | `/themekit/dist/svg/logo_color.svg` | User-Agent | 200 | 4,445 bytes | **PASS** |
| Homepage WebP | `/hospital-staff-1280x800-corners.png.webp` | User-Agent | 200 | 117,182 bytes | **PASS** |
| Product PNG (no headers) | `/image/2024-11/x250-28xtm-3840.png` | None | 200 | 1,021,906 bytes | **PASS** |
| Product PNG (ext referer) | `/image/2024-11/x250-28xtm-3840.png` | Referer: amazon.com | 200 | 1,021,906 bytes | **PASS** |
| Video WebM | `/video/2025-09/cityscape.webm` | None | 200 | 855,525 bytes | **PASS** |

**Conclusion: Allied Telesis CDN has NO hotlinking protection.** All assets are freely downloadable without authentication, User-Agent, or Referer headers. Image style tokens (itok=) do not block access.

---

## 6. Video Asset Inventory

### Homepage Videos (Direct-Hosted WebM)

| Video | URL | Format | Resolution | Size | Autoplay | Loop | Context |
|-------|-----|--------|------------|------|----------|------|---------|
| **Cityscape Hero** | `https://www.alliedtelesis.com/sites/default/files/video/2025-09/cityscape.webm` | video/webm | 1280x720 | 855 KB | Yes | Yes | Hero background behind "Highly Reliable, Automated, Open Networks" |
| **Grey Background** | `https://www.alliedtelesis.com/sites/default/files/video/2025-09/grey-background.webm` | video/webm | 1920x1080 | 116 KB | Yes | Yes | Background texture for "Automated Solution" section |

### Product Page Videos (Vimeo Embeds)

Found via oembed thumbnail references in product page HTML:

| Product Page | Vimeo URL | Description |
|-------------|-----------|-------------|
| TQ6403 GEN2 (Wireless) | `https://vimeo.com/516758202` | AWC/Wireless management video |
| TQ6403 GEN2 (Wireless) | `https://vimeo.com/324894758` | Allied Telesis wireless solutions |
| ARX200S-GTX (Security) | `https://vimeo.com/721250694` | Security appliance overview |
| ARX200S-GTX (Security) | `https://vimeo.com/830053308` | ARX/security feature video |

### Social/Video Channels
- **YouTube**: https://www.youtube.com/@AlliedTelesisIntl
- **Vimeo**: https://vimeo.com/alliedtelesis

### Video Content Page
The page at `/us/en/documents/video-total-autonomous-networking` uses a static thumbnail image rather than an embedded video player. The thumbnail image:
- Hero: `/sites/default/files/styles/xx_large_hq/public/images/heroes/hero_g1_xl_1.jpg` (600x360)
- Content Thumb: `/sites/default/files/image/2023-01/total-autonomous-networking-thumb.jpg` (700x394)

Video pages appear to rely on click-to-play or external links rather than inline embeds. Uses a LiveChat widget (license 9783410).

### Video Download Status

| Video | curl Status | Downloadable |
|-------|------------|-------------|
| cityscape.webm | HTTP 200, 855,525 bytes | Yes - full download works |
| grey-background.webm | HTTP 200, 115,760 bytes | Yes - full download works |
| Vimeo embeds | N/A - hosted on Vimeo | Requires Vimeo tools to download |

---

## 7. Hero Imagery Style Description

The Allied Telesis homepage hero section features:

1. **Bold Blue Background** (`#003865`) serving as the base layer
2. **Looping WebM Video** (cityscape.webm, 1280x720) showing a nighttime city skyline with glowing network connection lines and particles overlaid -- conveying connectivity, smart cities, and digital infrastructure
3. **Left-aligned white text** in Roboto Light (300 weight) at 51px with the headline "Highly Reliable, Automated, Open Networks"
4. **Dark Red accent stripe** (`#983222`) running along the bottom/left edge of the hero creating a warm contrast against the cool blue
5. **Clean, minimal composition** -- no product shots in the hero, purely conceptual/aspirational imagery

The overall visual language is:
- **Enterprise-professional** with a cool blue-gray palette
- **Technology-forward** with network visualization, circuit board, and abstract data imagery
- **Clean and minimal** -- heavy use of whitespace, light font weights, rounded corners (0.25rem default)
- **Photography style**: Lifestyle/scenario imagery (hospital staff, building exterior) with rounded corners applied via CSS
- **Product photography**: Clean white/transparent background cutouts at very high resolution (3840px originals)

---

## 8. Design System Summary

### Framework
- **CSS Framework**: Bootstrap 5 (customized via SCSS with custom color tokens)
- **CMS**: Drupal (theme: `themekit`)
- **Image Processing**: Drupal Image Styles (small_hq, medium_hq, x_large_hq, xx_large_hq) with WebP conversion

### Key Design Tokens
```scss
// Primary brand colors
$primary: #4D738A;        // Links, primary buttons
$dark-red: #983222;       // CTA buttons, accents
$primary-red: #BE3A34;    // Secondary red accent
$bold-blue: #003865;      // Hero backgrounds
$gold: #EFBD47;           // Accent highlights

// Neutral scale
$body-color: #333333;
$body-bg: #F7F7F7;
$primary-black: #25282A;
$primary-gray: #7C878E;

// Typography
$font-family: Roboto, "Libre Franklin", "Source Sans Pro", system-ui, sans-serif;
$body-font-weight: 300;
$body-font-size: 1rem;      // 17px (root = 1.0625rem)
$body-line-height: 1.4;

// Border radius
$border-radius: 0.25rem;
$border-radius-sm: 3px;
$border-radius-lg: 0.3rem;
```

### Pantone References (from CSS variable names)
The theme CSS variable names suggest these Pantone references:
- `--bs-blue-2955`: `#003C69` (likely Pantone 2955, the corporate navy)
- `--bs-blue-5405`: `#44697D` (likely Pantone 5405, the medium blue)
- `--bs-blue-5435`: `#A6BCC6` (likely Pantone 5435, the calm blue)
- `--bs-yellow-142`: `#EFBD47` (likely Pantone 142, the gold)
- `--bs-yellow-145`: `#CA7700` (likely Pantone 145, the burnt orange)
- `--bs-green-348`: `#008542` (likely Pantone 348, the green)
- `--bs-red-484`: `#99030B` (likely Pantone 484, the dark red)
- `--bs-blue-430`: `#818A8F` (likely Pantone 430, the gray)
- `--bs-blue-550`: `#8CB8C6` (likely Pantone 550, the bright blue)
