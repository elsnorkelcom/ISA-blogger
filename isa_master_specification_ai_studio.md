# ISA — INTERNATIONAL SUBMARINE ACADEMY
## Master Technical Specification for Google AI Studio Compilation
*Document Reference: ISA-PROD-SPEC-V1.0 // SOBERANÍA Y TELEMETRÍA NAVAL*

---

### 1. Vision and Product Architecture
The **International Submarine Academy (ISA)** is an educational, transmedia, local-first web platform connecting real-world submarine museum heritage with STEM curriculum (aligned with TIMSS Grade 8 Science & Mathematics).

- **Sovereign Local-First Core**: Zero PII harvesting. No backend requirement for MVP. No accounts, emails, passwords, trackers, or commercial telemetry.
- **Client Storage**: All progression, medals, tokens, and preferences reside strictly within `window.localStorage` (`isa-progress-v1`) and `IndexedDB v1`.
- **Bilingual Interface**: Native, instantaneous EN/ES toggle with zero layout shift (`data-i18n` bindings).
  - *Guiding Principle*: "English for the world. Spanish for the experience."
- **Dual Visual Modes**: Seamless toggle between **Day Ops** (Naval Emerald) and **Night Ops** (Battle Lantern Red).
- **Core Persona & Terminology Constraint**: All references to learners are strictly **"Visitante" (Visitor)** or **"Explorador" (Explorer)**. Military rank or student terms like "Cadet/Cadete" are strictly prohibited.

---

### 2. Design System & Theming Tokens

```css
:root {
  /* Day Ops (Default Theme) */
  --isa-bg-dark: #08151e;
  --isa-surface-day: #101d26;
  --isa-surface-card-day: #162734;
  --isa-surface-bright: #2e3b45;
  --isa-accent-day: #38e8a6;          /* Radar Emerald */
  --isa-accent-day-glow: rgba(56, 232, 166, 0.25);
  --isa-text-day: #e6edf3;
  --isa-text-muted-day: #8b9bb4;
  --isa-border-day: rgba(56, 232, 166, 0.25);

  /* Night Ops (Battle Lantern Mode) */
  --isa-bg-night: #050a0d;
  --isa-surface-night: #0e0506;
  --isa-surface-card-night: #18080a;
  --isa-accent-night: #FF3B30;        /* Battle Lantern Crimson */
  --isa-accent-night-glow: rgba(255, 59, 48, 0.28);
  --isa-text-night: #FFB3B3;
  --isa-text-muted-night: #FF6B6B;
  --isa-border-night: rgba(255, 59, 48, 0.35);

  /* Active Dynamic Bindings */
  --bg-current: var(--isa-bg-dark);
  --surface-current: var(--isa-surface-day);
  --surface-card-current: var(--isa-surface-card-day);
  --accent-current: var(--isa-accent-day);
  --text-current: var(--isa-text-day);
  --text-muted-current: var(--isa-text-muted-day);
  --border-current: var(--isa-border-day);
  --glow-current: var(--isa-accent-day-glow);

  /* Typography */
  --font-display: 'Space Grotesk', system-ui, sans-serif;
  --font-telemetry: 'JetBrains Mono', 'Fira Code', monospace;
  --min-touch-target: 48px;
}

body[data-theme="night"],
html[data-theme="night"] {
  --bg-current: var(--isa-bg-night);
  --surface-current: var(--isa-surface-night);
  --surface-card-current: var(--isa-surface-card-night);
  --accent-current: var(--isa-accent-night);
  --text-current: var(--isa-text-night);
  --text-muted-current: var(--isa-text-muted-night);
  --border-current: var(--isa-border-night);
  --glow-current: var(--isa-accent-night-glow);
}
```

---

### 3. Screen Inventory & Viewport Specifications

| # | Screen Production Title | Device / Archetype | Route / Shell ID | Key Functional Specs |
|---|---|---|---|---|
| 01 | **ISA - Classified Key Entry Terminal** | Mobile (Full Splash) | `/access` (blank) | Monospace PIN terminal, instant demo access bypass, simulation disclaimer. |
| 02 | **ISA - Home Discovery Stream (Night Ops & Logo)** | Mobile Tab Navigation | `/home` (tab) | Two-column responsive stream, topic filter pills, Night Ops toggle, sound toggle. |
| 03 | **ISA - Mission Map & 5x5 Mission Grid** | Mobile Tab Navigation | `/map` (tab) | 25-cell TIMSS interactive matrix, Steel/Copper/Bronze seasons, node status indicators. |
| 04 | **ISA - Video Challenge HUD & Elena Intercom** | Mobile Stack Navigation | `/episode/:id/challenge` (stack) | Video playback finish trigger, tactical HUD question overlay, Elena mentor intercom modal on miss. |
| 05 | **ISA - Answer Feedback & Circuit Resolution** | Mobile Stack Navigation | `/episode/:id/feedback` (stack) | STEM rationale breakdown, mechanical system tie-in, nominal radar sweep transition. |
| 06 | **ISA - Copper Reward & Credential Transition** | Mobile Stack Navigation | `/reward/:missionId` (stack) | 3D lighting coin render, +100 PTS streak count, Local Integrity Signature chip. |
| 07 | **ISA - Badge Registry & Stepped Coin Rack** | Mobile Tab Navigation | `/badges` (tab) | Stepped physical coin rack shelf (Acero/Cobre/Bronce), search input, assembly blueprint. |
| 08 | **ISA - Share Card Vertical (9:16)** | Mobile Stack Navigation | `/badges/share` (stack) | HTML5 Canvas 9:16 story exporter (`ISA_MiColeccion_YYYY-MM.png`), Web Share API. |
| 09 | **ISA - Visitor Profile (Explorer Profile)** | Mobile Tab Navigation | `/profile` (tab) | Pseudonymous callsign, radar STEM skills chart, visit record, verified visitor stats. |
| 10 | **ISA - Nickname Selection & Callsign Terminal** | Mobile Tab Navigation | `/profile/callsign` (tab) | Local salt generator, suggestions list (`LUNAR FISH #884`), anti-PII sanitizer. |
| 11 | **ISA - Operational Sync Bridge** | Mobile Tab Navigation | `/sync` (tab) | Modo Local Seguro indicator, pending queue inspection, JSON backup download (`Blob`). |
| 12 | **ISA - Privacy Transparency & Sovereign Consent** | Mobile Stack Navigation | `/privacy` (stack) | 4 Pillars of Sovereign Privacy, live memory byte inspector, two-step safe purge modal. |
| 13 | **ISA - Museum Directory & Museum Profile (BAP Abtao / U-995)** | Mobile Tab / Stack | `/museums` (tab) | 160-vessel registry, coordinates telemetry, 3D model/virtual tour launch links. |
| 14 | **ISA - Desktop Helm & Responsive Map Directory** | Desktop Web Dashboard | `/desktop` (dashboard) | Two-column desktop helm with interactive 2D Leaflet / 3D Globe visualization. |

---

### 4. Mandatory Institutional Legal Disclaimers (Strictly Required on Every Screen)
1. **Academic Recognition Waiver**:
   > *"RECONOCIMIENTO SIMBÓLICO — NO ES UNA CERTIFICACIÓN ACADÉMICA / SYMBOLIC RECOGNITION — NOT AN ACADEMIC CERTIFICATION"*
2. **Sovereign Privacy Guarantee**:
   > *"Privacy by design. Minimal pseudonymous data. No email stored in plaintext. Local-first credential record. No account required."*
3. **Narrative Grounding**:
   > *"Todo lo que ves es ficción. Los museos y su contexto histórico son reales."*
