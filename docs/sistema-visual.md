# Sistema Visual — RecetApp (fundamentación)

> Fundamentación de las decisiones **visuales transversales** de la app: tipografía, color,
> espaciado/grilla, iconografía y sistema de componentes. A diferencia de las fichas por
> pantalla ([`justificaciones-ux.md`](justificaciones-ux.md)), estas decisiones se toman **una
> sola vez** y rigen en todas las vistas.
>
> Alimenta el **Documento de Fundamentación** (área *Sistema Visual*) y el **bloque 3 de la
> defensa oral**. Fuentes: **Clase 10** (Sistema de Diseño), **Clase 9** (grilla/medidas, sl. 64–83),
> **Clase 4** (accesibilidad WCAG 2.2 AA). Valores: [`../recetapp_tokens.json`](../recetapp_tokens.json).

---

## Cómo leer las etiquetas

Cada decisión cierra con una línea de **chips fuente**, trazables al material de cátedra:

- `Estilo` — concepto de **Clase 10** (Sistema de Diseño / Lenguaje Visual).
- `Ley` — Ley de UX (**Clase 9**, sl. 23–32).
- `Patrón` — Patrón de diseño (**Clase 9**, sl. 34–83).
- `Heurística` — Heurística de Nielsen (**Clase 11**, sl. 6–46).
- `A11y` — criterio WCAG 2.2 (**Clase 4**).
- `Regla` — regla transversal del proyecto ([`reglas-transversales.md`](reglas-transversales.md)).

> El mismo sistema de chips se usa en las fichas por pantalla.

---

## Coherencia con el público objetivo

RecetApp se dirige a tres arquetipos definidos en la investigación (sección *UX Research*, Clase 5):
**Martina (25)** —necesita saber *qué comprar y qué hacer con lo que ya tiene*; el miedo a gastar mal
la paraliza—, **Lucas (28)** —necesita *adaptar las recetas a su objetivo del día*, busca controlar
variables— y **Andrea (42)** —necesita *resolver "qué comemos hoy" en menos de 5 minutos*, vive en
fatiga de decisión—.

Más allá de sus metas distintas, los tres comparten un **contexto emocional**: deciden **bajo
presión, con poco tiempo y cierta ansiedad** (miedo a equivocarse, sobrecarga de opciones), en un
entorno **doméstico y cotidiano**. El sistema visual responde a ese contexto, no lo agrava:

- **Cálido y cercano** (paleta calabaza & canela, tipografía amable) para un uso hogareño, no
  corporativo ni clínico; estimula el apetito **sin la urgencia agresiva del rojo** de fast-food.
- **Calmo y de baja carga cognitiva** (base neutra dominante, espaciado generoso, diseño
  minimalista) — clave para la **fatiga de decisión de Andrea** y la **parálisis de Martina**
  (*"la abundancia de opciones es parte del problema"*).
- **Claro y jerárquico** (escala tipográfica fuerte + un único acento que guía la acción) para que
  cada pantalla comunique rápido qué hacer.

→ `Estilo` Regla KISS / "Menos es más" · *Horror Vacui* · *Carga cognitiva* baja (Clase 10) · `Ley` Hick (menos opciones, decisión más rápida — Clase 9 sl. 23).

---

## 1. Tipografía

**Poppins (títulos) + Inter (cuerpo), ambas Sans Serif.**
Las **Sans Serif** son las indicadas para pantalla: la Clase 10 las describe como *"perfectas para
títulos… especialmente indicadas para visualizaciones en pantallas, quedando legibles en tamaños
pequeños y limpias en los grandes"*, y como transmisoras de **modernidad, simpleza y alegría** —
coherente con una app cotidiana y amable (Poppins figura literalmente entre los ejemplos del deck).
**Poppins** (geométrica, redondeada, cálida) da carácter a los títulos; **Inter** está optimizada
para UI y sostiene la lectura del cuerpo. Se descartan Serif (remates que *"pueden dar problemas a
personas con dislexia"*, Clase 4) y Decorativas (baja legibilidad).
→ `Estilo` Familia Sans Serif legible en pantalla (Clase 10) · `A11y` sans serif recomendada (Clase 4 sl. 21).

**Jerarquía por escala tipográfica.**
La importancia se comunica por **tamaño**: la Clase 10 enseña que *"la escala crea jerarquía de
forma instantánea"* y nombra las **Jerarquías** como *"la organización visual de los textos según su
importancia"*. La escala de 8 estilos cubre de **Display 32** a **Caption 12**, con pesos crecientes
(Inter Regular para cuerpo → Poppins SemiBold para títulos).

| Estilo | Fuente | Tamaño / Interlineado | Uso |
|---|---|---|---|
| `Texto/Display` | Poppins SemiBold | 32 / 120% | Números/realces grandes |
| `Texto/H1` | Poppins SemiBold | 26 / 125% | Título de pestaña raíz (R11) |
| `Texto/H2` | Poppins SemiBold | 21 / 130% | Secciones |
| `Texto/H3` | Poppins Medium | 17 / 135% | Título de subpantalla (R1), filas |
| `Texto/Body L` | Inter Regular | 16 / 160% | Cuerpo principal |
| `Texto/Body M` | Inter Regular | 14 / 160% | Cuerpo secundario, valores |
| `Texto/Label` | Inter Medium | 13 / 140% | Encabezados de sección, etiquetas |
| `Texto/Caption` | Inter Regular | 12 / 140% | Metadatos, leyendas |

→ `Estilo` Escala = jerarquía (Clase 10) · `Regla` estilos `Texto/*` atados como variables.

**Accesibilidad de la tipografía (Clase 4, sl. 21).**
El cuerpo de lectura (**Body L/M**) va a **160% de interlineado**, por encima del mínimo **1,5**; el
texto más chico es **Caption 12pt**, en el piso de los **12pt** recomendados; las alineaciones son a
izquierda (**nunca justificado**). *Limitación consciente:* los encabezados de sección usan
mayúsculas (`Texto/Label`), que la Clase 4 desaconseja para lectura larga — se acota a **rótulos
cortos**, nunca a párrafos, para preservar la legibilidad.
→ `A11y` interlineado ≥1,5 · ≥12pt · sin justificar (Clase 4 sl. 21) · WCAG 1.4.12 Espaciado del texto.

---

## 2. Color — paleta "Calabaza & canela"

**La identidad parte de la psicología del color (Clase 10).**
La paleta es cálida y otoñal. La Clase 10 asocia el **Naranja** a *"creatividad, aventura y
juventud… muy enérgico, con toque retro"* y el **Marrón** a *"sencillez, estabilidad y calidez… se
relaciona con la naturaleza"*. **Calabaza** (naranja terroso) aporta energía y apetito; **canela**
(marrón) aporta calidez hogareña y naturalidad. Se evitó deliberadamente el **Rojo** —que el deck
liga a *"peligro, pasión"* y que domina en fast-food— para no transmitir urgencia agresiva.
→ `Estilo` Psicología del color: Naranja/Marrón cálidos (Clase 10) · coherencia con público objetivo.

**Paleta primaria (colores de marca) + paleta secundaria (feedback).**
Siguiendo la distinción de la Clase 10: la **primaria** identifica la marca (calabaza, canela y el
dorado como realce — *"dos o tres" colores de identidad*), y la **secundaria** comunica **estados
del sistema** según los modelos mentales del usuario, con los cuatro roles que nombra el deck:

| Rol (Clase 10) | Token | Valor | Matiz esperado |
|---|---|---|---|
| Éxito | `feedback/success` | `#2F7D33` | verde |
| Error | `feedback/error` | `#C0392B` | rojo |
| Advertencia | `feedback/warning` | `#8A5708` | ámbar/naranja oscuro |
| Información | `feedback/info` | `#2B6C9E` | azul |

→ `Estilo` Paleta primaria (marca) + secundaria (feedback) (Clase 10).

**Distribución con la regla 60-30-10 — paleta definitiva de 6 roles.**
*Decisión a partir de feedback (proceso, clave para la rúbrica).* La primera versión del foundation
tenía una paleta **demasiado extensa**; la devolución de la cátedra fue que no se podían usar tantos
colores y sugirió aplicar la **regla 60-30-10** (Clase 10: *"una de las reglas más importantes en UI y
color"*). Resolución: las escalas completas (50–900) quedan como **fundamento de tokens**, pero la
interfaz se **consolidó en 6 roles semánticos** repartidos en 60-30-10 — un set acotado y coherente:

| Rol | Hex | Uso | 60/30/10 |
|---|---|---|---|
| **Fondo** | `#FDF4E8` | Fondo de todas las pantallas | **60 %** |
| **Texto primario** | `#2B1B12` | Títulos, nombres de receta, labels | 30 % |
| **Texto secundario** | `#6E4631` | Descripciones, tiempos, dificultad, subtítulos | 30 % |
| **Texto terciario / placeholder** | `#7D6657` | Placeholder "Buscar recetas", vacíos ("Ninguna") | 30 % |
| **Borde / divisor** | `#9C8674` | Bordes de cards/inputs, chips no sel., íconos inactivos | 30 % |
| **Acento / CTA** | `#AF5012` | Botón principal, chip/tab activo, bookmark, precio, avatar | **10 %** |

- **60 % Fondo** crema `#FDF4E8`: domina y aporta *"calma y coherencia"*.
- **30 % neutros cálidos**: los cuatro marrones de texto y estructura (derivados de canela) construyen
  jerarquía y separan contenido sin competir con el acento.
- **10 % acento** `#AF5012`: *"el protagonista visual que guía la acción"* (CTA, estado activo, precio).

Refinamiento clave: los neutros se llevaron a **marrones cálidos (no grises)**, para que todo viva en
la familia calabaza & canela y la paleta sea más cohesiva. La **paleta de feedback**
(éxito/error/advertencia/información) queda **fuera del 60-30-10** (colores funcionales y
transitorios). *(Los valores definitivos deben sincronizarse en las variables de Figma y en
[`../recetapp_tokens.json`](../recetapp_tokens.json), que aún tienen los valores previos — ver M5 en
[`mejoras-pendientes.md`](mejoras-pendientes.md#sistema-visual--tokens).)*

→ `Estilo` Regla 60-30-10 · paleta consolidada por feedback (Clase 10) · `Ley` von Restorff (acento aislado, Clase 9 sl. 30) · `Heurística` Consistencia y estándares (#4).

**Color tokenizado (primitivos + semánticos).**
La Clase 10 advierte que el color *"puede salirse de control… docenas de valores usados de manera
inconsistente"*. Por eso el color se gestiona con **tokens**: primitivos (escalas 50–900) referidos
por **alias semánticos** (`action/default`, `text/primary`, `feedback/error`…). Cambiar el alias
**cambia en todos lados** —la promesa de consistencia "a escala" del sistema de diseño.
→ `Estilo` Tokens de diseño contra la inconsistencia (Clase 10) · `Regla` variables `Color/Semanticos`.

**Accesibilidad del color — evidencia WCAG AA (verificada por cálculo).**
Toda la paleta definitiva pasa AA sobre el fondo crema `#FDF4E8`:

| Par sobre fondo `#FDF4E8` | Ratio | Umbral | |
|---|---|---|---|
| Texto primario `#2B1B12` | **15,2:1** | 4,5 (texto) | ✓ |
| Texto secundario `#6E4631` | **7,5:1** | 4,5 (texto) | ✓ |
| Texto terciario / placeholder `#7D6657` | **4,9:1** | 4,5 (texto) | ✓ |
| Borde / divisor `#9C8674` | **3,2:1** | 3,0 (no textual) | ✓ |
| Acento `#AF5012` (precio/texto) | **4,9:1** | 4,5 (texto) | ✓ |
| Blanco sobre acento `#AF5012` (botón) | **5,3:1** | 4,5 (texto) | ✓ |

Decisiones duras detrás de los valores: el acento se fijó en **calabaza 600 `#AF5012`** (el 500
`#C75A12` daba 4,29:1 con blanco, **no** pasa); incluso el **placeholder** terciario llega a 4,9:1
(supera AA de texto normal, donde muchas paletas fallan); el **dorado** de realce nunca lleva texto
blanco, solo oscuro. Verificación final con **STARK** en Fase 5.
→ `A11y` 1.4.3 Contraste mínimo 4,5:1 · 1.4.11 Contraste no textual 3:1 (Clase 4 sl. 20) · `Regla` R9.

**No depender solo del color (WCAG 1.4.1 A).**
El color nunca comunica estado por sí solo: se combina con **forma, ícono o etiqueta** (tab activa =
color **+** etiqueta; chip seleccionado = relleno **+** forma; error = color **+** texto).
→ `A11y` 1.4.1 Uso del color (Clase 4 sl. 20) · `Regla` R10.

---

## 3. Espaciado y grilla

**Escala estricta de 8 puntos.**
Todo el espaciado y las proporciones son múltiplos de 8 (`space/8…64`; el 4 solo como medio-paso
excepcional). La Clase 9 lo enseña como **"la regla de los 8 puntos"** (sl. 71): valores y
proporciones en múltiplos de 8, que dan ritmo y alineación consistentes.
→ `Patrón` Regla 8pt (Clase 9 sl. 71) · `Estilo` Ritmo / Alineación (principios de composición, Clase 10).

**Grilla de 4 columnas, margen y gutter de 16, sobre frame iPhone 15 (393×852).**
La Clase 9 habilita para mobile **1/2/4/8 columnas** (sl. 69); se eligieron **4 columnas** con
**margen y gutter de 16**. El gutter de 16 es además el margen lateral global de toda la app.
→ `Patrón` Sistema de grillas mobile (Clase 9 sl. 64–70) · `Regla` R3 (gutter 16).

**Superficies como paneles "inset" (no a sangre) y radios escalonados.**
Los bloques blancos se muestran con margen lateral 16 + esquinas redondeadas, sobre el fondo crema
—elimina el corte duro crema↔blanco y agrupa visualmente. Radios: `sm` 8 (inputs/chips), `md` 12
(botones), `lg` 16 (cards).
→ `Ley` Proximidad / uso del espacio (Clase 9 sl. 26) · `Regla` R4 (paneles inset).

---

## 4. Iconografía

**Set único Tabler (outline), con el trazo atado a un token de color.**
La Clase 10 sostiene que *"un buen ícono no necesita explicación; si la necesita, es un mal ícono"*.
Se usa un **único set Tabler outline** (lenguaje coherente) y el **trazo (stroke)** se ata a
`text/primary`; al recolorear (p. ej. tab activa) se toca **solo el trazo**, nunca el relleno.
→ `Estilo` Iconografía clara y consistente (Clase 10) · `Heurística` Consistencia y estándares (Nielsen #4).

**Los íconos siempre acompañados de texto en navegación.**
Ningún destino o acción de navegación depende solo del ícono: llevan **etiqueta textual** (tab bar,
atajos). Refuerza comprensión y accesibilidad.
→ `A11y` 1.4.1 no solo color/forma (Clase 4) · `Regla` R2, R10.

---

## 5. Sistema de componentes (Atomic Design)

**No es solo un UI Kit: es un Sistema de Diseño.**
La Clase 10 distingue **UI Kit** (botones, inputs, colores… "acelera el diseño") de **Design System**
(*"componentes + tokens + guías de uso + pautas de accesibilidad + documentación"* que *"garantiza
consistencia a escala: cuando algo cambia, cambia en todos lados"*). RecetApp tiene las tres capas:
**tokens** (variables de color/medida), **componentes** (UI Kit con variantes y *component
properties*) y **guías de uso** (las reglas transversales R1–R16) → funciona como **Design System**.
→ `Estilo` Design System vs UI Kit (Clase 10) · `Heurística` Consistencia y estándares (Nielsen #4).

**Construcción por Atomic Design (Brad Frost).**
La Clase 10 enseña que *"hoy ya no diseñamos páginas, sino elementos de UI"* y los organiza en 5
niveles. El sistema de RecetApp mapea así:

| Nivel (Clase 10) | En RecetApp |
|---|---|
| **Átomos** | tokens de color/tipografía, `icon/*`, `Button`, `Input`, `Chip` |
| **Moléculas** | `Stepper`, `Campo de búsqueda`, `Fila de ajuste`, `Input con unidad`, `Fila seleccionable` |
| **Organismos** | `Tab bar`, `Card de receta`, `Encabezado de subpantalla`, `Segmented control`, `Fila de ingrediente` |
| **Plantillas** | layout de cada pantalla (header + contenido + tab bar) |
| **Páginas** | las pantallas con contenido real (Home, Perfil, Recetas…) |

Esto habilita además el entregable **opcional "Atomic Design"** de la consigna.
→ `Estilo` Atomic Design: átomos→moléculas→organismos→plantillas→páginas (Clase 10).

---

## Tabla resumen — Sistema Visual

| Decisión transversal | Fundamento principal |
|---|---|
| Poppins + Inter (Sans Serif) | **Sans Serif legible en pantalla** (Clase 10) + legibilidad (Clase 4) |
| Jerarquía por escala tipográfica (8 estilos) | **Escala = jerarquía** (Clase 10) |
| Paleta cálida "Calabaza & canela", sin rojo | **Psicología del color** (Clase 10) + público objetivo |
| Reparto 60-30-10 (acento calabaza 600) | **Regla 60-30-10** (Clase 10) + von Restorff |
| Color por tokens semánticos | **Tokens contra inconsistencia** (Clase 10) |
| Acento = calabaza 600 (no 500) | **Contraste 4.5:1** (Clase 4) · R9 |
| Escala 8pt + grilla 4 col + gutter 16 | **8pt + grilla mobile** (Clase 9 sl. 64–71) |
| Paneles inset + radios escalonados | **Proximidad / uso del espacio** (Clase 9) · R4 |
| Íconos Tabler outline + etiqueta | **Ícono claro** (Clase 10) + 1.4.1 (Clase 4) |
| UI Kit como Design System (Atomic) | **Design System + Atomic Design** (Clase 10) |

---

## Evidencias de accesibilidad del sistema visual (WCAG 2.2 AA)

- **Contraste (1.4.3 AA):** acento `#AF5012` ≥4.5:1 con blanco; estados de feedback con texto blanco
  verificados AA; textos `text/primary`/`text/secondary` AA holgado. Verificación final con **STARK**
  (Fase 5).
- **Uso del color (1.4.1 A):** todo estado combina color **+** forma/ícono/etiqueta.
- **Tipografía legible:** Sans Serif, cuerpo ≥12pt, interlineado de lectura 160% (> 1,5), sin
  justificar (Clase 4 sl. 21).
- **Área táctil (2.5.8 AA):** controles con objetivo **≥44×44** (ideal del deck; el mínimo es 24×24).
