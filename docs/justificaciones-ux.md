# Justificaciones de diseño UX — RecetApp

> Documento de fundamentación de las decisiones de diseño, pantalla por pantalla.
> Registra **qué patrón / ley UX** se aplicó, **dónde** y **por qué**, junto con las
> decisiones de **accesibilidad WCAG AA**. Alimenta el *Documento de fundamentación*
> (Fase 7) y la *Presentación* (bloques 4 "Patrones de diseño" y 5 "Evaluación heurística").
>
> Contexto completo del proyecto: [`../RecetApp - Handoff y contexto.md`](../RecetApp%20-%20Handoff%20y%20contexto.md).
> node IDs y estado: [`contexto-figma.md`](contexto-figma.md).

---

## Marco de referencia

Las decisiones se apoyan en tres fuentes, alineadas con la cátedra:

- **Leyes UX** (lawsofux.com) — heurísticas de comportamiento (Hick, Fitts, Jakob, Miller, Von Restorff, etc.).
- **Material Design 3 + iOS Human Interface Guidelines** — patrones de plataforma mobile (Clase 10 los fija como marcos de referencia).
- **WCAG 2.1 nivel AA** — contraste 4.5:1 (texto normal), área táctil ideal 44×44 px, no depender solo del color (Clase 4).

Reglas duras del sistema heredadas del handoff: botón/acento primario = **calabaza 600 `#AF5012`** (el 500 no pasa AA); dorado solo como acento con texto oscuro; escala de espaciado estricta de 8 pt.

---

## Pantalla: Home (`56:2`)

**Concepto rector:** *"Cociná con lo que tenés"*. Home no es un feed genérico de recetas
(eso es la pestaña Recetas), sino una pantalla de **sugerencias accionables a partir de
los ingredientes que el usuario ya tiene** y de accesos rápidos a sus tareas frecuentes.

### Estructura (de arriba hacia abajo)

1. **Header** — saludo personalizado ("Hola, Octavio 👋") + campana de notificaciones con badge.
2. **Atajos** — fila de 4 accesos directos: Cargar ingrediente · Cargar ticket · Recetas guardadas · Lista de compras.
3. **Buscador** (sticky) — "Buscar recetas".
4. **"Sugerencias para ti"** — grilla de 2 columnas de recetas, con **scroll infinito**.
5. **Tab bar** — 5 destinos: Home · Recetas · Planificación · Ingredientes · Perfil.

### Decisiones y su justificación

**Atajos a acciones comunes en la zona superior.**
Son entradas directas a tareas que normalmente viven 1–2 niveles más abajo en la
navegación (cargar ingredientes, ver guardadas, lista de compras). Ubicarlas arriba
**reduce la profundidad de navegación** y expone lo más frecuente apenas se abre la app.
Se eligieron exactamente 4 para no saturar la decisión inicial.
→ *Hick's Law* (menos opciones, decisión más rápida) · *Fitts's Law* (objetivos grandes y
cercanos, área táctil ≥44 px) · *ley de Tesler / reducción de fricción*.

**Grilla de 2 columnas para las sugerencias (no carrusel).**
Para un feed largo con scroll, la grilla vertical es el patrón estándar de apps de recetas
(Cookpad, Mealime): permite **escanear más opciones de un vistazo** y aprovecha el ancho.
Motivó crear una variante compacta de card (`55:16`) con solo lo esencial: foto, título,
tiempo, dificultad y precio.
→ *Ley de la región común / agrupación* (Gestalt) · *Aesthetic-Usability Effect*.

**Contenido mínimo de la card.**
Se mantienen foto, título, **precio**, **tiempo de cocción** y **dificultad** — los datos que
el usuario usa para decidir qué cocinar sin entrar al detalle. Se omiten metadatos
secundarios (porciones, tags) para no recargar la tarjeta.
→ *Miller's Law / chunking* (información acotada y digerible) · *jerarquía visual*.

**Scroll infinito con red de seguridad de accesibilidad.**
El feed carga más recetas al llegar al final (descubrimiento sin fricción). Para mitigar
los problemas conocidos del patrón (trampa de foco para teclado/lector de pantalla, no
saber dónde termina), se definió: tab bar **siempre fija y alcanzable**, anuncio de carga de
nuevos ítems vía *live region*, y un botón **"Cargar más"** visible como alternativa al
auto-load.
→ *Patrón Infinite Scroll* con consideraciones WCAG (2.4.3 Orden del foco, 4.1.3 Mensajes de estado).

**Buscador sticky.**
Queda pegado al tope del contenido al hacer scroll, para que la búsqueda siga disponible
durante el recorrido del feed infinito.
→ *Jakob's Law* (patrón familiar) · accesibilidad de alcance.

**Tab bar de 5 destinos.**
Cinco es el máximo recomendado por iOS HIG / Material para *bottom navigation*; estamos en
el límite sano. Home y Perfil se ubican en los extremos (posiciones más memorables y
alcanzables con el pulgar).
→ *Jakob's Law* (navegación inferior estándar) · *Serial Position Effect* (extremos) · *Fitts's Law*.

**FAB descartado.**
La propuesta inicial tenía un FAB para "agregar ingrediente", pero esa acción ya vive en los
atajos superiores. Se eliminó para **evitar accesos duplicados** y ruido visual.
→ *Consistencia y estándares* (Nielsen #4) · *Aesthetic and minimalist design* (Nielsen #8).

**Saludo personalizado + "para ti".**
Refuerzan continuidad y pertenencia, y hacen la pantalla más cálida (coherente con la paleta
"Calabaza & canela").
→ *Aesthetic-Usability Effect* · *Peak-End / vínculo emocional*.

### Tabla resumen — leyes y patrones

| Aplicación en Home | Ley / patrón |
|---|---|
| 4 atajos + 5 destinos; chips e íconos reconocibles | **Hick's Law** + **Jakob's Law** |
| Atajos saltan niveles de navegación; objetivos ≥44 px | **Fitts's Law** + reducción de fricción |
| Feed agrupado en cards de info acotada | **Miller's Law / chunking** |
| Grilla y secciones con agrupación visual clara | **Gestalt (región común)** |
| Ítem activo único en color sólido (calabaza) | **Von Restorff (aislamiento)** |
| Home y Perfil en los extremos de la tab bar | **Serial Position Effect** |
| Saludo personalizado, estética cálida coherente | **Aesthetic-Usability Effect** |

### Accesibilidad (WCAG AA) en Home

- **Contraste:** `text/primary #2E1E12` y `text/secondary #5C4A3A` sobre crema/blanco superan AA holgado. Estado activo e íconos de acción en **calabaza 600 `#AF5012`** (verificado ≥4.5:1).
- **No depender del color:** el badge de la campana usa color **+ número** ("3"); el ítem activo de la tab bar combina color **+ etiqueta de texto** (no solo el ícono).
- **Área táctil:** atajos, íconos del header y celdas de la tab bar con objetivo ≥44×44 px.
- **Texto visible en navegación:** cada atajo y cada destino de la tab bar lleva etiqueta textual, no solo ícono.
- **Scroll infinito accesible:** ver "red de seguridad" arriba (foco, live region, "Cargar más").
- **Pendiente de verificación con STARK** al maquetar estados finales (Fase 5).

---

## Pantalla: Perfil (`112:166`) + subpantallas

**Concepto rector:** Perfil concentra los datos que **personalizan las sugerencias** de la
app (restricciones, objetivo, actividad, hogar). No es un feed ni un panel de cuenta: es
una **pantalla de configuración** a la que el usuario vuelve a ajustar valores puntuales.
Alcance ceñido al sitemap (6 campos); la identidad se muestra pero no es editable y no se
agregan ajustes de cuenta/app en esta etapa (*consistente con el enunciado del TP*).

### Estructura

**Vista principal** (`112:166`):
1. **Bloque de identidad** — avatar + nombre + email (solo lectura).
2. **"Sobre mí"** — Peso y altura · Objetivo nutricional · Actividad deportiva · Restricciones personales.
3. **"Mi hogar"** — Personas en casa · Restricciones familiares.
4. **Tab bar** con Perfil activo.

**Subpantallas** (una plantilla por tipo de dato, todas con encabezado *‹ volver + título*):
- **Restricciones personales** (`112:197`) — lista de **selección múltiple** (checkboxes).
- **Objetivo nutricional** (`112:221`) — lista de **selección única** (radios).
- **Peso y altura** (`112:245`) — dos **inputs con unidad** (kg / m).
- **Personas en casa** (`112:269`) — un **input** numérico.
- *Actividad deportiva* y *Restricciones familiares* reutilizan exactamente las plantillas
  de selección única y múltiple respectivamente (se clonan en el maquetado final, Fase 5).

### Decisiones y su justificación

**Lista de ajustes con filas + divisores, no cards.**
Las 6 opciones son **entradas de navegación a sub-ajustes**, no objetos de contenido
independientes: el patrón correcto es la *grouped list* (iOS HIG / Material), filas con
divisor bajo encabezados de sección. Reemplaza la propuesta inicial de 6 cards apiladas,
que recargaba visualmente y chocaba con la regla del proyecto *"evitar uso excesivo de
Cards"*.
→ *Jakob's Law* (los ajustes se ven como ajustes en todas las apps) · *Aesthetic and
minimalist design* (Nielsen #8). Ver regla transversal **R5**.

**Agrupación "Sobre mí" / "Mi hogar".**
Los 6 campos se ordenan según el modelo mental **"yo" vs "mi grupo familiar"** — el mismo
que estructura las restricciones. Reduce la carga de escaneo y da sentido al orden.
→ *Ley de la región común / agrupación* (Gestalt) · *Miller's Law / chunking*.

**Valor actual como subtítulo.**
Cada fila muestra el dato vigente ("70 kg · 1,75 m", "Mantener peso") sin necesidad de
entrar; los vacíos se rotulan "Ninguna" en `text/disabled`.
→ *Recognition over recall* (Nielsen #6) · reduce profundidad de navegación. Ver **R6**.

**Encabezado de subpantalla fijo (back + título).**
Toda subpantalla abre con un encabezado de **alto fijo (52)**, botón volver de 32 y título
`Texto/H3`, idéntico en las cuatro vistas. Da una ruta de regreso siempre predecible.
→ *Jakob's Law* · *User control and freedom* (Nielsen #3). Ver **R1**.

**Restricciones como selección múltiple desde un catálogo.**
En vez de una lista editable con "Agregar" + borrar (texto libre), se ofrece un **catálogo
de restricciones frecuentes** y el usuario **tilda** las que apliquen. Datos consistentes,
sin errores de tipeo, menos pasos.
→ *Recognition over recall* · *Error prevention* (Nielsen #5) · *Hick's Law* (decisión guiada).

**El control se elige según el tipo de dato.**
Selección única (Objetivo, Actividad) → radios; selección múltiple (Restricciones) →
checkboxes; valores numéricos libres (Peso, altura, Personas) → inputs. Coherencia entre
forma del control y naturaleza del dato.
→ *Jakob's Law* · *Consistency and standards* (Nielsen #4).

**Auto-guardado, sin botón "Guardar".**
Las ediciones se persisten al volver (estándar de ajustes mobile); se quitó el botón
"Guardar" incluso en Peso y altura, y el stepper de Personas en casa se reemplazó por un
input para unificar el patrón de edición numérica. Menos fricción y menos UI.
→ *Reducción de fricción (Tesler)* · *Aesthetic and minimalist design* (Nielsen #8). Ver **R7**.

**Superficies como paneles inset + gutter global de 16.**
Los paneles blancos no van a sangre: margen lateral 16 + esquinas `radius/lg`, sobre el
fondo crema. Elimina el corte duro crema↔blanco y unifica el ritmo de toda la app.
→ *Aesthetic-Usability Effect* · Gestalt (región común). Ver **R3** y **R4**.

### Tabla resumen — leyes y patrones

| Aplicación en Perfil | Ley / patrón |
|---|---|
| Lista de ajustes (filas + divisores) en vez de cards | **Jakob's Law** + Nielsen #8 |
| Agrupación "Sobre mí" / "Mi hogar" | **Gestalt (región común)** + **Miller / chunking** |
| Valor vigente visible en cada fila | **Recognition over recall** (Nielsen #6) |
| Catálogo de restricciones tildables (no texto libre) | **Error prevention** (Nielsen #5) + **Hick** |
| Control según tipo de dato (radio/check/input) | **Consistency & standards** (Nielsen #4) |
| Encabezado de regreso fijo y consistente | **User control & freedom** (Nielsen #3) |
| Auto-guardado, sin Guardar | **Reducción de fricción (Tesler)** |

### Accesibilidad (WCAG AA) en Perfil

- **Contraste:** títulos en `text/primary #2E1E12` y valores en `text/secondary #5C4A3A`
  sobre paneles blancos (AA holgado). Estado seleccionado y tab activa en **calabaza 600
  `#AF5012`** (≥4.5:1).
- **No depender solo del color:** los seleccionables combinan color **+ forma e ícono**
  (checkbox tildado / radio relleno con ✓); la tab activa combina color **+ etiqueta**.
- **Área táctil:** filas, botón volver (32 + área de fila), ítems de tab bar y filas de
  selección con objetivo ≥44 px.
- **Estados vacíos diferenciados** ("Ninguna" en `text/disabled`) — no se confunden con un
  valor real.
- **Pendiente de verificación con STARK** al maquetar estados finales (Fase 5).

---

## Pantallas pendientes

A documentar a medida que se diseñen: **Recetas · Detalle de receta · Planificación ·
Ingredientes · Notificaciones**. Cada una seguirá esta misma estructura
(estructura → decisiones y justificación → tabla de leyes/patrones → accesibilidad).
