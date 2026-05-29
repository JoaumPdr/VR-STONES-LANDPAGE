---
name: Cyber-Stone Architectural
colors:
  surface: '#131313'
  surface-dim: '#131313'
  surface-bright: '#3a3939'
  surface-container-lowest: '#0e0e0e'
  surface-container-low: '#1c1b1b'
  surface-container: '#201f1f'
  surface-container-high: '#2a2a2a'
  surface-container-highest: '#353534'
  on-surface: '#e5e2e1'
  on-surface-variant: '#b9ccb2'
  inverse-surface: '#e5e2e1'
  inverse-on-surface: '#313030'
  outline: '#84967e'
  outline-variant: '#3b4b37'
  surface-tint: '#00e639'
  primary: '#ebffe2'
  on-primary: '#003907'
  primary-container: '#00ff41'
  on-primary-container: '#007117'
  inverse-primary: '#006e16'
  secondary: '#3fea50'
  on-secondary: '#003908'
  secondary-container: '#02cc35'
  on-secondary-container: '#004f0e'
  tertiary: '#fbf8f8'
  on-tertiary: '#303030'
  tertiary-container: '#dedcdb'
  on-tertiary-container: '#616060'
  error: '#ffb4ab'
  on-error: '#690005'
  error-container: '#93000a'
  on-error-container: '#ffdad6'
  primary-fixed: '#72ff70'
  primary-fixed-dim: '#00e639'
  on-primary-fixed: '#002203'
  on-primary-fixed-variant: '#00530e'
  secondary-fixed: '#72ff72'
  secondary-fixed-dim: '#37e44b'
  on-secondary-fixed: '#002203'
  on-secondary-fixed-variant: '#00530f'
  tertiary-fixed: '#e4e2e1'
  tertiary-fixed-dim: '#c8c6c5'
  on-tertiary-fixed: '#1b1c1c'
  on-tertiary-fixed-variant: '#474746'
  background: '#131313'
  on-background: '#e5e2e1'
  surface-variant: '#353534'
typography:
  headline-xl:
    fontFamily: Space Grotesk
    fontSize: 64px
    fontWeight: '700'
    lineHeight: '1.1'
    letterSpacing: -0.02em
  headline-lg:
    fontFamily: Space Grotesk
    fontSize: 48px
    fontWeight: '700'
    lineHeight: '1.2'
    letterSpacing: -0.01em
  headline-md:
    fontFamily: Space Grotesk
    fontSize: 32px
    fontWeight: '600'
    lineHeight: '1.3'
  headline-sm:
    fontFamily: Space Grotesk
    fontSize: 24px
    fontWeight: '600'
    lineHeight: '1.4'
  body-lg:
    fontFamily: Outfit
    fontSize: 18px
    fontWeight: '400'
    lineHeight: '1.6'
  body-md:
    fontFamily: Outfit
    fontSize: 16px
    fontWeight: '400'
    lineHeight: '1.6'
  label-md:
    fontFamily: Space Grotesk
    fontSize: 14px
    fontWeight: '500'
    lineHeight: '1.0'
    letterSpacing: 0.1em
  headline-xl-mobile:
    fontFamily: Space Grotesk
    fontSize: 40px
    fontWeight: '700'
    lineHeight: '1.1'
  headline-lg-mobile:
    fontFamily: Space Grotesk
    fontSize: 32px
    fontWeight: '700'
    lineHeight: '1.2'
rounded:
  sm: 0.5rem
  DEFAULT: 1rem
  md: 1.5rem
  lg: 2rem
  xl: 3rem
  full: 9999px
spacing:
  unit: 8px
  container-max: 1440px
  gutter: 24px
  margin-mobile: 20px
  margin-desktop: 80px
  section-gap: 120px
---

## Brand & Style
The design system embodies a "High-Tech Craftsmanship" aesthetic, blending the raw, enduring nature of stonework and carpentry with a futuristic, digital-first precision. It targets a premium clientele looking for bespoke, architectural solutions. 

The visual language is rooted in **Minimalism** with **High-Contrast** accents. By utilizing an ultra-dark canvas, we emphasize the "glow" of the craftsmanship, mirroring how neon light interacts with polished stone or dark wood. A subtle grain texture overlay should be applied globally at low opacity (2-3%) to evoke the physical tactility of raw materials like marble and timber.

## Colors
The palette is built on deep obsidian tones to provide maximum contrast for the neon green primary accent. 

- **Primary Neon:** Use `#00FF41` for critical calls to action, active states, and decorative "glow" elements.
- **Surface Tiers:** Use the primary background for the main canvas, secondary for cards, and tertiary for input fields or nested components.
- **Functional Borders:** Borders use a subtle `#2A2A2A` to maintain a structural feel without creating visual clutter.
- **Glow Logic:** Any element using the primary accent should consider a subtle `box-shadow` or `text-shadow` using the secondary `#00CC35` at 40-60% opacity to simulate a physical neon radiance.

## Typography
The typography system uses a "Technical vs. Fluid" pairing. **Space Grotesk** provides a geometric, architectural foundation for headings, echoing the precision of CNC machinery. **Outfit** is used for body text to ensure readability and a modern, approachable feel.

Large-scale headlines are a core part of the brand identity. High-contrast sizing between labels and headers creates a rhythmic, editorial flow. Always use uppercase for `label` styles to enhance the technical aesthetic.

## Layout & Spacing
The layout philosophy is based on a **fixed-width container** for desktop to ensure the architectural alignment of content. Use a 12-column grid with generous margins to create an "expensive" feel through whitespace.

Spacing follows an 8px linear scale. Section vertical padding should be substantial (120px+) to allow the high-contrast typography and product imagery to "breathe." On mobile, the layout shifts to a single column with reduced margins but maintains the 8px rhythm.

## Elevation & Depth
In this exclusively dark system, depth is conveyed through **Tonal Layers** and **Radiant Glows** rather than traditional shadows.

- **Level 0 (Base):** `#0A0A0A` – The infinite background.
- **Level 1 (Cards/Sections):** `#111111` – Subtle lift, used for main content areas.
- **Level 2 (Popovers/Modals):** `#1A1A1A` – Highest elevation, always paired with a thin `#2A2A2A` border.
- **Accent Glow:** Interactive elements do not cast black shadows; they emit a green aura (`0px 4px 20px rgba(0, 255, 65, 0.2)`).

## Shapes
The shape language is defined by a contrast between **Pill-shaped (Fully Rounded)** interactive elements and **Sharp-edged** structural containers. 

Buttons, badges, and chips must always be pill-shaped (`rounded-full`). This softens the aggressive nature of the neon-on-black color scheme. Conversely, image containers and section dividers should remain sharp or have very minimal rounding to maintain the architectural "stone" feel.

## Components
- **Buttons:** Primary buttons are pill-shaped with a solid `#00FF41` background and black text. On hover, they should exhibit a subtle outer glow. Secondary buttons are outlined with a 1px border.
- **Inputs:** Dark backgrounds (`#1A1A1A`) with a bottom-only border or a full subtle border. Focus state triggers a primary green border and a soft glow.
- **Cards:** Use `#111111` with no shadow, relying on the `#2A2A2A` border for definition.
- **Badges:** Small, pill-shaped elements with `label-md` typography. Use these for categories like "Marble," "Granite," or "Bespoke."
- **Progressive Disclosure:** Use clean, minimalist icons (thin stroke weight) that rotate 90 degrees on interaction.
- **Texture Overlay:** Apply a global pseudo-element with a noise texture SVG at 3% opacity over the entire viewport to give the UI a "material" quality.
