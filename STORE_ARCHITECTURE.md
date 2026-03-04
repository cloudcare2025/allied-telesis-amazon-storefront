# Allied Telesis Amazon Brand Store — Store Architecture

## Phase 2 Output — Single Source of Truth for Phases 4, 5, 6

---

## Step 1: Category Taxonomy

1. **Switches** — Enterprise campus, stackable edge, and SMB managed Layer 3 switches (17 products)
2. **Industrial Switches** — Ruggedized fanless DIN-rail switches for factory floors and harsh environments (5 products)
3. **Wireless Access Points** — Enterprise Wi-Fi 6, 6E, and 7 access points with AWC self-optimization (7 products)
4. **Firewalls & Security** — Unified Threat Management appliances with SD-WAN and DPI (2 products)
5. **Connectivity** — Media converters and PCIe network adapters for fiber/copper bridging (9 products)

**Special Page**: Network Management — Vista Manager EX, OneConnect, AWC, StreamConnect software platforms (4 products)

**Total**: 44 products across 5 categories + 1 special page

---

## Step 1b: Category Slug Map

Written to `CATEGORY_SLUG_MAP.json` at project root. See that file for the canonical slug/filename/data-section/image-directory mappings.

---

## Step 2: Page Map

```
PAGE MANIFEST (canonical — delete all .html files not listed here):
──────────────────────────────────────────────────────────────────
 #  | Filename                  | Type     | data-section         | Description
────|───────────────────────────|──────────|──────────────────────|──────────────
 1  | index.html                | homepage | home                 | Brand landing page with hero video
 2  | switches.html             | category | switches             | Enterprise, stackable edge, and SMB switches
 3  | industrial.html           | category | industrial           | Industrial ruggedized switches
 4  | wireless.html             | category | wireless             | Wi-Fi 6/6E/7 access points
 5  | firewalls.html            | category | firewalls            | UTM firewalls and security appliances
 6  | connectivity.html         | category | connectivity         | Media converters and network adapters
 7  | network-management.html   | special  | network-management   | Software management platforms
```

**Enforcement rule for Phase 5:** Before generating HTML, run `ls *.html` and delete any file not in this manifest. After generation, run `ls *.html` again and confirm the list matches exactly 7 files.

---

## Step 3: Navigation Structure & Data-Section Map

### 3a: Navigation Tabs

```
NAV TABS:
─────────────────────────────────────────────────────────────
 Tab Label            | Target Page               | data-section         | Nav Icon
──────────────────────|───────────────────────────|──────────────────────|─────────────────────────────
 Home                 | index.html                | home                 | images/nav/icon-home.svg
 Switches             | switches.html             | switches             | images/nav/icon-switches.svg
 Industrial           | industrial.html           | industrial           | images/nav/icon-industrial.svg
 Wireless             | wireless.html             | wireless             | images/nav/icon-wireless.svg
 Firewalls            | firewalls.html            | firewalls            | images/nav/icon-firewalls.svg
 Connectivity         | connectivity.html         | connectivity         | images/nav/icon-connectivity.svg
 Network Management   | network-management.html   | network-management   | images/nav/icon-network-management.svg
```

### 3b: DATA_SECTION_MAP

```json
{
  "data_section_map": {
    "home": {
      "nav_tab": "Home",
      "html_page": "index.html",
      "page_sections": ["hero", "about-brand", "category-preview", "differentiators", "industries", "testimonials", "partners", "contact-cta"]
    },
    "switches": {
      "nav_tab": "Switches",
      "html_page": "switches.html",
      "page_sections": ["hero", "product-grid-campus", "product-grid-edge", "product-grid-smb", "features", "specs-comparison"]
    },
    "industrial": {
      "nav_tab": "Industrial",
      "html_page": "industrial.html",
      "page_sections": ["hero", "product-grid", "features", "use-cases"]
    },
    "wireless": {
      "nav_tab": "Wireless",
      "html_page": "wireless.html",
      "page_sections": ["hero", "product-grid", "features", "video-section"]
    },
    "firewalls": {
      "nav_tab": "Firewalls",
      "html_page": "firewalls.html",
      "page_sections": ["hero", "product-grid", "features", "specs-comparison", "video-section"]
    },
    "connectivity": {
      "nav_tab": "Connectivity",
      "html_page": "connectivity.html",
      "page_sections": ["hero", "product-grid-converters", "product-grid-adapters", "features"]
    },
    "network-management": {
      "nav_tab": "Network Management",
      "html_page": "network-management.html",
      "page_sections": ["hero", "product-grid", "features", "integration"]
    }
  }
}
```

---

## Step 4: Homepage Blueprint

```
HOMEPAGE BLUEPRINT (index.html):
═══════════════════════════════

Section 1: Hero Banner (Video Background)
  - Container: <section class="hero-section" data-section="home">
  - Background: <video> element using hero-video-web.webm (autoplay, muted, loop)
  - Poster fallback: images/hero/hero-poster.svg (1500x400 branded illustration)
  - Overlay: Semi-transparent gradient in brand secondary color (#003865)
  - Headline: "Allied Telesis — Network Smarter."
  - Subhead: "Enterprise-grade switches, wireless, and security trusted by organizations in 90+ countries. Engineered in Japan since 1987."
  - CTA button: "Explore Solutions" → scrolls to category-preview section
  - CSS classes: .hero-section, .hero__bg-video, .hero__content, .hero__headline, .hero__sub, .hero__cta

Section 2: About Brand
  - Container: <section class="about-brand" id="about-brand">
  - Layout: Two-column (text left 60%, image right 40%)
  - Image: images/branding/about-brand.svg (800x600 — network topology illustration)
  - Headline: "Trusted Network Infrastructure Since 1987"
  - Content paragraph 1: "At the heart of Allied Telesis lies a simple yet powerful belief: technology should elevate performance, empower people, and create lasting value. From our headquarters in Tokyo and San Jose, we serve organizations across education, healthcare, government, and manufacturing."
  - Content paragraph 2: "With nearly 1,900 employees worldwide, Allied Telesis delivers enterprise-grade networking at a fraction of the cost of Tier 1 competitors — backed by autonomous management, self-defending security, and non-stop resilience."
  - CSS classes: .about-brand, .about-brand__content, .about-brand__image

Section 3: Category Preview Grid
  - Container: <section class="category-preview" id="category-preview">
  - Layout: 3-column responsive grid (2-col on tablet, 1-col on mobile)
  - Headline: "Explore Our Product Portfolio"
  - Cards (5 category cards + 1 software card):
    1. Switches — images/nav/icon-switches.svg — "Enterprise campus, stackable edge, and SMB switches with up to 100G uplinks" → switches.html
    2. Industrial — images/nav/icon-industrial.svg — "Ruggedized DIN-rail switches for factory floors, IIoT, and harsh environments" → industrial.html
    3. Wireless — images/nav/icon-wireless.svg — "Wi-Fi 6, 6E, and 7 access points with AI-powered wireless optimization" → wireless.html
    4. Firewalls — images/nav/icon-firewalls.svg — "UTM security with SD-WAN, deep packet inspection, and 10G throughput" → firewalls.html
    5. Connectivity — images/nav/icon-connectivity.svg — "Media converters and 25G PCIe network adapters for seamless bridging" → connectivity.html
    6. Network Management — images/nav/icon-network-management.svg — "Cloud and on-premise platforms for unified network visibility and control" → network-management.html
  - CSS classes: .category-preview, .category-preview__grid, .category-card, .category-card__icon, .category-card__title, .category-card__desc

Section 4: Key Differentiators
  - Container: <section class="differentiators" id="differentiators">
  - Layout: 4-column icon grid (2-col on mobile)
  - Headline: "Why Allied Telesis"
  - Cards:
    1. Icon: images/branding/icon-reliability.svg — "Non-Stop Networks" — "Redundant hardware, VCStack resilience, and EPSRing with 50ms failover keep your network running 24/7."
    2. Icon: images/branding/icon-automation.svg — "Autonomous Management" — "AMF Plus zero-touch provisioning, AWC AI-driven Wi-Fi optimization, and Vista Manager single-pane-of-glass control."
    3. Icon: images/branding/icon-security.svg — "Self-Defending Security" — "AMF-Sec automatically quarantines threats without endpoint agents. Multiple InfoSec and Fortress Cyber Security Awards."
    4. Icon: images/branding/icon-performance.svg — "Lower Total Cost" — "Enterprise-grade networking at a fraction of Tier 1 pricing. License fees are a fraction of hardware cost."
  - CSS classes: .differentiators, .differentiators__grid, .diff-card, .diff-card__icon, .diff-card__title, .diff-card__desc

Section 5: Industries Served
  - Container: <section class="industries" id="industries">
  - Layout: Horizontal scrolling card row (5 cards)
  - Headline: "Trusted Across Industries"
  - Cards:
    1. images/industries/education.svg — "Education" — "Next-level performance for classrooms and mobile users with secure infrastructure."
    2. images/industries/healthcare.svg — "Healthcare" — "Reliable networks for diagnostic imaging, patient data, and 15+ devices per room."
    3. images/industries/government.svg — "Government" — "NDAA Section 889 and TAA compliant networking for federal, state, and local agencies."
    4. images/industries/manufacturing.svg — "Manufacturing" — "Industrial-grade IIoT networking with PTP, CIP/IO, and extended lifecycle support."
    5. images/industries/transportation.svg — "Transportation" — "Fast, efficient, and safe transit network infrastructure."
  - CSS classes: .industries, .industries__scroll, .industry-card, .industry-card__image, .industry-card__title, .industry-card__desc

Section 6: Customer Testimonials
  - Container: <section class="testimonials" id="testimonials">
  - Layout: Carousel/slider (3 visible, auto-rotate)
  - Headline: "What Our Customers Say"
  - Testimonials:
    1. Quote mark: images/branding/quote-mark.svg
       Quote: "With Allied Telesis, the license fee is a fraction of the hardware cost. We were able to save a substantial amount of money by going with them."
       — Sean Stinner, Network Engineer, Service Spring Corporation
    2. Quote: "Allied Telesis hardware is better than everyone else's and meets my needs better than everybody else."
       — Chris Hanshaw, Technology Director, Nicholas County Schools
    3. Quote: "The total cost of ownership for our network is so much lower than that of a legacy network architecture."
       — Chris Hanshaw, Technology Director, Nicholas County Schools
    4. Quote: "Allied Telesis has empowered us to build the best and most reliable network for our University."
       — Mr Pradeep, Campus Network Facility, University of Hyderabad
    5. Quote: "Unlike other manufacturers, Allied Telesis provides a real partnership, with competent and dedicated support from A to Z."
       — Michael Brase, Managing Director, TELBA GmbH
  - CSS classes: .testimonials, .testimonials__carousel, .testimonial-card, .testimonial-card__quote, .testimonial-card__author

Section 7: Technology Partners
  - Container: <section class="partners" id="partners">
  - Layout: Centered logo row with 3 partner logos
  - Headline: "Technology Partners"
  - Logos:
    1. images/branding/partner-sinclair.svg — "Sinclair Digital" (AGILE-CORE architecture)
    2. images/branding/partner-hanwha.svg — "Hanwha Vision" (video surveillance integration)
    3. images/branding/partner-milestone.svg — "Milestone Systems" (VMS integration)
  - CSS classes: .partners, .partners__grid, .partner-logo

Section 8: Contact CTA
  - Container: <section class="contact-cta" id="contact-cta">
  - Layout: Full-width banner with centered text
  - Background: Brand secondary color (#003865)
  - Headline: "Ready to Network Smarter?"
  - Subhead: "Contact an Allied Telesis authorized reseller to find the right solution for your organization."
  - CTA button: "Find a Reseller" (links to alliedtelesis.com partner locator)
  - CSS classes: .contact-cta, .contact-cta__content, .contact-cta__headline, .contact-cta__btn

Section 9: Footer
  - Container: <footer class="amazon-footer">
  - DO NOT use any class other than "amazon-footer"
  - Logo: images/branding/brand-logo-white.svg
  - Links: About Us, Contact, Privacy Policy, Terms of Service
  - Copyright: "© 2026 Allied Telesis, Inc. All rights reserved."
  - Tagline: "Network smarter."
```

---

## Step 5: Category Page Blueprints

### CATEGORY PAGE: Switches (switches.html)

```
SWITCHES PAGE BLUEPRINT:
═══════════════════════

Section 1: Hero
  - Container: <section class="hero-section" data-section="switches">
  - Background: images/hero/switches-hero.svg (1500x300 — switch stack illustration on bold blue)
  - Headline: "Enterprise Switches"
  - Subhead: "From 100G backbone aggregation to multi-gigabit edge access — Layer 3 managed switches with VCStack resilience, AMF Plus automation, and up to 1.92 Tbps switching fabric."
  - CSS classes: .hero-section, .hero__content, .hero__headline, .hero__sub

Section 2: Product Grid — Enterprise Campus (13 products)
  - Container: <section class="product-section" id="product-grid-campus">
  - Sub-headline: "Enterprise Campus"
  - Layout: 3-column responsive grid (2-col tablet, 1-col mobile)
  - Products:
     1. x950-28XSQ — images/products/switches/x950-28xsq.png
        "24-port 10G SFP+ | 4x 100G QSFP28 | 1.92 Tbps"
     2. x950-28XTQm — images/products/switches/x950-28xtqm.png
        "24-port 10G copper | 4x 100G QSFP28 | 1.92 Tbps"
     3. x950-52XSQ — images/products/switches/x950-52xsq.png
        "48-port 10G SFP+ | 4x 100G QSFP28 | 1.92 Tbps"
     4. x950-52XTQm — images/products/switches/x950-52xtqm.png
        "48-port 10G copper | 4x 100G QSFP28 | 1.92 Tbps"
     5. x560-28YSQ — images/products/switches/x560-28ysq.png
        "24-port 25G SFP28 | 4x 100G QSFP28 | 2.0 Tbps"
     6. x540L-28XTm — images/products/switches/x540l-28xtm.png
        "24-port multi-gigabit | 4x 10G SFP+ | 560 Gbps"
     7. x540L-28XS — images/products/switches/x540l-28xs.png
        "28-port 10G SFP+ | 560 Gbps | all-fiber"
     8. x250-28XTm — images/products/switches/x250-28xtm.png
        "24-port multi-gigabit | 4x 10G SFP+ | 560 Gbps"
     9. x250-28XS — images/products/switches/x250-28xs.png
        "28-port 10G SFP+ | 560 Gbps | stackable edge"
    10. x250-18XTm — images/products/switches/x250-18xtm.png
        "16-port multi-gigabit | 2x 10G SFP+ | 360 Gbps"
    11. x250-18XS — images/products/switches/x250-18xs.png
        "18-port 10G SFP+ | 360 Gbps | compact"
    12. SBx908 GEN3 — images/products/switches/sbx908-gen3.png
        "8-bay modular chassis | 3RU | hot-swap PSU"
    13. x240-26GHXM — images/products/switches/x240-26ghxm.png
        "24-port multi-gigabit | 90W PoE++ | 280 Gbps"
  - CSS classes: .product-section, .product-section__title, .product-grid, .product-card, .product-card__image, .product-card__name, .product-card__specs

Section 3: Product Grid — Stackable Edge (2 products)
  - Container: <section class="product-section" id="product-grid-edge">
  - Sub-headline: "Stackable Edge"
  - Products:
    14. SE540L-28XTm — images/products/switches/se540l-28xtm.png
        "24-port multi-gigabit | 4x 10G SFP+ | 560 Gbps"
    15. SE250-28XTm — images/products/switches/se250-28xtm.png
        "24-port multi-gigabit | 4x 10G SFP+ | stackable"

Section 4: Product Grid — SMB (2 products)
  - Container: <section class="product-section" id="product-grid-smb">
  - Sub-headline: "Small Business"
  - Products:
    16. GS950/28 V2 — images/products/switches/gs950-28-v2.png
        "24-port Gigabit | 4x SFP | fanless | WebSmart"
    17. GS950/28PS V2 — images/products/switches/gs950-28ps-v2.png
        "24-port Gigabit PoE+ | 185W | 4x SFP | WebSmart"

Section 5: Key Features
  - Container: <section class="features-section" id="features">
  - Layout: 3-column icon grid
  - Cards:
    1. "VCStack Resilience" — "Virtual chassis stacking creates a unified, fault-tolerant switching fabric across up to 8 units."
    2. "AMF Plus Automation" — "Zero-touch provisioning, automated backup and recovery, and seamless firmware management."
    3. "MACSec & FIPS 140-2" — "Hardware-level encryption on every link. FIPS 140-2 certified for government compliance."

Section 6: Specs Comparison Table
  - Container: <section class="specs-section" id="specs-comparison">
  - Layout: Responsive table
  - Columns: Model | Ports | Switching Fabric | Throughput | Uplinks | Key Feature
  - Include top 6 models for quick comparison

Section 7: Footer
  - <footer class="amazon-footer">
```

### CATEGORY PAGE: Industrial Switches (industrial.html)

```
INDUSTRIAL SWITCHES PAGE BLUEPRINT:
═══════════════════════════════════

Section 1: Hero
  - Container: <section class="hero-section" data-section="industrial">
  - Background: images/hero/industrial-hero.svg (1500x300 — factory floor with DIN-rail switch)
  - Headline: "Industrial Networking"
  - Subhead: "Ruggedized, fanless switches built for factory floors, outdoor environments, and critical infrastructure. DIN-rail mount, IP30-rated, industrial temperature range."

Section 2: Product Grid (5 products)
  - Container: <section class="product-section" id="product-grid">
  - Layout: 3-column responsive grid
  - Products:
    1. IE360-12GHX — images/products/industrial/ie360-12ghx.png
       "8-port GbE PoE++ (90W) | 2x SFP | 2x 10G SFP+ | 360W PoE budget"
    2. IE360-12GTX — images/products/industrial/ie360-12gtx.png
       "8-port GbE | 2x SFP | 2x 10G SFP+ | MACsec | fanless"
    3. IE560-12GSX — images/products/industrial/ie560-12gsx.png
       "8x SFP + 4x 10G SFP+ | all-fiber industrial"
    4. iGS950/10PS — images/products/industrial/igs950-10ps.png
       "8-port GbE PoE+ | 2x SFP | 130W budget | fanless"
    5. iGS950/28PS — images/products/industrial/igs950-28ps.png
       "24-port GbE PoE+ | 4x combo | 370W budget"

Section 3: Key Features
  - Container: <section class="features-section" id="features">
  - Cards:
    1. "Fanless IP30 Design" — "Convection-cooled enclosures with IP30 protection and -40°C to +75°C operation range."
    2. "DIN-Rail & Wall Mount" — "Flexible mounting for industrial cabinets, factory walls, and outdoor enclosures."
    3. "PoE++ (90W per port)" — "Power cameras, sensors, and edge devices directly over Ethernet with up to 360W total budget."

Section 4: Use Cases
  - Container: <section class="use-cases" id="use-cases">
  - Layout: 3-column card grid
  - Cards: Manufacturing & IIoT, Transportation, Energy & Utilities

Section 5: Footer
  - <footer class="amazon-footer">
```

### CATEGORY PAGE: Wireless Access Points (wireless.html)

```
WIRELESS PAGE BLUEPRINT:
════════════════════════

Section 1: Hero
  - Container: <section class="hero-section" data-section="wireless">
  - Background: images/hero/wireless-hero.svg (1500x300 — wireless wave illustration)
  - Headline: "Wireless Access Points"
  - Subhead: "Wi-Fi 7, 6E, and 6 access points with Autonomous Wave Control for AI-driven RF optimization, hybrid single/multi-channel architecture, and up to 19 Gbps capacity."

Section 2: Product Grid (7 products)
  - Container: <section class="product-section" id="product-grid">
  - Layout: 3-column responsive grid
  - Products:
    1. TQ7613-R — images/products/wireless/tq7613-r.png
       "Wi-Fi 7 | 4x4 tri-radio | 19 Gbps | dual 10G uplinks"
    2. TQ6403 GEN2 — images/products/wireless/tq6403-gen2.png
       "Wi-Fi 6 | tri-radio 2x2 | 2.4 Gbps | hybrid mode"
    3. TQm6403 GEN2 — images/products/wireless/tqm6403-gen2.png
       "Wi-Fi 6 | tri-radio 2x2 | 2.4 Gbps | wall/ceiling mount"
    4. TQ3403 — images/products/wireless/tq3403.png
       "Wi-Fi 6E | tri-radio | 2.4 Gbps | 6GHz band"
    5. TQ7403-R — images/products/wireless/tq7403-r.png
       "Wi-Fi 6E | AP + VPN router | SD-WAN | AlliedWare Plus"
    6. TQ6702e GEN2-R — images/products/wireless/tq6702e-gen2-r.png
       "Wi-Fi 6 | 8x8 MIMO | 4.8 Gbps | outdoor-rated"
    7. TQ3403-R — images/products/wireless/tq3403-r.png
       "Wi-Fi 6E | tri-radio | 2.4 Gbps | built-in routing"

Section 3: Key Features
  - Container: <section class="features-section" id="features">
  - Cards:
    1. "Autonomous Wave Control" — "AI-powered RF optimization that automatically tunes channel, power, and coverage for best performance."
    2. "Hybrid Wi-Fi (World First)" — "Simultaneous Channel Blanket single-channel and traditional multi-channel architecture for seamless roaming."
    3. "AlliedWare Plus OS" — "Enterprise operating system with DPI, Passpoint, OpenRoaming, and centralized management."

Section 4: Video Section
  - Container: <section class="video-section" id="video-section">
  - Layout: Featured video + thumbnail grid
  - Featured: Vimeo embed — https://player.vimeo.com/video/516758202 — "AWC Wireless Solutions"
  - Thumbnail: Vimeo embed — https://player.vimeo.com/video/324894758 — "Wireless Solutions Overview"

Section 5: Footer
  - <footer class="amazon-footer">
```

### CATEGORY PAGE: Firewalls & Security (firewalls.html)

```
FIREWALLS PAGE BLUEPRINT:
═════════════════════════

Section 1: Hero
  - Container: <section class="hero-section" data-section="firewalls">
  - Background: images/hero/firewalls-hero.svg (1500x300 — shield/lock security illustration)
  - Headline: "Firewalls & Security"
  - Subhead: "Unified Threat Management with 10G performance, integrated SD-WAN, deep packet inspection, and advanced threat protection. Built on AlliedWare Plus for autonomous security."

Section 2: Product Grid (2 products)
  - Container: <section class="product-section" id="product-grid">
  - Layout: 2-column centered grid
  - Products:
    1. ARX200S-GTX — images/products/firewalls/arx200s-gtx.png
       "10G WAN | 5.5 Gbps firewall | 2.5 Gbps VPN | 600K sessions"
    2. ARX200S-GT — images/products/firewalls/arx200s-gt.png
       "1G WAN | branch office UTM | SD-WAN | cloud-first"

Section 3: Key Features
  - Container: <section class="features-section" id="features">
  - Cards:
    1. "Unified Threat Management" — "Application control, web filtering, antivirus, IPS, and advanced threat protection in one appliance."
    2. "Integrated SD-WAN" — "Secure inter-branch connectivity with intelligent path selection and application-aware routing."
    3. "AMF-Sec Self-Defending" — "Automatically quarantines suspect devices without endpoint agents. Winner of Fortress Cyber Security Award."

Section 4: Specs Comparison Table
  - Container: <section class="specs-section" id="specs-comparison">
  - Columns: Model | WAN | Firewall Throughput | VPN Throughput | Sessions | UTM Throughput
  - Rows: ARX200S-GTX, ARX200S-GT

Section 5: Video Section
  - Container: <section class="video-section" id="video-section">
  - Featured: Vimeo embed — https://player.vimeo.com/video/721250694 — "Security Overview"
  - Thumbnail: Vimeo embed — https://player.vimeo.com/video/830053308 — "ARX Security Feature"

Section 6: Footer
  - <footer class="amazon-footer">
```

### CATEGORY PAGE: Connectivity (connectivity.html)

```
CONNECTIVITY PAGE BLUEPRINT:
════════════════════════════

Section 1: Hero
  - Container: <section class="hero-section" data-section="connectivity">
  - Background: images/hero/connectivity-hero.svg (1500x300 — fiber/copper bridge illustration)
  - Headline: "Connectivity Solutions"
  - Subhead: "Media converters for copper-to-fiber bridging and high-speed PCIe network adapters from 100Mbps to 25Gbps. Bridge any network gap."

Section 2: Product Grid — Media Converters (3 products)
  - Container: <section class="product-section" id="product-grid-converters">
  - Sub-headline: "Media Converters"
  - Layout: 3-column responsive grid
  - Products:
    1. MMC2000I/SP — images/products/connectivity/mmc2000i-sp.png
       "10/100/1000T to SFP | industrial temp | mini form factor"
    2. PC2000T2/SP — images/products/connectivity/pc2000t2-sp.png
       "Dual-port | 2x RJ45 + 2x SFP | DIN rail mount"
    3. MMC6000 Series — images/products/connectivity/mmc6000.png
       "VDSL2 distance extender | existing copper reuse"

Section 3: Product Grid — Network Adapters (6 products)
  - Container: <section class="product-section" id="product-grid-adapters">
  - Sub-headline: "Network Adapters"
  - Layout: 3-column responsive grid
  - Products:
    4. ANC25SP — images/products/connectivity/anc25sp.png
       "25 Gbps single-port | PCIe x8 | server NIC"
    5. ANC25SP/2 — images/products/connectivity/anc25sp-2.png
       "25 Gbps dual-port | PCIe x8 | high availability"
    6. AT-2911Ta/2 — images/products/connectivity/at-2911ta-2.png
       "Dual GbE copper | PCIe | desktop NIC"
    7. AT-2911SFPa/2 — images/products/connectivity/at-2911sfpa-2.png
       "Dual SFP 1G | PCIe | fiber NIC"
    8. AT-2911SXa/LC — images/products/connectivity/at-2911sxa-lc.png
       "1000BASE-SX/LC | PCIe | multimode fiber"
    9. AT-2711FXa/SC — images/products/connectivity/at-2711fxa-sc.png
       "100FX/SC | PCIe | Fast Ethernet fiber"

Section 4: Key Features
  - Container: <section class="features-section" id="features">
  - Cards:
    1. "Plug and Play" — "Auto-negotiation, MDI/MDI-X, and hot-swappable SFP modules for zero-configuration deployment."
    2. "Industrial-Grade" — "Extended temperature ranges, DIN-rail mounting, and ruggedized enclosures for demanding environments."
    3. "25G Server Performance" — "PCIe x8 NICs with hardware acceleration for high-throughput data center and virtualization workloads."

Section 5: Footer
  - <footer class="amazon-footer">
```

---

## Step 6: Special Page Blueprints

### SPECIAL PAGE: Network Management (network-management.html)

```
NETWORK MANAGEMENT PAGE BLUEPRINT:
═══════════════════════════════════

Section 1: Hero
  - Container: <section class="hero-section" data-section="network-management">
  - Background: images/hero/network-management-hero.svg (1500x300 — dashboard/cloud illustration)
  - Headline: "Network Management"
  - Subhead: "Unified visibility and control across your entire Allied Telesis infrastructure — from a single pane of glass or the cloud. Automate provisioning, optimize wireless, and monitor in real time."

Section 2: Product Grid (4 software products)
  - Container: <section class="product-section" id="product-grid">
  - Layout: 2-column centered grid
  - Products:
    1. Vista Manager EX — images/products/software/vista-manager.png
       "Unified LAN/SD-WAN/wireless management | floor plans | heat maps | DPI"
    2. OneConnect — images/products/software/oneconnect.png
       "Cloud SaaS | multi-site monitoring | zero-touch provisioning"
    3. AWC — images/products/software/awc.png
       "AI-powered wireless controller | auto RF optimization | seamless roaming"
    4. StreamConnect — images/products/software/streamconnect.png
       "VMS integration | surveillance network visibility | Milestone XProtect"

Section 3: Key Features
  - Container: <section class="features-section" id="features">
  - Cards:
    1. "Single Pane of Glass" — "Vista Manager EX provides unified management across LAN, SD-WAN, and wireless from one dashboard."
    2. "Cloud-First Management" — "OneConnect delivers SaaS-based monitoring and control from anywhere via browser — no on-premise server required."
    3. "AI Wireless Optimization" — "AWC continuously self-tunes channel, power, and coverage using machine learning for optimal RF performance."

Section 4: Integration Ecosystem
  - Container: <section class="integration-section" id="integration">
  - Layout: Text block with partner logos
  - Headline: "Integrates With Your Existing Stack"
  - Content: "Allied Telesis management platforms support SNMP monitoring for third-party devices, REST APIs for automation, and direct integration with Milestone XProtect for video surveillance."
  - Partner logos: images/branding/partner-milestone.svg, images/branding/partner-hanwha.svg

Section 5: Footer
  - <footer class="amazon-footer">
```

---

## Step 7: Image Requirements Matrix

```
IMAGE REQUIREMENTS MATRIX
═════════════════════════

HERO IMAGES (images/hero/):
  images/hero/hero-poster.svg               — Homepage hero poster/fallback (1500x400)
  images/hero/switches-hero.svg             — Switches page hero (1500x300)
  images/hero/industrial-hero.svg           — Industrial page hero (1500x300)
  images/hero/wireless-hero.svg             — Wireless page hero (1500x300)
  images/hero/firewalls-hero.svg            — Firewalls page hero (1500x300)
  images/hero/connectivity-hero.svg         — Connectivity page hero (1500x300)
  images/hero/network-management-hero.svg   — Network Management page hero (1500x300)
  Subtotal: 7

NAV ICONS (images/nav/):
  images/nav/icon-home.svg                  — Home tab icon (64x64)
  images/nav/icon-switches.svg              — Switches tab icon (64x64)
  images/nav/icon-industrial.svg            — Industrial tab icon (64x64)
  images/nav/icon-wireless.svg              — Wireless tab icon (64x64)
  images/nav/icon-firewalls.svg             — Firewalls tab icon (64x64)
  images/nav/icon-connectivity.svg          — Connectivity tab icon (64x64)
  images/nav/icon-network-management.svg    — Network Management tab icon (64x64)
  Subtotal: 7

BRANDING (images/branding/):
  images/branding/brand-logo.svg            — Header logo color (200x60)
  images/branding/brand-logo-white.svg      — Footer logo white (200x60)
  images/branding/about-brand.svg           — About section illustration (800x600)
  images/branding/icon-reliability.svg      — Differentiator icon (80x80)
  images/branding/icon-performance.svg      — Differentiator icon (80x80)
  images/branding/icon-security.svg         — Differentiator icon (80x80)
  images/branding/icon-automation.svg       — Differentiator icon (80x80)
  images/branding/quote-mark.svg            — Testimonial quotation mark (40x40)
  images/branding/partner-sinclair.svg      — Sinclair Digital logo (200x80)
  images/branding/partner-hanwha.svg        — Hanwha Vision logo (200x80)
  images/branding/partner-milestone.svg     — Milestone Systems logo (200x80)
  images/branding/og-image.jpg              — Open Graph share image (1200x630)
  Subtotal: 12

PRODUCT IMAGES — SWITCHES (images/products/switches/):
  images/products/switches/x950-28xsq.png       — x950-28XSQ product shot
  images/products/switches/x950-28xtqm.png      — x950-28XTQm product shot
  images/products/switches/x950-52xsq.png       — x950-52XSQ product shot
  images/products/switches/x950-52xtqm.png      — x950-52XTQm product shot
  images/products/switches/x560-28ysq.png       — x560-28YSQ product shot
  images/products/switches/x540l-28xtm.png      — x540L-28XTm product shot
  images/products/switches/x540l-28xs.png       — x540L-28XS product shot
  images/products/switches/x250-28xtm.png       — x250-28XTm product shot
  images/products/switches/x250-28xs.png        — x250-28XS product shot
  images/products/switches/x250-18xtm.png       — x250-18XTm product shot
  images/products/switches/x250-18xs.png        — x250-18XS product shot
  images/products/switches/sbx908-gen3.png      — SBx908 GEN3 product shot
  images/products/switches/x240-26ghxm.png      — x240-26GHXM product shot
  images/products/switches/se540l-28xtm.png     — SE540L-28XTm product shot
  images/products/switches/se250-28xtm.png      — SE250-28XTm product shot
  images/products/switches/gs950-28-v2.png      — GS950/28 V2 product shot
  images/products/switches/gs950-28ps-v2.png    — GS950/28PS V2 product shot
  Subtotal: 17

PRODUCT IMAGES — INDUSTRIAL (images/products/industrial/):
  images/products/industrial/ie360-12ghx.png    — IE360-12GHX product shot
  images/products/industrial/ie360-12gtx.png    — IE360-12GTX product shot
  images/products/industrial/ie560-12gsx.png    — IE560-12GSX product shot
  images/products/industrial/igs950-10ps.png    — iGS950/10PS product shot
  images/products/industrial/igs950-28ps.png    — iGS950/28PS product shot
  Subtotal: 5

PRODUCT IMAGES — WIRELESS (images/products/wireless/):
  images/products/wireless/tq7613-r.png         — TQ7613-R product shot
  images/products/wireless/tq6403-gen2.png      — TQ6403 GEN2 product shot
  images/products/wireless/tqm6403-gen2.png     — TQm6403 GEN2 product shot
  images/products/wireless/tq3403.png           — TQ3403 product shot
  images/products/wireless/tq7403-r.png         — TQ7403-R product shot
  images/products/wireless/tq6702e-gen2-r.png   — TQ6702e GEN2-R product shot
  images/products/wireless/tq3403-r.png         — TQ3403-R product shot
  Subtotal: 7

PRODUCT IMAGES — FIREWALLS (images/products/firewalls/):
  images/products/firewalls/arx200s-gtx.png     — ARX200S-GTX product shot
  images/products/firewalls/arx200s-gt.png      — ARX200S-GT product shot
  Subtotal: 2

PRODUCT IMAGES — CONNECTIVITY (images/products/connectivity/):
  images/products/connectivity/mmc2000i-sp.png    — MMC2000I/SP product shot
  images/products/connectivity/pc2000t2-sp.png    — PC2000T2/SP product shot
  images/products/connectivity/mmc6000.png        — MMC6000 Series product shot
  images/products/connectivity/anc25sp.png        — ANC25SP product shot
  images/products/connectivity/anc25sp-2.png      — ANC25SP/2 product shot
  images/products/connectivity/at-2911ta-2.png    — AT-2911Ta/2 product shot
  images/products/connectivity/at-2911sfpa-2.png  — AT-2911SFPa/2 product shot
  images/products/connectivity/at-2911sxa-lc.png  — AT-2911SXa/LC product shot
  images/products/connectivity/at-2711fxa-sc.png  — AT-2711FXa/SC product shot
  Subtotal: 9

PRODUCT IMAGES — SOFTWARE (images/products/software/):
  images/products/software/vista-manager.png    — Vista Manager EX dashboard screenshot
  images/products/software/oneconnect.png       — OneConnect cloud dashboard screenshot
  images/products/software/awc.png              — AWC wireless controller screenshot
  images/products/software/streamconnect.png    — StreamConnect VMS integration screenshot
  Subtotal: 4

INDUSTRY IMAGES (images/industries/):
  images/industries/education.svg               — Education vertical illustration
  images/industries/healthcare.svg              — Healthcare vertical illustration
  images/industries/government.svg              — Government vertical illustration
  images/industries/manufacturing.svg           — Manufacturing vertical illustration
  images/industries/transportation.svg          — Transportation vertical illustration
  Subtotal: 5

VIDEO ASSETS (project root — NOT in images/):
  hero-video-web.webm       — Homepage hero background (cityscape, autoplay, muted, loop, 855KB)
  grey-background.webm      — Automation section background (116KB)

  VIDEO EMBEDS (no download — use iframe in Phase 5):
  https://player.vimeo.com/video/516758202      — AWC Wireless Solutions (wireless.html)
  https://player.vimeo.com/video/324894758      — Wireless Solutions Overview (wireless.html)
  https://player.vimeo.com/video/721250694      — Security Overview (firewalls.html)
  https://player.vimeo.com/video/830053308      — ARX Security Feature (firewalls.html)

TOTAL: 75 images + 2 video files + 4 video embeds
```

---

## Phase 2 Summary Checklist

- [x] `CATEGORY_SLUG_MAP.json` exists at project root with all 5 categories and 2 special pages
- [x] `IMAGE_PATH_CONTRACT.json` exists at project root with every image in the store (75 entries)
- [x] Every HTML filename in the page manifest is lowercase and ends in `.html`
- [x] Every image path starts with `images/` (no leading slash, no bare relative paths)
- [x] Every image filename is lowercase
- [x] Every `data-section` value in the nav tabs matches a page in the slug map
- [x] Every page blueprint specifies `<footer class="amazon-footer">` as the footer element
- [x] The page manifest includes a deletion instruction for non-listed `.html` files
- [x] No two categories share a slug, data-section, image directory, or HTML filename
- [x] The DATA_SECTION_MAP accounts for every page and every nav tab with no orphans
- [x] Product image filenames are derived from model numbers (lowercased, special chars → hyphens)
- [x] Total image count in the matrix (75) matches total entries in IMAGE_PATH_CONTRACT.json
- [x] BRAND_INTELLIGENCE.md has video assets, and IMAGE_PATH_CONTRACT.json has videos section with paths for direct .webm files and embed URLs for Vimeo videos
