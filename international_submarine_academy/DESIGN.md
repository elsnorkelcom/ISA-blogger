---
name: International Submarine Academy
colors:
  surface: '#08151e'
  surface-dim: '#08151e'
  surface-bright: '#2e3b45'
  surface-container-lowest: '#040f18'
  surface-container-low: '#101d26'
  surface-container: '#14212a'
  surface-container-high: '#1f2b35'
  surface-container-highest: '#2a3640'
  on-surface: '#d7e4f1'
  on-surface-variant: '#bacabf'
  inverse-surface: '#d7e4f1'
  inverse-on-surface: '#25323c'
  outline: '#85948a'
  outline-variant: '#3c4a41'
  surface-tint: '#2be19f'
  primary: '#92ffca'
  on-primary: '#003824'
  primary-container: '#38e8a6'
  on-primary-container: '#006444'
  inverse-primary: '#006c49'
  secondary: '#ffb784'
  on-secondary: '#4f2500'
  secondary-container: '#8a4400'
  on-secondary-container: '#ffc095'
  tertiary: '#ffe6c9'
  on-tertiary: '#452b00'
  tertiary-container: '#ffc36f'
  on-tertiary-container: '#794e00'
  error: '#ffb4ab'
  on-error: '#690005'
  error-container: '#93000a'
  on-error-container: '#ffdad6'
  primary-fixed: '#56feba'
  primary-fixed-dim: '#2be19f'
  on-primary-fixed: '#002113'
  on-primary-fixed-variant: '#005236'
  secondary-fixed: '#ffdcc6'
  secondary-fixed-dim: '#ffb784'
  on-secondary-fixed: '#301400'
  on-secondary-fixed-variant: '#713700'
  tertiary-fixed: '#ffddb3'
  tertiary-fixed-dim: '#ffb952'
  on-tertiary-fixed: '#291800'
  on-tertiary-fixed-variant: '#633f00'
  background: '#08151e'
  on-background: '#d7e4f1'
  surface-variant: '#2a3640'
typography:
  display-hero:
    fontFamily: Space Grotesk
    fontSize: 4rem
    fontWeight: '700'
    lineHeight: 4.5rem
    letterSpacing: -0.03em
  display-hero-mobile:
    fontFamily: Space Grotesk
    fontSize: 2.25rem
    fontWeight: '700'
    lineHeight: 2.75rem
    letterSpacing: -0.02em
  headline-lg:
    fontFamily: Space Grotesk
    fontSize: 2.5rem
    fontWeight: '600'
    lineHeight: 3rem
    letterSpacing: -0.02em
  headline-lg-mobile:
    fontFamily: Space Grotesk
    fontSize: 1.75rem
    fontWeight: '600'
    lineHeight: 2.25rem
    letterSpacing: -0.01em
  headline-md:
    fontFamily: Space Grotesk
    fontSize: 1.75rem
    fontWeight: '600'
    lineHeight: 2.25rem
    letterSpacing: 0em
  headline-sm:
    fontFamily: Space Grotesk
    fontSize: 1.25rem
    fontWeight: '500'
    lineHeight: 1.75rem
    letterSpacing: 0.01em
  body-lg:
    fontFamily: Chivo
    fontSize: 1.125rem
    fontWeight: '400'
    lineHeight: 1.75rem
    letterSpacing: 0.01em
  body-md:
    fontFamily: Chivo
    fontSize: 1rem
    fontWeight: '400'
    lineHeight: 1.5rem
    letterSpacing: 0em
  body-sm:
    fontFamily: Chivo
    fontSize: 0.875rem
    fontWeight: '400'
    lineHeight: 1.375rem
    letterSpacing: 0.01em
  telemetry-lg:
    fontFamily: Space Mono
    fontSize: 1rem
    fontWeight: '700'
    lineHeight: 1.5rem
    letterSpacing: 0.08em
  telemetry-sm:
    fontFamily: Space Mono
    fontSize: 0.75rem
    fontWeight: '400'
    lineHeight: 1rem
    letterSpacing: 0.12em
  label-caps:
    fontFamily: Space Mono
    fontSize: 0.6875rem
    fontWeight: '700'
    lineHeight: 1rem
    letterSpacing: 0.15em
spacing:
  gutter: 1.5rem
  gutter-mobile: 1rem
  margin: 3rem
  margin-mobile: 1.25rem
  space-xs: 0.25rem
  space-sm: 0.5rem
  space-md: 1rem
  space-lg: 1.5rem
  space-xl: 2.5rem
---

## Brand & Style
The brand embodies maritime authority, classified technological stewardship, and deep-sea exploration. It serves naval historians, STEM+A educators, cadets, and digital researchers seeking immersive naval engineering and maritime heritage archives.

The aesthetic fuses **Classified Tactical Archive** with **Deep-Ocean Oceanic Sci-Fi**. Interface elements borrow functional metaphors from submarine helm instrumentation: sonar sweep indicators, telemetry readouts, acoustic signatures, and pressure-rated structural grids. Contrast remains strictly tuned for high legibility in low-light environments, evoking the atmosphere of a deep-submergence command module combined with the archival precision of a military naval museum.

## Colors
The default palette is tuned strictly for night-ops dark mode to replicate submersible helm consoles and pressure hull displays.

- **Primary (`#38E8A6` - Radar Green):** Vector sweeps, active sonar returns, confirmed targets, operational readiness markers, and primary user interactions.
- **Secondary (`#C87533` - Hull Copper):** Ballast metrics, engineering schematics, historic artifact annotations, and brass instrumentation accents.
- **Tertiary (`#FFB74A` - Alert Amber):** Depth alerts, pressure anomalies, radiation/atmosphere telemetry cautions, and historic archival flags.
- **Neutral (`#8A97A3` - Marine Steel):** Structural borders, bulkhead framing lines, inactive data indicators, and tertiary metadata.
- **Deep Canvas (`#04121F` & `#05080C`):** Midnight oceanic depth and near-black pressure-hull base layers.
- **Off-White (`#EAF2F5` - Deck Strobe):** Uncompromising high-readability text for critical body paragraphs and archival documents.

## Typography
The system enforces a dual-voice typographical hierarchy:

1. **Space Grotesk (Command & Structural Display):** Sharp geometric grotesque handling tactical headings, mission titles, artifact classification indices, and module banners.
2. **Chivo (Tactical Narrative & Body):** High-efficiency neutral grotesque handling dense STEM pedagogical explanations, oral histories, and archival dossiers.
3. **Space Mono (Telemetry & Telecommunication):** Monospaced computational typeface applied to coordinates, depth soundings, Morse transcription strings, UTC timestamps, and sensor telemetry.

Always render telemetry tokens and system tags in full uppercase with expanded letter-spacing to ensure absolute legibility against dark tactical surfaces.

## Layout & Spacing
The layout follows a strict 12-column tactical bulkhead grid on desktop, scaling to 6 columns on tablet, and 4 columns on mobile viewport configurations.

- **Desktop (1200px+):** 12 columns with 24px gutters and 48px outer margins. Panels align cleanly to column boundaries mimicking segmented sub-aquatic console arrays.
- **Tablet (768px – 1199px):** 6 columns with 20px gutters and 32px margins. Auxiliary telemetry modules collapse into expandable command drawers.
- **Mobile (< 768px):** 4 columns with 16px gutters and 20px margins. Telemetry lines snap to horizontal status bands with vertical stacking.

Grid intersections may display crosshair reticles or corner ticks (`+` markers) using the steel grey token at 40% opacity to reinforce the technical apparatus feel.

## Elevation & Depth
Depth is constructed through **Tonal Pressure Layering** and **Phosphor Backlighting** rather than organic blurred drop shadows:

- **Hull Bed (`#05080C`):** Deepest background baseline. Unfocused areas remain deep oceanic black.
- **Bulkhead Compartments (`#04121F`):** Standard container background for cards, viewports, and primary panels.
- **Interactive Deck (`#0A1F33`):** Active or hover state surfaces with hard-edged technical delineation.
- **Borders & Reticles:** Hairline strokes (1px) in `#8A97A3` at 25% opacity for passive containers, shifting to `#38E8A6` at 80% opacity when locked or active.
- **Phosphor Bloom:** Focused indicators, primary controls, and active tracking points emit a short-radius glow: `0 0 12px rgba(56, 232, 166, 0.35)`.
- **Scanlines:** Archival viewport screens utilize a subtle 2px repeating horizontal CSS scanline overlay at 4% opacity to mimic authentic cathode-ray telemetry monitors.

## Shapes
The shape architecture is uncompromisingly architectural, clinical, and utilitarian. A roundedness index of `0` ensures sharp corners that match watertight bulkhead construction, tactical glass consoles, and stamped military plates.

- Standard modules feature precise 90-degree orthogonal corners.
- Specialized telemetry cards and action buttons feature 45-degree chamfered corners (clip-path `polygon` cuts of 6px to 10px) on top-right and bottom-left diagonal axes to evoke modular subsea avionics and industrial chassis plates.

## Components

### Buttons & Tactical Triggers
- **Primary (Action/Engage):** Chamfered rectangle filled with `#38E8A6`, text in `#05080C` (`telemetry-lg`). On hover, emits a sharp radar bloom (`0 0 16px rgba(56, 232, 166, 0.5)`).
- **Secondary (Override/Archive):** Outline button with 1px border in `#C87533`, text in `#C87533`. Background shifts to `#C87533` at 15% opacity on hover.
- **Ghost/Auxiliary:** 1px border in `#8A97A3` (40% opacity) with text in `#EAF2F5`. Displays monospaced terminal brackets `[ SYS_EXEC ]` around action labels.

### Chips & Sensor Badges
- Compact monospaced labels (`telemetry-sm`) framed with hairline borders.
- Preceded by a blinking or static circular tracking dot (`4px` by `4px`). Green for operational, Amber for cautionary depth/system state, Copper for historic archival tier.

### Cards & Compartment Panels
- Containers feature `#04121F` solid fills bordered with 1px `#8A97A3` at 30% opacity.
- Top panel headers include integrated tactical coordinates (e.g., `SEC_04 // LAT: 45.109 N`) in `telemetry-sm` typography.
- Outer corner framing can incorporate Morse code border notches (alternating 4px and 12px segment dash strokes) along horizontal divider lines.

### Inputs & Terminal Fields
- Inset box styling using `#05080C` backdrop with a sharp 1px border in `#8A97A3`.
- Active focus state swaps border to `#38E8A6` and initiates an active square cursor blink (`|` or `█`).
- Placeholder text in `#8A97A3` styled with `label-caps`.

### Checkboxes & Tactical Toggles
- Custom square selectors (`0px` border-radius). Checked states display an inverted green crosshair (`×` or `+`) using `#38E8A6` over a deep navy fill.

### Domain-Specific Components
- **Sonar Ping Radar Visualizer:** Circular concentric range rings rendered in 1px `#38E8A6` (20% opacity) with a continuously sweeping radial gradient arm indicating dynamic data streaming.
- **Acoustic Waveform Visualizer:** Oscilloscope-style audio player interface for hydrophone hydro-acoustic logs and submarine oral heritage recordings.
- **Morse Ribbon Dividers:** Section separators integrating dynamic Morse code translations of academy mottos and STEM curriculum classification codes.