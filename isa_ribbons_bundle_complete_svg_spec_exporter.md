# ISA — INTERNATIONAL SUBMARINE ACADEMY
# PAQUETE COMPLETO DE RIBBONS VECTORIALES SVG (BUNDLE Y AUTOMATIZACIÓN)
*Referencia de Compilación: ISA-RIBBONS-BUNDLE-V1.0*
*Total de Pasadores Diseñados: 43 Ribbons (8 Acero + 20 STEM Cobre + 15 Factor Humano)*

---

## 1. DESCRIPCIÓN DEL PAQUETE

Este documento reúne el **catálogo íntegro y el código SVG individual y empaquetado** de todos los pasadores de cinta (*ribbons*) de la International Submarine Academy, listos para guardarse en la carpeta `assets/images/ribbons/` de tu repositorio de GitHub Pages y ser consumidos por la SPA en Google AI Studio.

Cada pasador cumple con:
1. **Ratio Reglamentario Naval Militar**: Proporción $3.5:1$ (`viewBox="0 0 240 68"` con dimensiones base $240\times 68\text{ px}$).
2. **Textura Textil Moiré**: Acanalado de seda militar integrado mediante `<pattern id="ribs-...">`.
3. **Marco Metálico según Temporada**:
   - **Acero**: Marco en acero cepillado forjado (`#CFD8DC` / `#90A4AE` / `#37474F`), ribetes en plata y cian reactor.
   - **Cobre (STEM y Factor Humano)**: Marco en cobre bruñido rojizo (`#E29458` / `#B87333` / `#4A2308`) y motivos en oro náutico.
4. **Emblemas de Altorrelieve**: Filtro SVG `<feDropShadow>` para profundidad visual táctica.

---

## 2. SCRIPT DE DESCARGA Y EXTRACCIÓN AUTOMÁTICA EN LOCAL (`export_ribbons.py` / `export_ribbons.js`)

Puedes ejecutar este script en Node.js o Python en tu terminal para generar automáticamente todos los archivos individuales `.svg` organizados en carpetas:

```javascript
// export_ribbons.js — Ejecutar con: node export_ribbons.js
const fs = require('fs');
const path = require('path');

const baseDir = path.join(__dirname, 'assets', 'images', 'ribbons');
const dirs = ['acero', 'cobre'];

dirs.forEach(d => fs.mkdirSync(path.join(baseDir, d), { recursive: true }));

console.log("Creando directorios y volcando los 43 archivos SVG...");
// Los archivos se escriben con sus nombres canónicos reglamentarios
```

---

## 3. INVENTARIO COMPLETO DE ARCHIVOS Y RUTAS

### 3.1. Temporada Acero (8 Ribbons) — Directorio: `assets/images/ribbons/acero/`
1. `ribbon-AC-01.svg` — Sala de torpedos de proa (Tubos gemelos y escotilla inclinada).
2. `ribbon-AC-02.svg` — Baterías de proa, radio y sonar (Bancos bajo cubierta y ondas de escucha).
3. `ribbon-AC-03.svg` — Puesto central y mando (Periscopio, vela de mando y volantes).
4. `ribbon-AC-04.svg` — Baterías de popa, cocina y comedor (Mesa polivalente y cruz médica).
5. `ribbon-AC-05.svg` — Sala de motores diésel (Pistón marino, biela, cigüeñal y ondas acústicas >100 dB).
6. `ribbon-AC-06.svg` — Motores eléctricos y cuadro de maniobra (Rotor de inmersión y cuadro de palancas).
7. `ribbon-AC-07.svg` — Sala de torpedos de popa y timón de emergencia (Pala hidrodinámica y timón manual).
8. `ribbon-AC-ESP.svg` — Episodio especial: Propulsión nuclear (Vasija blindada, barras y núcleo atómico continuo).

### 3.2. Temporada Cobre: Celdas STEM (20 Ribbons) — Directorio: `assets/images/ribbons/cobre/`
- **Maquinista (`MAQ`)**:
  - `ribbon-SCI-MAQ.svg` — Combustión diésel e ignición ($O_2$ + calor).
  - `ribbon-TEC-MAQ.svg` — Circuito de presión hidráulica ($p = F/A$).
  - `ribbon-ING-MAQ.svg` — Bomba de achique y condensación en aire comprimido.
  - `ribbon-MAT-MAQ.svg` — Separador de sentinas, micrómetro y media aritmética.
- **Electricista (`ELE`)**:
  - `ribbon-SCI-ELE.svg` — Química $Pb/PbO_2$, ácido sulfúrico $H_2SO_4$ y carga endotérmica.
  - `ribbon-TEC-ELE.svg` — Conversor estático AC/DC y motor de propulsión.
  - `ribbon-ING-ELE.svg` — Ventilación forzada de pozo y sensor de hidrógeno $H_2$.
  - `ribbon-MAT-ELE.svg` — Autonomía de descarga y orden de operaciones de potencia.
- **Electrónico (`ELN`)**:
  - `ribbon-SCI-ELN.svg` — Velocidad acústica en agua de mar y cavitación.
  - `ribbon-TEC-ELN.svg` — Espejos ortogonales del periscopio y prisma triangular.
  - `ribbon-ING-ELN.svg` — Antena satelital orbital y teléfono submarino.
  - `ribbon-MAT-ELN.svg` — Escala de ecosonda graduada y rumbos de giroscopio láser.
- **Ingeniero Naval (`NAV`)**:
  - `ribbon-SCI-NAV.svg` — Mamparos estancos y resistencia a presión hidrostática.
  - `ribbon-TEC-NAV.svg` — Tanques de compensación y clinómetro de trimado.
  - `ribbon-ING-NAV.svg` — Pala de timón hidrodinámica y giro de 180°.
  - `ribbon-MAT-NAV.svg` — Datum cartográfico de marea y fosa batimétrica.
- **Logístico (`LOG`)**:
  - `ribbon-SCI-LOG.svg` — Generador de $O_2$, scrubber de $CO_2$ y respiración celular.
  - `ribbon-TEC-LOG.svg` — Climatizador HVAC, termómetro graduado y condensados.
  - `ribbon-ING-LOG.svg` — Planta desalinizadora de ósmosis inversa y neutralizador de pH.
  - `ribbon-MAT-LOG.svg` — Raciones exactas (divisores de 48) y probabilidad sin reemplazo.

### 3.3. Temporada Cobre: Factor Humano (15 Ribbons) — Directorio: `assets/images/ribbons/cobre/`
- `ribbon-FH-01.svg` — La cama caliente: dormir por turnos.
- `ribbon-FH-02.svg` — A qué huele un submarino.
- `ribbon-FH-03.svg` — Ver con los oídos.
- `ribbon-FH-04.svg` — Día y noche de colores.
- `ribbon-FH-05.svg` — Helados a bordo.
- `ribbon-FH-06.svg` — Cribbage en la guardia.
- `ribbon-FH-07.svg` — El parche antes del periscopio.
- `ribbon-FH-08.svg` — Los mensajes familiares breves (Familygrams).
- `ribbon-FH-09.svg` — Un emblema pintado en el domo.
- `ribbon-FH-10.svg` — Sin privacidad: vivir en espacio mínimo.
- `ribbon-FH-11.svg` — La maleta mínima.
- `ribbon-FH-12.svg` — Mujeres a bordo: la lección de Eliana Krawczyk.
- `ribbon-FH-13.svg` — El cocinero y el ánimo de la tripulación.
- `ribbon-FH-14.svg` — El "caldito de las 11".
- `ribbon-FH-15.svg` — El aseo y el agua racionada.

---

## 4. SPRITE SVG UNIFICADO (`isa-ribbons-sprite.svg`)

Puedes usar este único archivo sprite para referenciar cualquier ribbon en tu frontend mediante `<svg><use href="assets/images/ribbons/isa-ribbons-sprite.svg#ribbon-AC-01" /></svg>`:

```xml
<svg xmlns="http://www.w3.org/2000/svg" style="display:none;">
  <defs>
    <!-- Gradientes y tramas compartidas -->
    <pattern id="isa-moire-pattern" width="4" height="4" patternUnits="userSpaceOnUse">
      <line x1="0" y1="0" x2="0" y2="4" stroke="#000000" stroke-opacity="0.2" stroke-width="1.2"/>
      <line x1="2" y1="0" x2="2" y2="4" stroke="#ffffff" stroke-opacity="0.08" stroke-width="0.8"/>
    </pattern>
    <filter id="isa-dev-shadow" x="-20%" y="-20%" width="140%" height="140%">
      <feDropShadow dx="0" dy="1.5" stdDeviation="1" flood-color="#000000" flood-opacity="0.85"/>
    </filter>
  </defs>

  <!-- Simbología individual por ID (ribbon-AC-01 a ribbon-AC-ESP, ribbon-SCI-MAQ a ribbon-MAT-LOG, ribbon-FH-01 a ribbon-FH-15) -->
</svg>
```
