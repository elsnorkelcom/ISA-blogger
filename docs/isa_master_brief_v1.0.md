# ISA — INTERNATIONAL SUBMARINE ACADEMY
# MASTER BRIEF & TECHNICAL SPECIFICATION V1.0
*Document Reference: ISA-MASTER-BRIEF-V1.0 // SOBERANÍA Y TELEMETRÍA NAVAL*
*Single Source of Truth (SSOT) para Stitch, Google AI Studio y Desarrolladores Futuros*

---

## 1. VERSION & STATUS

- **Versión**: `v1.0 — MVP Funcional, Modular y Mejorable`.
- **Fecha de Compilación**: Febrero 2025.
- **Alcance**: Arquitectura frontend cliente-soberana, capa de descubrimiento en Blogger, base de datos relacional desacoplada en Google Sheets con motor de automatización en Google Apps Script, suite completa de 12 pantallas/rutas funcionales, banco curricular STEM (TIMSS Grado 8) y Factor Humano, y protocolo de gobernanza de privacidad local-first.
- **Titularidad & Operación**:
  - *Iniciativa*: International Submarine Academy (ISA) en colaboración con El Snorkel (`elsnorkel.com`).
  - *Liderazgo Curatorial y Técnico*: Equipo de Preservación Histórica y Pedagogía Naval ISA.
  - *Diseño & Prototipado*: Stitch Design System Suite.
  - *Implementación de Referencia*: Google AI Studio (SPA Vanilla JS / ES Modules).

---

## 2. VISION & PRINCIPLES

### 2.1. Misión de ISA
La **International Submarine Academy (ISA)** es una plataforma educativa transmedia y un archivo inmersivo naval diseñado para transformar el patrimonio de más de 160 submarinos museo del mundo en portales de acceso a las ciencias duras (STEM: Ciencia, Tecnología, Ingeniería y Matemáticas) y a la memoria viva de la navegación submarina.

> *«Todo lo que ves es ficción. Los museos y su contexto histórico son reales. La experiencia hace que el visitante quiera regresar a un submarino museo real.»*

### 2.2. Soberanía Local-First (*Zero-Cloud Lock-in*)
- **Sin Dependencia de Servidor Central**: La aplicación opera de forma 100% funcional en el navegador del usuario. El progreso, las evaluaciones, los puntos, la racha y las insignias no requieren autenticación en la nube para persistir.
- **Propiedad Radical del Dato**: El usuario es el único propietario de su bitácora. Puede inspeccionar los bytes exactos utilizados, descargar su respaldo como JSON abierto y legible, o destruirlo de manera irreversible en cualquier momento.

### 2.3. Privacidad por Diseño (*Privacy by Design & Zero PII*)
- **Cero Recolección de Datos Personales (PII)**: Queda terminantemente prohibido incorporar campos de correo electrónico, nombre real, teléfono, contraseñas o datos biométricos.
- **Identidad Seudónima**: El identificador de exploración (*Callsign*, ej. `LUNAR FISH #884`) se deriva localmente en el cliente mediante un salt criptográfico efímero almacenado en el dispositivo.
- **Cero Rastreadores Comerciales**: No se inyectan cookies de terceros, píxeles de seguimiento ni telemetría comercial.

---

## 3. TECH STACK (ARQUITECTURA DE PRODUCCIÓN)

Para garantizar portabilidad absoluta, compatibilidad nativa con Blogger y ausencia de sobrecargas de compilación (*zero build step*), el stack se define estrictamente de la siguiente manera:

- **Lenguaje Core**: Vanilla JavaScript moderno (**ES Modules / ECMAScript 2022+**).
- **Estilos & Diseño**: **CSS Custom Properties** (Variables nativas con transiciones de color de 450ms) y utilidades semánticas puras.
- **Sin Frameworks Pesados**: **CERO React, CERO Tailwind compiler en tiempo de ejecución, CERO Node/Webpack/Vite**.
- **Compatibilidad con Blogger**: Capaz de ser embebido directamente en una plantilla XML de Blogger, en un gadget HTML/JavaScript o servido como SPA estática independiente alojada en GitHub Pages / CDN sin dependencias externas.
- **Almacenamiento Cliente**:
  - `window.localStorage`: Para configuraciones inmediatas (`isa-theme`, `isa-lang`, versión de esquema).
  - `IndexedDB v1` (Base: `isa-progress-v1`): Para el registro relacional de misiones completadas, respuestas TIMSS, racha y catálogo de monedas/cintas.
- **Renderizado de Exportación**: HTML5 `<canvas>` nativo para generación síncrona en cliente de tarjetas gráficas (9:16).

---

## 4. ARCHITECTURE & DATA FLOW

El ecosistema ISA desacopla la autoría y curaduría editorial de la experiencia de usuario final:

```
┌─────────────────────────────────────────────────────────────────┐
│               1. CAPA EDITORIAL & CURADURÍA                     │
│   Google Sheets (ISA_Base.xlsx - 18 pestañas, 213 columnas)     │
│   - Catálogo de 160 museos reales                               │
│   - Reactivos TIMSS G8 y Factor Humano                          │
└────────────────────────────────┬────────────────────────────────┘
                                 │
                                 ▼ Exportación JSON / Webhook
┌─────────────────────────────────────────────────────────────────┐
│              2. MOTOR DE AUTOMATIZACIÓN (MIDDLEWARE)            │
│   Google Apps Script (Scripts de Sincronización)                │
│   - Validador de esquema y relaciones de clave foránea          │
│   - Publicador estático de JSON versionados (seed/dataset)      │
└────────────────────────────────┬────────────────────────────────┘
                                 │
                                 ▼ Inyección de JSON / Publicación
┌─────────────────────────────────────────────────────────────────┐
│               3. CAPA DE DESCUBRIMIENTO PÚBLICA                 │
│   Blogger (elsnorkel.com / Blog ISA)                            │
│   - Artículos, fichas de museos y docu-cortos en video          │
│   - Plantilla ligera con marcado semántico SEO                  │
└────────────────────────────────┬────────────────────────────────┘
                                 │
                                 ▼ Marco Embebido / App Host
┌─────────────────────────────────────────────────────────────────┐
│              4. EXPERIENCIA DE INMERSIÓN (SPA CLIENTE)          │
│   ISA Client Engine (Vanilla JS + CSS Custom Properties)        │
│   - 12 Pantallas de Interfaz Táctica / HUD                      │
│   - Persistencia Soberana en IndexedDB / localStorage           │
│   - Conmutación Day Ops / Night Ops instantánea                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## 5. DATA MODEL SUMMARY (`ISA_Base.xlsx`)

Basado en el modelo relacional aprobado en `26_BASE_SHEET.md`, estructurado en **18 pestañas y 213 columnas técnicas**:

### 5.1. Inventario de Tablas
1. `LEEME`: Guía técnica y diccionario de validación.
2. `Config` (7 cols): Parámetros globales (versión de semilla, tiempo de temporizador, bandera de audio, textos de bienvenida).
3. `Instituciones` (11 cols): Entidades académicas y armadas conservadoras de museos.
4. `Claves` (9 cols): Hash de claves maestras para acceso al terminal (nunca publicada en frontend).
5. `Museos` (28 cols): Directorio de 160 submarinos históricos (coordenadas GPS, clase, año de botadura, enlaces virtuales).
6. `Compartimentos` (8 cols): Estaciones del buque (Proa, Baterías, Central, Máquinas, Popa).
7. `Sistemas` (10 cols): Equipos navales (Periscopio, Ecosonda, Diésel, Scrubber, Torpedos).
8. `Temporadas` (12 cols): Progresión elemental: Acero, Cobre, Bronce, Plata, Oro.
9. `Episodios` (15 cols): Docu-cortos enlazados a museos y sistemas.
10. `Misiones` (18 cols): Nodos de desafío en grilla o estación.
11. `Reactivos` (23 cols): Banco de preguntas curriculares TIMSS Grado 8 y testimonios históricos.
12. `Insignias` (15 cols): Metadatos de medallas físicas y cintas conmemorativas.
13. `Roles` (7 cols): Especialidades operativas: Maquinista, Electricista, Electrónico, Naval, Logístico.
14. `Disciplinas` (7 cols): Cuadrantes STEM+A (Ciencias, Tecnología, Ingeniería, Matemática, Humanidades/Artes).
15. `Grilla_5x5` (7 cols): Mapeo bidimensional de la matriz TIMSS 25 celdas.
16. `Credenciales_Emitidas` (15 cols): Registro cliente de firmas de integridad.
17. `Propuestas` (12 cols): Buzón futuro de retroalimentación de museos.
18. `Metricas` (9 cols): Contadores locales agregados.

---

## 6. DESIGN SYSTEM & VISUAL TOKENS

### 6.1. Paleta de Iluminación Dual (Sheet Config Synced)

```css
:root {
  /* Transiciones Tácticas */
  --transition-theme: background-color 0.45s cubic-bezier(0.4, 0, 0.2, 1),
                      border-color 0.45s cubic-bezier(0.4, 0, 0.2, 1),
                      color 0.35s ease,
                      box-shadow 0.45s ease;

  /* Day Ops (Modo Radar Diurno) */
  --isa-bg-dark: #08151e;
  --isa-surface-day: #101d26;
  --isa-surface-card-day: #162734;
  --isa-surface-bright: #2e3b45;
  --isa-accent-day: #38e8a6;              /* Verde Radar Esmeralda */
  --isa-accent-day-glow: rgba(56, 232, 166, 0.25);
  --isa-text-day: #e6edf3;
  --isa-text-muted-day: #8b9bb4;
  --isa-border-day: rgba(56, 232, 166, 0.25);

  /* Night Ops (Modo Linterna Roja de Batalla Submarina) */
  --isa-bg-night: #050a0d;
  --isa-surface-night: #0e0506;
  --isa-surface-card-night: #18080a;
  --isa-accent-night: #FF3B30;            /* Rojo Carmesí Linterna de Batalla */
  --isa-accent-night-glow: rgba(255, 59, 48, 0.28);
  --isa-text-night: #FFB3B3;
  --isa-text-muted-night: #FF6B6B;
  --isa-border-night: rgba(255, 59, 48, 0.35);

  /* Mapeo Activo Semántico por Defecto */
  --bg-current: var(--isa-bg-dark);
  --surface-current: var(--isa-surface-day);
  --surface-card-current: var(--isa-surface-card-day);
  --accent-current: var(--isa-accent-day);
  --text-current: var(--isa-text-day);
  --text-muted-current: var(--isa-text-muted-day);
  --border-current: var(--isa-border-day);
  --glow-current: var(--isa-accent-day-glow);

  /* Tipografía y Ergonomía */
  --font-display: 'Space Grotesk', system-ui, -apple-system, sans-serif;
  --font-telemetry: 'JetBrains Mono', 'Fira Code', monospace;
  --min-touch-target: 48px;
}

/* Selector para Linterna Roja */
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

### 6.2. Escala Tipográfica y Ergonomía Táctil
- **Titulares Tácticos**: 20–24 px (Space Grotesk, mayúsculas con espaciado expandido `letter-spacing: 0.05em`).
- **Cuerpo de Lectura**: 16–18 px con altura de línea `line-height: 1.6`.
- **Telemetría y Coordenadas**: 13–15 px (Monospace).
- **Límite Mínimo Absoluto**: Ningún texto en pantalla por debajo de 12 px.
- **Área Táctil**: Mínimo estricto de **48×48 px** en todo botón, píldora, celda de grilla o pestaña.

---

## 7. SCREEN INVENTORY & USER FLOWS (12 RUTAS)

| # | Ruta SPA | Nombre de Pantalla | Tipo de Shell | Descripción Funcional y Flujo |
|---|---|---|---|---|
| **01** | `/access` | **Classified Key Entry Terminal** | `mobile_blank` | Terminal monoespaciado de acceso por PIN numérico de 4 dígitos con bypass instantáneo para modo simulación/demo. |
| **02** | `/home` | **Home Discovery Stream** | `mobile_tab` | Tarjetas de docu-cortos en dos columnas, filtros de especialidad STEM, logo oficial 220×220 y alternador Day/Night Ops. |
| **03** | `/map` | **Mission Map & 5x5 Mission Grid** | `mobile_tab` | Matriz de 25 celdas TIMSS Grado 8 dividida por especialidad (filas) y disciplina STEM+A (columnas). Selector de temporadas. |
| **04** | `/episode/:id/challenge` | **Video Challenge HUD & Elena Intercom** | `mobile_stack` | Reproductor que al completarse despliega HUD con el reactivo TIMSS. Botón de intercomunicador pedagógico con la Jefa Elena ante error. |
| **05** | `/episode/:id/feedback` | **Answer Feedback & Circuit Resolution** | `mobile_stack` | Rationale explicativo del concepto físico/químico y barrido radar de nominalidad para cerrar el circuito. |
| **06** | `/reward/:missionId` | **Copper Reward & Credential Transition** | `mobile_stack` | Moneda metálica de alto relieve en perspectiva 3D, animación de racha (+100 PTS) y chip de firma de integridad local. |
| **07** | `/badges` | **Badge Registry & Stepped Coin Rack** | `mobile_tab` | Estante escalonado de exhibición para monedas (Acero, Cobre, Bronce) y plano modular de ensamblaje de las 4 secciones del submarino. |
| **08** | `/badges/share` | **Share Card Vertical (9:16)** | `mobile_stack` | Generador en cliente HTML5 Canvas que exporta `ISA_MiColeccion_YYYY-MM.png` adaptada a Instagram Stories y WhatsApp. |
| **09** | `/profile` | **Visitor Profile (Explorer Profile)** | `mobile_tab` | Bitácora del visitante, identificador táctico seudónimo, gráfico de radar de competencias STEM y telemetría de visitas. |
| **10** | `/profile/callsign` | **Callsign Selection Terminal** | `mobile_tab` | Generador y selector de seudónimos navales con filtro anti-PII (elimina nombres reales, correos y números telefónicos). |
| **11** | `/sync` | **Operational Sync Bridge** | `mobile_tab` | Indicador de **MODO LOCAL SEGURO**, cola de cambios diferidos (Local-Wins) y botón de descarga de backup JSON (`isa-backup-progress.json`). |
| **12** | `/privacy` | **Privacy Transparency & Sovereign Consent** | `mobile_stack` | Los 4 Pilares de Privacidad Soberana, inspector de memoria en vivo en bytes y botón de purga segura con modal destructivo de dos pasos. |

---

## 8. INVIOLABLE RULES (REGLAS INQUEBRANTABLES)

1. **Terminología Estricta (Zero "Cadet")**:
   - Queda totalmente prohibido el uso de «Cadete» o «Cadet» en textos de interfaz, código, comentarios o documentación.
   - El estudiante es siempre **«Visitante» (Visitor)** o **«Explorador» (Explorer)**.
2. **Avisos Legales Mandatorios (Presentes en Toda Pantalla)**:
   - *«RECONOCIMIENTO SIMBÓLICO — NO ES UNA CERTIFICACIÓN ACADÉMICA / SYMBOLIC RECOGNITION — NOT AN ACADEMIC CERTIFICATION»*
   - *«Privacy by design. Minimal pseudonymous data. No email stored in plaintext. Local-first credential record. No account required.»*
   - *«Todo lo que ves es ficción. Los museos y su contexto histórico son reales.»*
3. **Telemetría de Red Desmitificada**:
   - El estado de red debe enunciarse exclusivamente como **«MODO LOCAL SEGURO»** o **«SIN CONEXIÓN ACTIVA»**.
   - Prohibido utilizar jerga de ingeniería de red (DNS, Air-Gapped, Off-Grid mesh) de cara al usuario.
4. **Ergonomía Táctil y Accesibilidad**:
   - Touch targets $\ge 48\times 48\text{ px}$. Contraste WCAG AA $\ge 7:1$ en modo Día y modo Noche.
5. **Cero PII**:
   - Ningún formulario, campo de texto o parámetro URL podrá solicitar datos privados del visitante.

---

## 9. UX & NARRATIVE DECISIONS

- **Mentora Jefa de Máquinas ELENA**: Personaje de guía pedagógica. Diseñada con la premisa: *«Hoy es imagen estática de intercomunicador con filtro CRT; mañana será video documental»*. Se activa cuando el visitante necesita una pista formativa ante una respuesta incorrecta.
- **Conmutador Bilingüe Instantáneo**: Principio *«English for the world. Spanish for the experience»*. Se ejecuta de forma síncrona mediante atributos `data-i18n` sin reiniciar el estado de la página ni perder la posición de scroll.
- **Linterna Roja de Batalla Submarina (Night Ops)**: No es un modo oscuro genérico; es una emulación rigurosa de las luces de emergencia y preservación visual utilizadas en inmersión nocturna en submarinos reales.
- **Estante Escalonado (Stepped Coin Rack) & Share Card 9:16**: La recompensa se concibe como un objeto físico tangible de valor patrimonial. La exportación vertical en 9:16 facilita el orgullo de compartir el conocimiento STEM sin violar la privacidad del menor.

---

## 10. PRODUCT ROADMAP

- **v1.0 (Versión Actual)**:
  - MVP funcional completo en cliente soberano.
  - 12 pantallas responsive interconectadas.
  - Grilla 5×5 y banco curricular TIMSS G8 para la temporada Cobre y Acero.
  - Exportación de Share Card (9:16) y backup local JSON.
- **v1.1 (Próximo Hito)**:
  - Video interactivo para las transmisiones pedagógicas de Elena.
  - Implementación de interfaz de carga editorial con AppSheet vinculada al Sheet `ISA_Base.xlsx`.
  - Recorrido inmersivo 360° optimizado para el Submarino BAP Abtao y U-995.
- **v1.2**:
  - Mecanismo de sincronización voluntaria peer-to-peer o push cifrado sin servidor de cuentas.
  - Integración del estándar **Open Badges 3.0 / W3C Verifiable Credentials** en el archivo JSON exportable.
- **v2.0**:
  - Escalabilidad del directorio global a los 160 museos con fichas interactivas en 3D (WebGL / Three.js).
  - Telemetría de impacto educativo anonimizada agregada con privacidad diferencial k-anonimato.

---

## 11. FINAL QA CHECKLIST (15 CRITICAL POINTS)

1. [ ] **Zero PII Harvesting**: No existen campos de email, nombre real, teléfono ni password en ninguna vista.
2. [ ] **Persistencia Soberana en Cliente**: Todo el progreso se almacena y recupera de `isa-progress-v1`.
3. [ ] **Descarga de Backup JSON**: El botón en Sync Bridge descarga limpiamente `isa-backup-progress.json`.
4. [ ] **Purga Destructiva Segura**: El modal en dos pasos reinicia el almacenamiento y el inspector a 0 bytes.
5. [ ] **Erradicación de "Cadete"**: Ningún texto en pantalla o metadato contiene la palabra "Cadete" o "Cadet".
6. [ ] **Etiquetado de Red Claro**: El enlace muestra **"MODO LOCAL SEGURO"** o **"SIN CONEXIÓN ACTIVA"**.
7. [ ] **Avisos Legales en 12 Pantallas**: Los tres disclaimers mandatorios se encuentran visibles.
8. [ ] **Touch Targets $\ge 48\text{px}$**: Todos los botones y celdas cumplen con el área de contacto táctil mínima.
9. [ ] **Escala Tipográfica Respetada**: Cuerpo 16–18 px; telemetría 13–15 px; ningún texto bajo 12 px.
10. [ ] **Conmutación Instantánea Day/Night Ops**: Alternancia entre `#38e8a6` y `#FF3B30` sin saltos de layout.
11. [ ] **Alternancia Bilingüe Síncrona**: Cambio ES / EN en caliente preservando la posición y el estado.
12. [ ] **Share Card 9:16 Generada**: Exportación con nombre `ISA_MiColeccion_YYYY-MM.png` con alto contraste.
13. [ ] **HUD de Desafío tras Video**: La pregunta se despliega de inmediato al concluir el reproductor.
14. [ ] **Intercomunicador Elena en Falla**: El modal de apoyo pedagógico se activa coherentemente al fallar.
15. [ ] **Resolución Nominal de Circuito**: El flujo de feedback transiciona armónicamente hacia la medalla.

---

## 12. GLOSSARY (VOCABULARIO OFICIAL ISA)

- **Visitante / Explorador (Visitor / Explorer)**: Usuario de la academia. Denominación única autorizada (reemplaza a "Cadete").
- **Moneda de Temporada (Season Coin)**: Distintivo metálico de alta graduación otorgado al dominar una temporada curricular (Acero, Cobre, Bronce, Plata, Oro).
- **Cinta de Especialidad (Specialty Ribbon)**: Distintivo de tela con pasador que conmemora la resolución de una celda específica STEM o Factor Humano.
- **Celda Matricial (Matrix Cell)**: Cada uno de los 25 nodos de la grilla TIMSS correspondientes al cruce de un Rol y una Disciplina (ej. `CU-SCI-MAQ`).
- **Modo Local Seguro (Secure Local Mode)**: Estado operativo predeterminado del motor donde la aplicación trabaja desconectada de servidores externos con garantía de privacidad local.
- **Linterna Roja de Batalla (Night Ops)**: Modalidad lumínica en rojo táctico (#FF3B30) que replica el entorno de mamparo submarino nocturno.
- **Firma de Integridad Local (Local Integrity Signature)**: Sello criptográfico generado en el dispositivo para validar la no alteración del registro de progreso en cliente.

---

## 13. DECISION LOG (HISTORIAL DE DECISIONES DE DISEÑO)

- **2025-02-10**: Decisión de desacoplar el backend y optar por un modelo soberano Local-First para cumplir con normativas de protección de menores y privacidad educativa.
- **2025-02-12**: Integración curricular estricta con los ítems liberados de TIMSS 2011 Grado 8 Ciencias y Matemáticas para asegurar valor pedagógico real.
- **2025-02-14**: Adopción de la paleta dual: Verde Radar Diurno `#38e8a6` y Linterna Roja Submarina `#FF3B30`.
- **2025-02-18**: Erradicación formal y definitiva de la terminología de rango militar («Cadete») a favor de «Visitante» y «Explorador».
- **2025-02-20**: Incorporación de la Jefa de Máquinas Elena como mentora documental y definición de la Share Card vertical 9:16 para redes sociales.
- **2025-02-24**: Publicación del modelo de datos de 18 tablas en Google Sheets y unificación de la especificación técnica en el Master Brief v1.0.
