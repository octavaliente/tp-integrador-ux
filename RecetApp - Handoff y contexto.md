# RecetApp — Handoff de contexto para migración de chat

> Documento de traspaso. Pegá/subí esto al iniciar el nuevo chat en la otra PC para retomar con todo el contexto del Trabajo Práctico Integrador de UX.

---

## 1. Contexto

- **Materia:** UI / UX (UTN — docentes Mailén Brandao y Florencia Abadi). Trabajo Práctico Final Integrador.
- **Proyecto:** Diseñar la **experiencia e interfaz mobile de "RecetApp"**, una app para planificar comidas, organizar recetas y generar listas de compras de forma simple, útil y accesible. Integra UX + UI + Accesibilidad **WCAG nivel AA**.
- **Usuario:** Octavio Valiente. Email Cowork: `ovaliente@daten.ar`. Email/cuenta de Figma: `ovaliente@frba.utn.edu.ar` (team tier *Starter*).
- **Fecha objetivo de presentación:** **2 de julio** (las fechas disponibles eran 25/6 y 2/7; no hay recuperatorio; 20 min por grupo).
- **Forma de trabajo acordada:** trabajar en paralelo Claude + Figma + decisiones nuestras; **definir/validar cada cosa en el chat antes de construir en Figma**, e iterar.

### Entregables obligatorios (de la consigna)
1. **Diseño completo** de todas las pantallas mobile con criterios WCAG AA.
2. **Archivo de Figma** organizado: pantallas, componentes, variables, estilos y UI Kit completo (UI Kit en página propia).
3. **Documento de fundamentación**: UX Research (entrevistas, mapa de empatía, user personas), Sistema Visual (tipografías, paleta, coherencia), UX (leyes UX, patrones, evaluación heurística), Accesibilidad (decisiones + evidencias WCAG AA).
4. **Presentación oral** (≤20 min, todos participan), estructura de 5 bloques: 1) Pitch, 2) Investigación (3 user personas + POV), 3) Sistema Visual, 4) Patrones de diseño, 5) Evaluación heurística.

### Entregables opcionales (decisión: NO por ahora)
Prototipo navegable, Atomic Design, Microinteracciones. Se evaluará al final si sobra tiempo/cupo.

---

## 2. Decisiones tomadas (validadas con el usuario)

- **Nombre de la app:** RecetApp.
- **Paleta de colores:** **"Calabaza & canela"** (cálida, otoñal, acogedora; estimula apetito sin caer en el rojo de fast-food).
- **Tipografía:** **Poppins** (títulos/display) + **Inter** (cuerpo/UI). Ambas en Google Fonts (cargadas en Figma).
- **Grilla:** frame base **iPhone 15 = 393 × 852 pt**, **4 columnas**, margen y gutter **16**. (Antes se había usado 375×812 por error; corregido a iPhone 15 por pedido de la profesora.)
- **Espaciado:** escala **estricta de 8 puntos** → 8 / 16 / 24 / 32 / 40 / 48 / 64. El 4 queda solo como medio-paso excepcional.
- **Radios:** sm 8 (inputs/chips), md 12 (botones), lg 16 (cards), pill/full (tags/FAB).
- **Área táctil mínima:** 44 × 44 px.
- **Chip seleccionado:** estilo suave (fondo crema + borde, no sólido). **FAB** incluido en el sistema. **Radio de botón = 12**.

---

## 3. Memoria — hechos clave a no olvidar

- **UX Research YA ESTÁ HECHA** en una etapa previa de la materia (3 user personas, mapa de empatía, POV). El **sitemap** sale de esa investigación. Se retoma solo para el documento de fundamentación y la presentación — **no es una fase a rehacer**.
- **Contraste AA verificado programáticamente.** Reglas duras del sistema de color:
  - **Botón primario = calabaza 600 (`#AF5012`)**, NO el 500. El 500 (`#C75A12`) da 4.29:1 con blanco (< 4.5, no pasa AA texto normal).
  - **Dorado = solo acento/realce, siempre con texto oscuro encima** (todas sus variantes fallan con blanco).
  - **Warning ajustado a `#8A5708`** (el `#B5710A` original daba 3.94 con blanco).
- **Lineamientos de la materia (qué fija y qué deja abierto):**
  - Clase 9 (pp. 63–82): sistema de grillas. Mobile = **1/2/4/8 columnas**; regla del **espaciado 8pt**. (Elegimos 4 col.)
  - Clase 4 (Accesibilidad): contraste **4.5:1 AA** texto normal; área táctil mín. 24×24 (AA), **ideal 44×44**; usar **STARK** para chequear.
  - Clase 10 (Design System): regla **60-30-10**, **Atomic Design**, familias tipográficas, color. Apunta a **Material Design + iOS HIG** como marcos de referencia.
  - **Radios y escala tipográfica NO están fijados por los apuntes** → son decisión de diseño (a justificar).
- **Adjuntos del usuario a veces no se materializan** en el disco del sandbox; si falta un archivo subido, pedir que lo pegue como texto.

---

## 4. Reglas (entorno y trabajo)

- **Figma MCP en plan Starter = límite de llamadas (rate limit).** Hay que **agrupar el trabajo al máximo por llamada** y **minimizar verificaciones**. Si aparece el error de límite, el script es **atómico** (no se ejecutó nada) → esperar a que el cupo se reinicie y reintentar.
- **`figma-use` skill obligatoria antes de cada `use_figma`.** Reglas clave que ya aplicamos:
  - Usar `return` para devolver datos; NO `figma.closePlugin()` ni IIFE async.
  - Colores en rango **0–1** (no 0–255).
  - **Setear `scopes` explícitos** al crear variables (no dejar `ALL_SCOPES`).
  - **Cargar fuentes** (`loadFontAsync`) antes de tocar texto.
  - Cambiar de página con `await figma.setCurrentPageAsync(page)` (el setter sync no funciona), 1 sola vez por llamada.
  - Trabajar **incremental**, devolver IDs creados, validar con screenshot/metadata.
  - **`hiddenFromPublishing` falla en Starter** → no usarlo.
- **Seguridad:** no tocar planes/pagos del usuario; pedir confirmación para acciones irreversibles; no entrar credenciales.

---

## 5. Archivos existentes (carpeta del proyecto)

Ruta: `D:\...\TP Integrador UX\`

- `Consigna TP Final.pdf` — consigna completa.
- `Clase 9 - Patrones UX y UI.pdf` — grillas (pp. 63–82), patrones.
- `Clase 4 - Accesibilidad.pdf` — WCAG AA, contraste, táctil, STARK.
- `Clase 10 - DesignSystem.pdf` — design system, 60-30-10, atomic, tipografía, color.
- `Sitemap - App recetas.jpg` — arquitectura de información (ver §7).
- `CLAUDE.md` — instrucciones del proyecto (apunta a `.claude/skills` para Figma MCP).
- `.claude/skills/` — `figma-use`, `skill-index`, `create-design-system-rules` (esta última se descartó por irrelevante).
- `recetapp_tokens.json` — export de todos los tokens de color (primitivos + semánticos) generado por Claude.
- `RecetApp - Handoff y contexto.md` — este documento.

---

## 6. Sistema de diseño — valores (para portabilidad)

### Paleta (hex)
- **Calabaza (primario):** 50 `#FBF2EC` · 100 `#F5E1D4` · 200 `#EAC0A5` · 300 `#DD9C71` · 400 `#D1783D` · 500 `#C75A12` · 600 `#AF5012` · 700 `#934612` · 800 `#773B12` · 900 `#5C3012`
- **Canela (secundario):** 50 `#F4F1ED` · 100 `#E7DED8` · 200 `#CCBAAC` · 300 `#AF927C` · 400 `#926B4B` · 500 `#7A4A24` · 600 `#6E4321` · 700 `#603B1E` · 800 `#52331B` · 900 `#452B17`
- **Dorado (acento, solo texto oscuro):** 50 `#FDF9F2` · 100 `#FBF2E2` · 200 `#F6E4C1` · 300 `#F1D49D` · 400 `#ECC579` · 500 `#E8B85C` · 600 `#CA9F50` · 700 `#A98443` · 800 `#876836` · 900 `#664C28`
- **Neutral cálido:** 50 `#F3F2F1` · 100 `#E4E1DF` · 200 `#C7C1BC` · 300 `#A69D95` · 400 `#86796E` · 500 `#6B5B4E` · 600 `#615144` · 700 `#56463A` · 800 `#4B3B2F` · 900 `#403024`
- **Base:** blanco `#FFFFFF` · crema (bg página) `#FDF4E8` · texto `#2E1E12` · texto-2 `#5C4A3A`
- **Estados (texto blanco encima, AA):** success `#2F7D33` · error `#C0392B` · warning `#8A5708` · info `#2B6C9E`

### Tokens semánticos (alias)
- `bg/page` → crema · `bg/surface` → blanco · `bg/subtle` → calabaza/50
- `text/primary` → `#2E1E12` · `text/secondary` → `#5C4A3A` · `text/disabled` → neutral/300
- `border/default` → neutral/200 · `border/strong` → neutral/300
- `action/default` → calabaza/600 · `action/hover` → calabaza/700 · `action/pressed` → calabaza/800 · `action/on` → blanco · `link` → calabaza/700
- `accent/fill` → dorado/500 · `accent/on` → texto oscuro
- `feedback/success|error|warning|info` → estados

### Tipografía (escala / estilos de texto en Figma)
- `Texto/Display` — Poppins SemiBold 32 / 120%
- `Texto/H1` — Poppins SemiBold 26 / 125%
- `Texto/H2` — Poppins SemiBold 21 / 130%
- `Texto/H3` — Poppins Medium 17 / 135%
- `Texto/Body L` — Inter Regular 16 / 160%
- `Texto/Body M` — Inter Regular 14 / 160%
- `Texto/Label` — Inter Medium 13 / 140%
- `Texto/Caption` — Inter Regular 12 / 140%

### Medidas
- Espaciado `space/4..64` (8pt) · Radios `radius/sm|md|lg|pill` (8/12/16/999) · `grid/margin` 16 · `grid/gutter` 16 · `grid/columnas` 4.

---

## 7. Arquitectura de información (del sitemap)

- **Home** — sugerencias de recetas según mis ingredientes.
- **Perfil** — tipo de actividad deportiva, restricciones familiares, cantidad de personas en casa, objetivo nutricional, restricciones personales, peso y altura.
- **Planificación** — lista de compras, sugerencias de recetas, planificación semanal.
- **Recetas** — recetas guardadas; detalle de receta (pasos de preparación, ajustar porciones, info nutricional por receta/ingrediente, reemplazar ingrediente, foto del plato, dificultad y tiempo, precio estimado); historial cocinado; guardar receta; añadir receta a planificación; buscar recetas (por ingredientes / por filtros).
- **Ingredientes** — ingresar ingredientes (foto del ticket, código de barras, manual, por voz); ver ingredientes.
- **Notificaciones.**

---

## 8. Herramientas (disponibles y usadas)

- **Figma MCP** (server `3e116291-1201-4ddc-9439-3e2168a6e999`). Usadas: `whoami`, `get_metadata`, `use_figma` (escritura vía Plugin API: variables, estilos, componentes, frames, grids). Disponibles además: `get_design_context`, `search_design_system`, `get_libraries`, `create_new_file`, `generate_diagram`, `get_variable_defs`, tools de Code Connect, `download_assets`.
- **show_widget** — para visualizar paletas, tipografías y componentes en el chat (validación previa).
- **bash (sandbox Linux)** — `pdftotext`/`pdftoppm` para leer PDFs de la materia; `npm @tabler/icons` para traer SVGs de íconos; cálculo de contraste WCAG en Python.
- **Read, AskUserQuestion, TaskCreate/TaskUpdate.**

### Datos de Figma
- **fileKey:** `xm1jJVWebfvCmj0Yeb7rC3` (archivo "TP-Integrador").
- **planKey (team):** `team::1361136318383520599`.
- **Páginas:** Portada `0:1` · Foundations `15:2` · UI Kit `15:3` · Pantallas `15:4`.
- **Nodos clave:** Button set `16:26` · Input set `17:23` · Chip set `20:12` · Card de receta `22:2` · Iconografía frame `21:2` · Foundations container `24:2` · Plantilla iPhone 15 `23:2`.

---

## 9. Skills

- **De salida/documento:** `docx`, `pdf`, `pptx`, `xlsx` (para fundamentación y deck más adelante). Otras: `schedule`, `skill-creator`, `setup-cowork`.
- **Figma (vía MCP / `.claude/skills`):** `figma-use` (HOW del Plugin API — leída y aplicada). Referenciadas en `skill-index` pero solo accesibles como recursos MCP: `figma-generate-library` (WHAT/orden para design systems), `figma-create-new-file`, `figma-generate-design`, `figma-code-connect`, `figma-use-figjam`, `figma-use-slides`.

---

## 10. Roadmap

- **Fase 0 — Previos:** nombre ✓, paleta ✓, tipografía ✓.
- **Fase 2 — UX Research:** ✓ ya hecha en la materia (insumo para fundamentación/presentación).
- **Fase 3 — Sistema visual + UI Kit en Figma:** ✅ **COMPLETA** (ver §11).
- **Fase 4 — Diseño de pantallas con Claude:** generar las vistas del sitemap aplicando leyes UX y patrones, con justificación → salida iterable (PDF). ← **PRÓXIMO PASO**
- **Fase 5 — Rehacer/pasar a Figma:** maquetar las pantallas finales en Figma usando el design system + plantilla iPhone 15; organizar páginas/capas; chequear AA con STARK.
- **Fase 6 — Evaluación heurística:** Nielsen, hallazgos y ajustes.
- **Fase 7 — Documento de fundamentación:** consolidar research + sistema visual + patrones + heurística + evidencias WCAG.
- **Fase 8 — Presentación final:** deck de 5 bloques, ensayo ≤20 min, reparto, control de tiempo, inscripción (2/7).

---

## 11. Estado actual

**Fase 3 terminada en Figma.** El archivo TP-Integrador contiene:

- **Variables:** `Color/Primitivos` (48, con scopes correctos) · `Color/Semanticos` (19, alias) · `Medidas` (16: espaciado 8pt, radios, grilla).
- **Estilos de texto:** `Texto/*` (8).
- **UI Kit (página propia, con títulos de sección):**
  - `Button` — 12 variantes (Tipo: Primario/Secundario/Fantasma × Estado: Default/Hover/Pressed/Disabled).
  - `Input` — 5 estados (Default, Foco, Con valor, Error, Disabled).
  - `Chip` — 5 variantes (Filtro, Filtro seleccionado, Categoría, Restricción, Metadato).
  - `Card de receta` — imagen + botón guardar, título, metadatos con íconos, tags (instancias).
  - `icon/*` — 20 íconos de Tabler (trazo atado a `text/primary`).
- **Foundations (página):** showcase visual de color, tipografía (estilos aplicados), espaciado 8pt y radios.
- **Pantallas (página):** **Plantilla base iPhone 15 (393×852)** con grilla de 4 columnas, grid de 8pt y zonas guía (header, contenido, tab bar).

**Próximo paso:** arrancar **Fase 4 — diseño de pantallas** (Home, Recetas, Detalle de receta, Planificación, Perfil, Ingredientes, Notificaciones) aplicando leyes UX y patrones, iterando primero como propuestas y luego maquetando en Figma sobre la plantilla y el UI Kit.

---

## 12. Cómo retomar en el nuevo chat

1. Subir esta carpeta del proyecto (con sus PDFs, sitemap, `CLAUDE.md`, `.claude/skills/` y `recetapp_tokens.json`).
2. Confirmar conexión del **Figma MCP** y que el fileKey `xm1jJVWebfvCmj0Yeb7rC3` sigue accesible.
3. Tener presente el **rate limit del plan Starter** (agrupar llamadas).
4. Cargar la skill **`figma-use`** antes de escribir en Figma.
5. Continuar por **Fase 4** (o revisar/ajustar el UI Kit si se desea antes).
