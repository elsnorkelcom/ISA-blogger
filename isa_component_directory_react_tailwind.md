# ISA — Production Architecture & Component Directory
*Tech Stack: React 18+ / TypeScript / Tailwind CSS / Lucide Icons*

```
src/
├── assets/
│   ├── branding/
│   │   ├── isa-crest-logo.svg           # Official ISA STEM+A Emblem
│   │   └── periscope-reticle.svg        # Optical Periscope HUD Graticule
│   └── images/
│       ├── elena-mentor.png             # Chief Engineer Elena Intercom Portrait
│       ├── coins/                       # High-relief metal coins (Steel/Copper/Bronze)
│       └── ribbons/                     # 20 STEM + 15 Human Factor Ribbons
│
├── components/
│   ├── layout/
│   │   ├── AppHeader.tsx                # Dynamic Header (Logo, Callsign chip, Day/Night toggle, EN/ES)
│   │   ├── BottomNav.tsx                # Fixed 5-tab persistent bottom bar (Touch targets ≥ 48px)
│   │   ├── DesktopSidebar.tsx           # Two-column Desktop Helm navigation rail
│   │   └── InstitutionalFooter.tsx      # Disclaimers: TIMSS recognition waiver & Sovereign Privacy
│   │
│   ├── common/
│   │   ├── TacticalButton.tsx           # Monospace button with radar glow states (min 48px)
│   │   ├── NightOpsToggle.tsx           # Instant battle lantern switch (Emerald #38e8a6 ↔ Crimson #FF3B30)
│   │   ├── LanguageToggle.tsx           # Synchronous ES/EN data-i18n state switcher
│   │   └── DisclaimerNotice.tsx         # Legal waiver & fiction reminder callouts
│   │
│   ├── access/
│   │   └── PinPadTerminal.tsx           # Monospace security keypad with bypass demo mode
│   │
│   ├── discovery/
│   │   ├── StreamCard.tsx               # Content card with episode duration, museum tag & STEM badge
│   │   └── TopicFilterPills.tsx         # Specialty pills (Maquinista, Electricista, Electrónico, Naval, Logístico)
│   │
│   ├── grid/
│   │   ├── MissionMatrix5x5.tsx         # Interactive 25-cell TIMSS interactive progression grid
│   │   └── CellDetailModal.tsx          # TIMSS G8 domain preview with variant inspector
│   │
│   ├── evaluation/
│   │   ├── VideoHUDOverlay.tsx          # Question trigger over completed video player
│   │   ├── ElenaIntercomModal.tsx       # Chief Engineer emergency audio/text pedagogical cue
│   │   └── FeedbackCard.tsx             # Post-answer breakdown & STEM concept explanation
│   │
│   ├── rewards/
│   │   ├── SteppedCoinRack.tsx          # Physical perspective stepped shelf for coins
│   │   ├── ShareCard916.tsx             # HTML5 Canvas 9:16 vertical social story generator
│   │   └── SubmarineBlueprint.tsx       # Modular 4-compartment hull completion diagram
│   │
│   ├── museums/
│   │   ├── MuseumMapLeaflet.tsx         # 2D responsive OpenStreetMap / Leaflet container
│   │   ├── GlobeView3D.tsx              # Three.js / WebGL lightweight globe for desktop
│   │   └── MuseumProfileCard.tsx        # 160-vessel directory card with coordinates and virtual tours
│   │
│   └── sovereignty/
│       ├── MemoryByteInspector.tsx      # Live IndexedDB / localStorage byte telemetry
│       ├── CallsignGenerator.tsx        # Local-first cryptographic salt & suggestions generator
│       ├── BackupExporter.tsx           # Blob-based instant isa-backup-progress.json download
│       └── SafePurgeModal.tsx           # Two-step confirmation dialog with irreversible wipeout
│
├── hooks/
│   ├── useThemeMode.ts                  # Persistent Day/Night Ops state manager
│   ├── useLanguage.ts                   # Instantaneous bilingual dictionary binding
│   ├── useVisitorProgress.ts            # Local-first client state (points, streak, badges, missions)
│   └── useOfflineSync.ts                # Pending queue reconciliation with Local-Wins logic
│
├── services/
│   ├── storageEngine.ts                 # IndexedDB v1 & window.localStorage wrapper
│   ├── callsignSanitizer.ts             # Zero-PII filter (strips emails, names, phone patterns)
│   └── canvasExporter.ts                # 9:16 offscreen canvas renderer for social sharing
│
└── types/
    ├── mission.ts                       # Specialty, Discipline, TIMSS domains & Question structures
    ├── visitor.ts                       # Anonymous Visitor Profile, telemetry & credential hash
    └── museum.ts                        # 160 museum submarines, coordinates & historical dossiers
```
