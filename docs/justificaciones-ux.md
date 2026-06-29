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

> Ficha con el **sistema de chips** trazable (ver [`sistema-visual.md`](sistema-visual.md#cómo-leer-las-etiquetas)).

**Concepto rector:** *"Cociná con lo que tenés"*. Home no es un feed genérico de recetas (eso es la
pestaña Recetas), sino una pantalla de **sugerencias accionables** a partir de los ingredientes que el
usuario ya tiene, más **accesos rápidos personalizados** a sus tareas más frecuentes.

### Estructura (de arriba hacia abajo)
1. **Header** — saludo personalizado ("Hola, Usuario 👋") + campana de notificaciones con badge ("3").
2. **Buscador** — "Buscar receta" (tope del contenido, sticky en el scroll).
3. **Fila de 4 accesos rápidos** — Cargar ingrediente · Cargar ticket · Recetas guardadas · Lista de
   compras (íconos circulares + etiqueta).
4. **"Sugerencias para ti"** — grilla de 2 columnas (card compacta `55:16`), con scroll.
5. **Tab bar** — 5 destinos (Home activo).

### Decisiones y su justificación

#### ① Criterio de los 4 accesos rápidos: sugeridos por IA según frecuencia
**Pregunta de cátedra: ¿con qué criterio se eligen las 4 acciones de arriba?** No son un set fijo: la
app **sugiere mediante IA los accesos más frecuentes del usuario** como *shortcuts* personalizados (en
el ejemplo: cargar ingrediente, cargar ticket, ver guardadas, lista de compras — acciones que viven en
**distintas secciones** y que el usuario usa seguido). Es una **interfaz adaptable**: muestra lo que el
usuario probablemente quiere hacer ahora, sin obligarlo a navegar en profundidad. Se exhiben
**exactamente 4** para no saturar la decisión. *(Al ser un TP de diseño sin backend, el criterio se
justifica a nivel de diseño: el contenido de los shortcuts es personalizable / aprendido por
frecuencia.)*
`Heurística` Flexibilidad y eficiencia de uso (#7 — aceleradores para acciones frecuentes) · Reconocimiento antes que recuerdo (#6) · `Patrón` Accesos rápidos (Clase 9 sl. 58) · `Ley` Hick (4 opciones, sl. 23) · Fitts (objetivos grandes/cercanos, sl. 24) · Tesler (fricción, sl. 29)

> **Distinción con Ingredientes:** los 4 tiles del Home son **adaptativos** (los más frecuentes del
> usuario, tomados de toda la app); los 4 de Ingredientes son el **set fijo y completo** de métodos de
> carga. Mismo formato visual, **criterio distinto** — vale aclararlo en la defensa.

#### ② Buscador en el tope
Queda arriba (y sticky durante el scroll del feed) para que buscar una receta esté siempre a mano.
Patrón familiar de apps de contenido.
`Patrón` Buscar (Clase 9 sl. 60) · `Ley` Jakob (sl. 25) · `Heurística` Flexibilidad y eficiencia (#7)

#### ③ Sugerencias en grilla de 2 columnas (no carrusel)
Para un feed largo con scroll, la **grilla vertical** (patrón de apps de recetas) permite **escanear
más opciones de un vistazo** y aprovecha el ancho. Reutiliza la card compacta `55:16` con contenido
**mínimo** para decidir sin entrar al detalle (foto, título, tiempo, dificultad, precio).
`Patrón` Galería / retícula (Clase 9 sl. 45) · `Ley` Proximidad (agrupación, sl. 26) · Miller / chunking (sl. 27) · `Estilo` jerarquía visual (Clase 10)

#### ④ Scroll infinito con red de seguridad de accesibilidad
El feed carga más recetas al llegar al final (descubrimiento sin fricción). Para mitigar los problemas
del patrón (trampa de foco, no saber dónde termina): tab bar **siempre fija**, anuncio de carga vía
*live region*, y botón **"Cargar más"** como alternativa al auto-load.
`Patrón` Paginado vs Scroll infinito (Clase 9 sl. 49) · `A11y` 2.4.3 Orden del foco · 4.1.3 Mensajes de estado

#### ⑤ Tab bar de 5 destinos; FAB descartado
Cinco destinos es el máximo sano para *bottom navigation*; Home y Perfil en los extremos (más
memorables/alcanzables con el pulgar). Se **descartó el FAB** de "agregar ingrediente" porque esa
acción ya vive en los accesos rápidos (evita acceso duplicado y ruido).
`Patrón` Tab bar - Pestañas (Clase 9 sl. 41) · `Ley` Posición en serie (extremos, sl. 28) · Fitts (sl. 24) · `Heurística` Consistencia y estándares (#4) · Diseño estético y minimalista (#8) · `Regla` R2

#### ⑥ Saludo personalizado + "para ti"
Refuerzan pertenencia y calidez, coherentes con la paleta cálida y el **contexto emocional de las
personas** (deciden bajo presión: una Home cálida y personalizada baja la tensión).
`Estilo` tono cálido / Aesthetic-Usability (Clase 10) · vínculo con público objetivo

### Tabla resumen — leyes / patrones / heurísticas

| Aplicación en Home | Ley / patrón / heurística |
|---|---|
| 4 accesos rápidos sugeridos por IA (frecuencia) | **Flexibilidad y eficiencia** (#7) + **Accesos rápidos** (Clase 9) |
| Limitar a 4 accesos / 5 destinos | **Hick** + **Jakob** |
| Objetivos grandes que saltan niveles | **Fitts** + reducción de fricción (Tesler) |
| Feed en grilla, card de info acotada | **Galería/retícula** (Clase 9) + **Miller** |
| Home/Perfil en los extremos de la tab bar | **Posición en serie** |
| Scroll infinito accesible | **Paginado vs Scroll** (Clase 9) + WCAG 2.4.3/4.1.3 |
| Saludo personalizado, estética cálida | **Aesthetic-Usability** |

### Accesibilidad (WCAG 2.2 AA) en Home

- **Contraste:** `text/primary`/`text/secondary` sobre crema/blanco AA holgado; acento e íconos de
  acción en **calabaza 600 `#AF5012`** (≥4.5:1).
- **No depender solo del color (1.4.1):** badge de la campana = color **+ número** ("3"); tab activa =
  color **+ etiqueta**.
- **Área táctil (2.5.8):** accesos rápidos, íconos del header y celdas de la tab bar ≥44×44.
- **Texto en navegación:** cada acceso rápido y cada destino lleva etiqueta textual, no solo ícono.
- **Scroll infinito accesible:** foco, live region, "Cargar más". Verificación con **STARK** en Fase 5.

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

## Pantalla: Ingredientes (`163:605`) + flujo de carga

> Ficha con el **sistema de chips** trazable (ver [`sistema-visual.md`](sistema-visual.md#cómo-leer-las-etiquetas)).

**Concepto rector:** Ingredientes es la **despensa del usuario** — la fuente de verdad de "qué tengo
en casa" que alimenta las sugerencias del Home. La pestaña cumple dos trabajos: **ver/ajustar** lo que
ya hay y **cargar** lo nuevo por cuatro vías (manual, voz, foto del ticket, código de barras). Como la
**fricción de carga es el riesgo principal del producto**, el diseño expone **accesos directos a los
cuatro métodos arriba de todo** y cierra las cargas automáticas con una **vista previa de
confirmación**.

### Estructura y estados
- **Vista principal** (`163:605`, pestaña raíz): encabezado de pestaña raíz (título `Texto/H1` +
  subtítulo `Body M`, R11) + **fila de 4 acciones** (tiles ícono+etiqueta) + sección **"MIS
  INGREDIENTES"** con control **Editar** + **lista de filas + divisores** (miniatura + nombre +
  cantidad) + tab bar (Ingredientes activo).
- **Modo edición** (`165:663`): el control pasa a **Listo**; cada fila muestra **tacho** (izq) +
  **stepper − / +**; "Listo" **auto-guarda**.
- **Estado vacío** (`166:801`): ícono canasta + "Todavía no cargaste nada" + bajada + CTA "Cargar
  ingredientes".
- **Subpantallas de carga** (encabezado *‹ volver*, **sin tab bar** → modal, R15):
  - **Carga manual** (`167:847`) — buscador sobre catálogo + resultados seleccionables + cantidad
    (stepper) + "Agregar ingrediente".
  - **Carga por voz** (`168:888`) — transcripción en vivo + micrófono (grabar→detener) +
    Reintentar / Continuar.
  - **Foto del ticket** (`169:898`) y **Código de barras** (`182:1372`) — mismo visor de cámara;
    cambian el marco-guía y el título.
  - **Revisar ingredientes** (`169:1050`) — vista previa editable donde **convergen** voz, ticket y
    código.

### Decisiones y su justificación

#### ① Botones de acceso a las acciones (4 métodos arriba de todo)
Las cuatro vías de carga se exponen como **tiles grandes** en la zona superior, no escondidas en un
menú: reducir la fricción de carga es crítico para mantener la despensa actualizada, y tenerlas a mano
es **acción directa sin navegar en profundidad**. Son **espejo de los atajos del Home** (redundancia
intencional). Exactamente 4 para no saturar la decisión.
`Patrón` Accesos rápidos (Clase 9 sl. 58) · `Ley` Fitts (objetivos grandes/cercanos, sl. 24) · Hick (4 opciones, sl. 23) · Tesler (fricción, sl. 29) · `Heurística` Flexibilidad y eficiencia de uso (#7) · `A11y` 2.5.8 área ≥44 · 1.4.1 ícono+etiqueta

> ⚠️ **Inconsistencia detectada:** la vista principal muestra *Manual · Ticket · Barras · **Atajo***
> (el 4.º es el micrófono pero etiquetado "Atajo"), mientras el estado vacío muestra *Manual · **Por
> voz** · Ticket · Barras* — difieren **etiqueta** y **orden**. → registrado como **M3** en
> [`mejoras-pendientes.md`](mejoras-pendientes.md#ingredientes-163605). `Heurística` Consistencia y estándares (#4) · `A11y` 3.2.4 Identificación consistente.

#### ② Edición por modo explícito — **patrón general de la app** (R13)
En reposo la lista es **solo lectura** (cantidad como texto, mínimo ruido); el control **Editar**
activa el **modo edición** (aparecen **stepper − / +** y **tacho** por fila) y pasa a **Listo**, que
**auto-guarda** (R7). Separar *ver* de *editar* **evita cambios accidentales** de cantidad y borrados
involuntarios. Es un **patrón transversal**: el mismo modelo "modo explícito para editar" ordena la
edición de listas en toda la app y se apoya en la red de seguridad de las acciones destructivas (R17).
`Patrón` Edición de listas (Clase 9 sl. 61) · `Ley` Jakob (patrón iOS/Material, sl. 25) · `Heurística` Prevención de errores (#5) · Diseño estético y minimalista (#8) · Control y libertad (#3) · `Regla` R13, R7, R17

#### ③ Ventanas de acciones (las 3 pantallas de captura)
**Carga manual — buscar contra catálogo, no texto libre.** El buscador resuelve sobre la base de
ingredientes de la app (datos normalizados, sin errores de tipeo); se elige de una lista y la cantidad
se fija con el mismo **stepper**. Al ser **explícita**, su "Agregar" **confirma directo** (sin vista
previa).
`Patrón` Buscar (Clase 9 sl. 60) · `Heurística` Reconocimiento antes que recuerdo (#6) · Prevención de errores (#5) · Consistencia y estándares (#4)

**Carga por voz — transcripción en vivo, estado por color + forma.** El micrófono en grabación va en
`feedback/error` y **cambia de forma** (círculo-mic → cuadrado-detener); "Escuchando…" + la
transcripción en vivo informan el estado. La voz es **uno de cuatro métodos**, nunca la única vía.
`Heurística` Visibilidad del estado del sistema (#1) · `A11y` 1.4.1 estado por color **+** forma · voz no como única opción (Clase 4 sl. 23) · `Regla` R10

**Cámara única para ticket y código.** Mismo visor y obturador; sólo cambian el **marco-guía**
(rectángulo amplio para el ticket / franja para el código) y el título + la instrucción ("Encuadrá…").
Menos superficie que mantener y experiencia consistente.
`Heurística` Consistencia y estándares (#4) · Visibilidad del estado (#1, el marco guía la acción) · `Ley` Jakob (visor familiar)

#### ④ Vista previa de carga para confirmar (Revisar ingredientes, R12)
Voz, ticket y código **infieren de una fuente ruidosa** y pueden equivocarse. Antes de escribir en la
despensa, los tres **convergen** en una pantalla editable —"Detectamos estos ingredientes. Ajustá o
quitá lo que no corresponda antes de guardar"— con **tacho + stepper** por fila y acciones **Descartar
/ Confirmar**. La carga manual no la necesita (ya es explícita) → un paso menos donde no hace falta.
`Patrón` Vista previa de confirmación · `Heurística` Prevención de errores (#5) · Ayuda a reponerse de errores (#9) · Visibilidad del estado (#1) · Control y libertad (#3) · `Regla` R12

### Tabla resumen — leyes / patrones / heurísticas

| Aplicación en Ingredientes | Ley / patrón / heurística |
|---|---|
| 4 métodos como tiles grandes arriba | **Accesos rápidos** (Clase 9) + **Fitts** + **Hick** |
| Modo edición explícito (Editar → Listo) | **Edición de listas** (Clase 9) + **Prevención de errores** (#5) |
| Buscar contra catálogo (manual) | **Reconocimiento antes que recuerdo** (#6) |
| Mic con color **+** forma; cámara única | **Visibilidad del estado** (#1) + **Consistencia** (#4) |
| Convergencia en Vista previa editable | **Prevención / recuperación de errores** (#5/#9) + **R12** |
| Stepper/fila/búsqueda reutilizados; chrome del Home | **Jakob** + consistencia |

### Accesibilidad (WCAG 2.2 AA) en Ingredientes

- **Contraste:** títulos `text/primary`, secundarios `text/secondary`; acción/estado activo en
  **calabaza 600 `#AF5012`** (≥4.5:1); texto blanco sobre micrófono `feedback/error` y botones
  primarios, AA.
- **No depender solo del color (1.4.1):** método/tab activos, micrófono grabando y resultado
  seleccionado combinan color **+** ícono/forma/etiqueta.
- **Área táctil (2.5.8):** tiles, filas, volver, stepper, tacho, micrófono y obturador con objetivo
  ≥44 (la celda contenedora aporta el área en los más chicos).
- **Voz no excluyente:** la carga por voz es una de cuatro vías, no la única (Clase 4 sl. 23).
- **Estado vacío con salida clara:** canasta + "Todavía no cargaste nada" + CTA.
- **Mejora pendiente:** consistencia de los tiles de acción (**M3** en
  [`mejoras-pendientes.md`](mejoras-pendientes.md#ingredientes-163605)). Verificación con **STARK** en Fase 5.

---

## Pantalla: Recetas (`205:1472`) + Detalle + Filtros

> Ficha con el **sistema de chips** trazable (ver [`sistema-visual.md`](sistema-visual.md#cómo-leer-las-etiquetas)).

**Concepto rector:** Recetas es el **catálogo navegable** de la app. Concentra tres trabajos del mismo
nivel jerárquico —**buscar** recetas nuevas, volver a las **guardadas** y revisar el **historial
cocinado**— y desde cualquiera se entra al **Detalle**. El reto es navegar internamente sin competir
con la tab bar, mostrar un detalle muy denso sin abrumar, y **usar el patrón de disposición que
corresponde a cada trabajo** (descubrir ≠ revisar historial).

### Estructura y estados
- **Pestaña Recetas** (raíz, tab bar con Recetas activo): título "Recetas" (`Texto/H1`, R11) +
  **segmented control** de 3 secciones.
  - **Buscar** (`205:1472`): buscador + botón de filtros (badge de filtros activos) + **grilla 2
    columnas** (card compacta `55:16`).
  - **Guardadas / Mis recetas** (`207:1656`): grilla 2 columnas.
  - **Historial** (`207:1888`): **lista de filas agrupada por día** (Hoy / fecha) — *no* grilla de cards.
- **Filtros** (`208:1976`, **modal**, sin tab bar): segmented "Por ingredientes / Por características" + grupos
  de **chips** (Tiempo, Dificultad, Restricciones) + **Porciones** (stepper) + "Limpiar" + botón fijo
  "Aplicar filtros · N recetas".
- **Detalle de receta** (push, **mantiene tab bar**): **card hero ancha** (`204:168`) + **acordeones**
  (Ingredientes con Porciones y sustitución · Preparación · Información nutricional por porción). Frame
  de uso `232:2751` (393×852, 1.ª sección abierta); `210:2007` es el frame extendido (393×1193) con los
  3 acordeones desplegados para documentar componentes.

### Decisiones y su justificación

#### ① Navegación interna por tabs (segmented control)
Las tres secciones son del **mismo nivel jerárquico**; la cátedra habilita el patrón **Pestañas** para
"cambiar entre pantallas del mismo nivel de jerarquía". Se materializa como **segmented control** (un
contenedor que agrupa las 2–3 opciones, activo en blanco elevado), **distinto de los chips de
filtro**: el segmented **navega** entre secciones, los chips **seleccionan valores**. Mantener esa
distinción evita confundir *navegar* con *filtrar*.
`Patrón` Tab bar - Pestañas (Clase 9 sl. 41) · `Ley` Jakob (sl. 25) · Hick (sl. 23) · `Heurística` Consistencia y estándares (#4) · `Regla` R14

#### ② Filtros: tabs para el modo + chips para los valores
Filtros combina **dos controles para dos trabajos distintos**:
- **Segmented "Por ingredientes / Por características"** = cambio de **modo** → mismo patrón *Pestañas* que la
  navegación de secciones.
- **Chips por grupo** (Tiempo, Dificultad, Restricciones) = selección de **valores**; **multi-select**
  donde aplica (p. ej. Restricciones: *Sin TACC* + *Vegano*); el seleccionado va en **relleno calabaza,
  sin ✓** (la diferencia relleno↔contorno es de **forma**, no solo color).

El botón fijo **"Aplicar filtros · N recetas"** muestra en vivo cuántos resultados quedan y
**"Limpiar"** resetea. Filtros es **modal** (sin tab bar) por ser un editor.
`Patrón` Pestañas (modo) + Chips de filtro (valores) (Clase 9) · `Heurística` Visibilidad del estado (#1, contador en vivo) · Control y libertad (#3, Limpiar / modal) · `A11y` 1.4.1 relleno **+** forma · `Regla` R14, R15

#### ②b Los dos modos de Filtros nombran su *input*, no se acumulan
El label original **"Por filtros"** era circular (estás *dentro* de Filtros). Se renombró a
**"Por características"** para que cada modo se nombre por su **input**: *Por ingredientes* parte de lo que
tenés, *Por características* parte de los atributos de la receta (tiempo, dificultad, restricciones,
porciones). Además, **cada modo muestra un set distinto** —no se repiten los controles del otro— para
**no acumular decisiones** ni mezclar "buscar con lo que tengo" con "afinar por atributos".
`Estilo` Lenguaje claro / del usuario (Clase 10) · `Heurística` Coincidencia sistema-mundo real (#2) · Consistencia y estándares (#4) · `Ley` Hick (menos opciones por pantalla) · `Regla` R14

#### ②c Modo "Por ingredientes" — la despensa como punto de partida (`363:16472`)
Materializa el concepto rector (*"cociná con lo que tenés"*) dentro de la búsqueda: **campo de
búsqueda** + grupo **"Tu despensa"** con chips **multi-select** (tocás los que querés usar; el activo en
relleno calabaza) + grupo **"Otros ingredientes"** que junta lo que sumás **por búsqueda** y no está en
tu despensa. (Se evaluó un control de *Coincidencia* —"con lo que tengo / me falta poco"— y se
**descartó**: no se comportaba como un filtro claro y sumaba carga; "Otros ingredientes" cumple mejor el
trabajo de ampliar la base de búsqueda.) Reutiliza el **mismo Chip** y el ritmo "header `Texto/H3` +
grupo de chips" del otro modo (consistencia) y **reconoce en vez de pedir recordar** (elegís de listas,
no tipeás de memoria).
`Patrón` Buscar (Clase 9) + Chips de filtro (Clase 9) · `Heurística` Reconocimiento antes que recuerdo (#6) · Consistencia (#4) · Diseño minimalista (#8, se quitó un control que no aportaba) · `A11y` 1.4.1 relleno **+** forma · 2.5.8 área ≥44 · `Regla` R3, R14, R15

#### ②d Búsqueda de ingredientes = un solo patrón reutilizable (componente `369:4231`)
Al escribir en el buscador aparece una **lista de resultados** (fila = miniatura + nombre + acción
circular): el match y sus variantes ("Tomate" / "Tomate cherry · perita · triturado"). La acción es
**`+` para agregar** y **`✓` para lo ya seleccionado** (estado por **forma + color**, nunca solo color).
Es **el mismo componente y la misma búsqueda** en los tres lugares donde hace falta —**Carga manual**
(`167:847`), **Filtros "Por ingredientes"** (`374:11270`) y **Carga de ingrediente a la lista**
(Planificación)—; lo único que cambia es qué pasa al elegir: en Filtros el ítem pasa a "Otros
ingredientes" (multi, sin cantidad); en las cargas se elige **uno** y se define **cantidad** (stepper)
antes de **Agregar**. Un único patrón baja la curva de aprendizaje y garantiza consistencia. En Filtros
la búsqueda es **overlay** (reemplaza los grupos mientras escribís → foco en buscar).
`Patrón` Buscar (Clase 9 sl. 60) + Lista de resultados · `Heurística` Reconocimiento antes que recuerdo (#6) · Consistencia y estándares (#4) · Flexibilidad y eficiencia (#7) · `Ley` Jakob (buscar familiar) · `A11y` 1.4.1 (`+`/`✓` = forma + color) · 2.5.8 ≥44 · `Regla` **R18**, R13 (cantidad por modo)

#### ③ Detalle denso resuelto con acordeones
El Detalle es la pantalla más cargada (ingredientes, pasos, nutrición). Se agrupa en **acordeones**
(header + chevron + cuerpo colapsable), con la **primera sección abierta** por defecto y el resto
colapsado. La **card hero ancha** concentra arriba las acciones primarias (Guardar · Planificar) y los
metadatos (25 min · Fácil · $1.980); **Porciones** se ajusta con stepper y cada ingrediente ofrece el
ícono **sustituir** (`201:168`). El Detalle es **contenido** → push que **mantiene la tab bar**;
Filtros, en cambio, es modal (no atrapa al usuario).
`Patrón` Menú acordeón (Clase 9 sl. 51) · Cards (sl. 44) · `Heurística` Diseño estético y minimalista (#8) · Flexibilidad y eficiencia (#7, sustituir/porciones) · Control y libertad (#3, push no atrapa) · `Regla` R16, R15

#### ④ Historial como lista, no como card
El Historial **no es descubrimiento, es un registro cronológico** de lo cocinado, agrupado por día
(Hoy / 2 de junio). Por eso usa una **lista de filas** (miniatura + nombre + tiempo/dificultad +
acciones rápidas guardar/planificar), **no** la grilla de cards de Buscar/Guardadas. El patrón se
elige según el trabajo: **cards/galería para elegir y descubrir** (Buscar, Guardadas) vs **lista para
escanear muchos registros rápido** (Historial). Además respeta la regla del proyecto de **evitar el
uso excesivo de cards**.
`Patrón` Listas (Clase 9 sl. 42) vs Galería (sl. 45) · `Ley` Proximidad (agrupación por día, sl. 26) · `Heurística` Consistencia y estándares (#4, patrón acorde al contenido) · `Regla` R5 (filas, no cards)

### Tabla resumen — leyes / patrones / heurísticas

| Aplicación en Recetas | Ley / patrón / heurística |
|---|---|
| Segmented control para secciones | **Pestañas** (Clase 9 sl. 41) + **Jakob** + #4 |
| Filtros: segmented (modo) + chips (valores) | **Pestañas + Chips** (Clase 9) + #1 contador |
| Modos nombrados por su input (no "Por filtros") | **Coincidencia mundo real** (#2) + **Consistencia** (#4) |
| "Por ingredientes": despensa + Otros (búsqueda) | **Reconocimiento** (#6) + **Minimalista** (#8) |
| Búsqueda de ingredientes reutilizable (`+`/`✓`) | **Buscar** (Clase 9) + **Consistencia** (#4) + R18 |
| Chips de filtro: relleno + forma, sin ✓ | **Reconocimiento antes que recuerdo** (#6) + **1.4.1** |
| Detalle en acordeones + card hero | **Menú acordeón** (Clase 9) + #8 |
| Sustituir ingrediente / Porciones | **Flexibilidad y eficiencia** (#7) |
| Push (Detalle) mantiene tab bar; Filtros modal | **Control y libertad** (#3) + R15 |
| **Historial como lista (no card)** | **Listas** vs **Galería** (Clase 9) + **R5** |
| Badge de filtros activos | **Visibilidad del estado** (#1) |

### Accesibilidad (WCAG 2.2 AA) en Recetas

- **Contraste:** títulos `text/primary`, secundarios `text/secondary`; acción, precio y chip
  seleccionado en **calabaza 600 `#AF5012`** (≥4.5:1). Segmento activo = `bg/surface` + texto
  `text/primary`.
- **No depender solo del color (1.4.1):** segmento activo (relleno elevado **+** posición), chip
  seleccionado (relleno **+** forma), tab activa (color **+** etiqueta).
- **Área táctil (2.5.8):** segmentos, chips, botón de filtros, filas del historial y acciones de la
  card hero, controles de acordeón y stepper con objetivo ≥44.
- **Navegación coherente (3.2.3):** el mismo segmented y la tab bar se repiten en todo el módulo;
  encabezado de volver consistente (R1).
- **Mejora pendiente:** estados vacíos / sin resultados (Buscar sin resultados, sin guardadas,
  historial vacío) — **M4** en [`mejoras-pendientes.md`](mejoras-pendientes.md#recetas-2051472). STARK en Fase 5.

---

## Pantalla: Notificaciones (`292:5478`) + estados

> Ficha redactada con el **sistema de chips** trazable (ver [`sistema-visual.md`](sistema-visual.md#cómo-leer-las-etiquetas)):
> `Ley` `Patrón` `Heurística` (Nielsen, Clase 11) `Estilo` `A11y` (WCAG 2.2) `Regla`.

**Concepto rector:** Notificaciones es el **centro de avisos** de la app, al que se llega desde la
**campana del Home** (no es un destino de la tab bar). Reúne tres tipos de aviso coherentes con el
producto —**recordatorio de compra** ("faltan ingredientes para tu ensalada rusa"), **recordatorio
de planificación** ("¿Qué vamos a comer?") y **sugerencia de recetas**—, cada uno accionable. El
reto de diseño es **informar sin abrumar** y permitir **gestionar** (borrar) la lista sin riesgo de
errores irreversibles.

### Estructura y estados
- **Principal** (`292:5478`): encabezado *‹ volver + "Notificaciones"* (R1) + lista de **filas con
  divisor** (no cards): título `Texto/H3` + cuerpo `Body M` `text/secondary` + **tiempo relativo**
  (1 h / 2 h / 3 d) + chevron `›` navegable. Tab bar con **Home activo** (sub-flujo del Home).
- **Swipe para borrar** (`303:8407` izq · `303:10170` der): arrastrar la fila revela un botón
  **tacho** en `action/default` (calabaza) del lado del arrastre → eliminar.
- **Eliminada** (`303:10647`): la fila desaparece y aparece un **snackbar** "N eliminada" +
  **"Deshacer"** sobre la tab bar.
- **Vacío** (`303:10452`): ✓ + "¡Ninguna novedad por ahora!" centrado, sin CTA (no hay acción que
  ofrecer cuando no hay avisos).

### Decisiones y su justificación

**Lista de avisos como filas + divisores, escaneable por título.**
Cada aviso es una fila con título destacado, bajada y antigüedad; el chevron indica que es
accionable. El usuario **escanea títulos** (no lee palabra por palabra) y entra solo a lo que le
interesa. Mantiene el patrón de listas/ajustes de toda la app (no cards).
`Patrón` Listas (Clase 9 sl. 42) · Patrón de lectura F (sl. 37) · `Regla` R5 (filas, no cards) · R1 (volver) · R15 (push, mantiene tab bar)

**Tiempo relativo en cada aviso.**
"1 h / 2 h / 3 d" comunica la **vigencia** del aviso de un vistazo —más legible que una fecha
absoluta para contenido reciente.
`Heurística` Visibilidad del estado del sistema (Nielsen #1) · `Estilo` lenguaje del usuario (Clase 10)

**Borrar por swipe con revelación de la acción.**
La acción de borrar no ocupa espacio en reposo: se **revela al arrastrar** la fila (hacia cualquiera
de los dos lados), patrón estándar de listas en iOS/Android. Mantiene la lista limpia y evita toques
accidentales sobre un botón siempre visible.
`Patrón` Accesos rápidos (Clase 9 sl. 58) · `Ley` Jakob (patrón de plataforma, sl. 25) · `Heurística` Prevención de errores (#5) · Diseño estético y minimalista (#8)

**Deshacer tras borrar (snackbar undo).**
Eliminar es una acción **destructiva**; el snackbar "N eliminada · Deshacer" da una **red de
seguridad** inmediata para revertir un borrado accidental, sin un diálogo de confirmación que
interrumpa el flujo.
`Patrón` Notificaciones / toast (Clase 9 sl. 63) · `Heurística` Control y libertad del usuario (#3) · Ayuda a reponerse de errores (#9) · `Regla` (nueva) **R17**

**Estado vacío con cierre positivo.**
En vez de una pantalla en blanco, **✓ + "¡Ninguna novedad por ahora!"** comunica que no hay nada
pendiente (no que algo falló).
`Heurística` Visibilidad del estado (#1) · Diseño estético y minimalista (#8) · `Estilo` tono cálido (Clase 10)

### Tabla resumen — leyes / patrones / heurísticas

| Aplicación en Notificaciones | Ley / patrón / heurística |
|---|---|
| Filas + divisor, escaneo por título | **Patrón Listas + lectura F** (Clase 9) |
| Tiempo relativo en cada aviso | **Visibilidad del estado** (Nielsen #1) |
| Swipe revela el tacho | **Accesos rápidos** (Clase 9) + **Jakob** |
| Snackbar "Deshacer" tras borrar | **Control y libertad** (#3) + **reponerse de errores** (#9) |
| Estado vacío con ✓ | **Diseño estético y minimalista** (#8) |

### Accesibilidad (WCAG 2.2 AA) en Notificaciones

- **Contraste:** título `text/primary`, cuerpo `text/secondary`, tiempo `text/disabled`; tacho =
  blanco sobre `action/default` (AA); snackbar = blanco sobre marrón oscuro (AA).
- **No depender solo del color (1.4.1):** snackbar y tacho combinan color **+ texto/ícono**.
- **Área táctil (2.5.8):** filas altas y botón de tacho con objetivo ≥44.
- **Mejoras de accesibilidad pendientes:** borrar solo por swipe (falta alternativa sin gesto) y
  estado leído/no leído sin indicador → registradas como **M1** y **M2** en
  [`mejoras-pendientes.md`](mejoras-pendientes.md#notificaciones-2925478).

> **Material para la evaluación heurística (bloque 5):** ✅ cumple #1 (tiempos + confirmación de
> borrado), #3 (Deshacer), #5 (swipe deliberado + undo). El destino **Home** resaltado en la tab bar
> es **intencional** (Notificaciones es un sub-flujo del Home). Hallazgos a registrar para la
> evaluación: M1 (alternativa no-gestual al borrado) y M2 (leído/no leído).

---

## Pantallas pendientes

A documentar a medida que se diseñen: **Planificación · Lista de compras**.
Cada una seguirá esta misma estructura (concepto rector → estructura → decisiones con chips → tabla
resumen → accesibilidad).
