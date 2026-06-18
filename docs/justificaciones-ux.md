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

## Pantallas pendientes

A documentar a medida que se diseñen: **Recetas · Detalle de receta · Planificación ·
Perfil · Ingredientes · Notificaciones**. Cada una seguirá esta misma estructura
(estructura → decisiones y justificación → tabla de leyes/patrones → accesibilidad).
