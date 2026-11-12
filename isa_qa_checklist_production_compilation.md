# ISA — Final Quality Assurance (QA) Checklist
*Document Reference: ISA-QA-CHECKLIST-V1.0*

### 1. Architectural & Privacy Compliance (Sovereign Core)
- [ ] **Zero PII Harvesting**: No input fields for email, real name, phone, or password exist anywhere across the suite.
- [ ] **Client-Side Persistence**: Progress, streak, points, and inventory save to `window.localStorage` (`isa-progress-v1`) and `IndexedDB v1`.
- [ ] **Data Export**: The `isa-backup-progress.json` backup downloads cleanly as a valid signed JSON file without requiring server connectivity.
- [ ] **Destructive Safe Purge**: The two-step confirmation modal wipes local storage completely, resets memory telemetry to 0 bytes, and redirects to initial state.
- [ ] **Offline Operation**: The app operates in **MODO LOCAL SEGURO** when offline with zero console network errors.

### 2. Terminology & Legal Guardrails
- [ ] **Zero Military / Cadet Terminology**: All learner references are strictly **"Visitante" (Visitor)** or **"Explorador" (Explorer)**. No instances of "Cadet" or "Cadete" appear in UI text, code, or documentation.
- [ ] **Sync Labeling**: Sync state displays as **"MODO LOCAL SEGURO"** or **"SIN CONEXIÓN ACTIVA"**. No internal network references (e.g., DNS, off-grid) appear in user-facing UI.
- [ ] **Institutional Waivers (Mandatory on Every Screen)**:
  - *"RECONOCIMIENTO SIMBÓLICO — NO ES UNA CERTIFICACIÓN ACADÉMICA / SYMBOLIC RECOGNITION — NOT AN ACADEMIC CERTIFICATION"*
  - *"Privacy by design. Minimal pseudonymous data. No email stored in plaintext. Local-first credential record. No account required."*
  - *"Todo lo que ves es ficción. Los museos y su contexto histórico son reales."*

### 3. Visual & Interaction Quality
- [ ] **Touch Targets**: All buttons, pills, matrix cells, and interactive nodes meet or exceed the **48×48 px** minimum touch target boundary.
- [ ] **Typography Scale**: Body copy is 16–18 px; telemetry/metadata is 13–15 px; zero text below 12 px. Space Grotesk used for headers/UI and Monospace for telemetry.
- [ ] **Dual Lighting Modes**:
  - **Day Ops**: Emerald Radar `#38e8a6` on dark naval background `#08151e`.
  - **Night Ops**: Battle Lantern Red `#FF3B30` on deep hull background `#050a0d`.
  - Color toggle triggers instantaneously with zero layout shift.
- [ ] **Bilingual Toggle (ES / EN)**: Language switch executes synchronously with zero layout shift using `data-i18n` attributes.
- [ ] **Share Card (9:16)**: Generates a 9:16 vertical PNG named `ISA_MiColeccion_YYYY-MM.png` with legible contrast in both Day and Night Ops modes.
