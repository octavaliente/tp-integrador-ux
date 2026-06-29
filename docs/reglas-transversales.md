# Reglas transversales — RecetApp

> Reglas de diseño/UX que aplican a **toda la app**, no a una pantalla puntual.
> Se definen a medida que aparecen y deben respetarse en cada vista nueva.
> Contexto: [`../CLAUDE.md`](../CLAUDE.md) · justificaciones por pantalla: [`justificaciones-ux.md`](justificaciones-ux.md).

---

## Navegación

- **R1 — Encabezado de subpantalla.** Toda subpantalla (un nivel por debajo de una
  pestaña raíz) lleva un **encabezado con botón de volver + título**.
  - Botón volver: círculo de **32×32**, borde `border/default`, ícono `‹`.
  - Título: estilo **`Texto/H3`** (Poppins Medium 17), color `text/primary`, *sentence case*.
  - El bloque encabezado tiene **alto fijo 52 px** y es **idéntico en todas las vistas**
    (consistencia → *Jakob's Law*).
  - Las pestañas raíz (Home, Recetas, Planificación, Ingredientes, Perfil) **no** llevan volver.

- **R2 — Tab bar siempre presente y con estado activo claro.** 5 destinos fijos en el
  orden **Home · Recetas · Planificación · Ingredientes · Perfil**. El ítem activo se
  distingue por **color `action/default` (calabaza 600)** en ícono **y** etiqueta; los
  inactivos en `text/secondary`. La etiqueta de texto está siempre visible (no depender
  solo del color → WCAG 1.4.1).
  > **Tab bar = componente único** (`179:446`, UI Kit, prop *Activo*), instanciado en todas las
  > vistas raíz (Home, Perfil, Ingredientes) → consistencia garantizada, un solo lugar para editar.
  > Orden **decidido y definitivo** (el del Home ya construido). Si en el futuro hiciera falta
  > reordenar, se edita solo el componente y se propaga a todas las vistas.

- **R11 — Encabezado de pestaña raíz: título + subtítulo.** Las pestañas raíz (las que **no**
  llevan volver) abren con un **bloque de título**: título en **`Texto/H1`** (`text/primary`) +
  subtítulo opcional en **`Texto/Body M`** (`text/secondary`), alineados a la izquierda dentro del
  gutter de 16. Da contexto a la vista sin recurrir a un header cargado. (Home es la excepción:
  usa saludo personalizado + campana de notificaciones.)
  → *Jakob's Law* · jerarquía visual.

- **R14 — Navegación interna por *segmented control*.** El cambio entre **secciones del mismo nivel**
  dentro de una pestaña raíz (p. ej. Recetas: Buscar / Mis recetas / Historial) y el cambio de **modo**
  (p. ej. Filtros: Por ingredientes / Por filtros) se resuelven con un **segmented control** (componente
  `202:199` / `203:185`): contenedor que agrupa **2–3 opciones**, segmento activo en `bg/surface`
  **elevado**, inactivos en `text/secondary`. Es el patrón *Pestañas* (Clase 9) materializado como
  *segmented* (iOS HIG) / *choice chips* (Material). **Es distinto de los chips de filtro** —que
  seleccionan **valores** (relleno calabaza, sin ✓, multi-select, dentro de grupos)— para no confundir
  *navegar* con *filtrar*. → *Jakob's Law* · *Consistency & standards* (Nielsen #4) · *Hick's Law*.
  - **Cuando el segmented cambia de *modo*** (no de sección), **cada modo muestra su propio set de
    controles** (no se acumulan) y los modos se **nombran por su input**, no por la pantalla que los
    contiene. Ej.: en **Filtros**, "**Por ingredientes**" (partís de tu despensa) / "**Por
    características**" (partís de atributos de la receta) — *no* "Por filtros", que era circular.
    → *Coincidencia con el mundo real* (Nielsen #2) · *Hick* (menos opciones por pantalla).

- **R15 — Subpantallas: contenido (push) vs edición/modal.** Según su rol se presentan distinto:
  **contenido** al que se llega navegando dentro de una pestaña (p. ej. Detalle de receta) → *push*,
  **mantiene la tab bar** + encabezado de volver (estándar iOS/Material); **edición / captura /
  configuración** (p. ej. carga de Ingredientes, Filtros, ajustes de Perfil) → *modal* a pantalla
  completa, **sin tab bar**, con volver y acción explícita. → *Jakob's Law* · *User control & freedom*
  (Nielsen #3).

- **R16 — Secciones densas en acordeón.** Las pantallas con mucha información (p. ej. Detalle de receta)
  agrupan su contenido en **acordeones** (header con título + chevron + cuerpo colapsable). Por defecto
  se abre la **primera sección** (la más usada) y el resto arranca colapsado. → *Menú acordeón* (Clase 9)
  · *Aesthetic & minimalist design* (Nielsen #8).

## Layout y superficies

- **R3 — Gutter global de 16 px.** Todo el contenido respeta un margen lateral de
  **16 px** (coincide con `grid/margin`). Nada va pegado al borde de la pantalla.

- **R4 — Superficies como paneles "inset", nunca a sangre.** Los bloques de contenido
  blanco (`bg/surface`) se muestran como **paneles con margen lateral 16 + esquinas
  redondeadas `radius/lg` (16)** sobre el fondo `bg/page` (crema). Evita el corte abrupto
  crema↔blanco de borde a borde.

- **R5 — Listas/ajustes con filas + divisores, no cards.** Para listas de navegación o
  configuración se usan **filas con divisor** (`border/default`), agrupadas bajo
  **encabezados de sección** en mayúsculas (`Texto/Label`, `text/secondary`). Reservar las
  cards para objetos de contenido independientes (p. ej. recetas). Regla heredada de
  CLAUDE.md: *evitar uso excesivo de Cards*.

## Estados y datos

- **R6 — Valor actual visible sin entrar.** En las filas de ajuste se muestra el valor
  vigente como subtítulo (→ *recognition over recall*). Si el dato está vacío, se rotula
  ("Ninguna") en **`text/disabled`** para diferenciarlo de un valor cargado.

- **R7 — Auto-guardado en ajustes.** Las subpantallas de edición **guardan al volver**
  (patrón estándar iOS/Material); no llevan botón "Guardar". Excepción: formularios de
  varios campos juntos pueden usar acción explícita si hiciera falta (no es el caso de
  Perfil, donde Peso y altura también auto-guarda).

## Accesibilidad (transversal)

- **R8 — Área táctil ≥ 44×44 px** en todo control interactivo (filas, volver, ítems de
  tab bar, checks/radios y su fila contenedora).
- **R9 — Contraste WCAG AA** (4.5:1 texto normal). Acento/acción = **calabaza 600
  `#AF5012`** (el 500 no pasa). Verificación final con **STARK** en Fase 5.
- **R10 — No depender solo del color** para comunicar estado: combinar color con
  ícono/forma/etiqueta (tab activa, checks de selección, etc.).

## Flujos

- **R12 — Captura automática → Vista previa de confirmación.** Todo flujo que **infiere datos de
  una fuente ruidosa** (voz, foto de ticket, código de barras) termina en una **Vista previa
  editable**: el usuario revisa lo detectado, ajusta cantidades, quita ítems y recién entonces
  **Confirma** o **Descarta**. La carga **manual** (explícita, ítem por ítem) no la requiere: su
  botón "Agregar" confirma directo.
  → *Error prevention* (Nielsen #5) · *Visibility of system status* (#1) · *User control & freedom* (#3).

- **R13 — Edición de listas por modo explícito.** En listas de objetos editables (p. ej. *Mis
  ingredientes*), la vista normal es **solo lectura** (cantidad como texto); un control **Editar**
  activa el **modo edición** (aparecen stepper − / + y el **tacho** para quitar) y pasa a **Listo**,
  que auto-guarda (→ R7). Evita cambios accidentales y baja el ruido visual en reposo.
  → *Error prevention* (Nielsen #5) · *Aesthetic & minimalist design* (#8) · *Jakob's Law* (patrón iOS/Material).

- **R17 — Acciones destructivas con red de seguridad (Deshacer).** Borrar/eliminar un ítem se
  confirma con un **snackbar "Deshacer"** (undo inmediato) en lugar de un diálogo bloqueante —salvo
  acciones de altísimo costo o irreversibles, que sí piden confirmación explícita—. Además, el
  borrado debe tener una **vía no-gestual** (no depender solo de *swipe*) para cumplir WCAG.
  → *Control y libertad del usuario* (Nielsen #3) · *Ayuda a reponerse de errores* (#9) ·
  *Reversibilidad* · WCAG 2.5.1 / 2.5.7. (Surgió en **Notificaciones**.)

- **R18 — Búsqueda de ingredientes: un único patrón reutilizable.** Toda búsqueda de ingredientes
  (Carga manual, Filtros "Por ingredientes", Carga de ingrediente a la lista de Planificación) usa el
  **mismo campo de búsqueda** (`159:133`) y la **misma lista de resultados** (componente **Resultado de
  búsqueda** `369:4231`: fila con miniatura + nombre + acción circular **`+` (agregar) / `✓`
  (seleccionado)**, estado por **forma + color**). Lo que cambia es **qué pasa al elegir**, según el
  contexto: en un **filtro** el ítem se suma a una lista de chips (multi, sin cantidad); en una **carga**
  se elige uno y se define **cantidad** (stepper) antes de confirmar. Cuando la búsqueda convive con otro
  contenido (Filtros), se muestra como **overlay** (reemplaza los grupos mientras hay texto).
  → *Consistencia y estándares* (Nielsen #4) · *Reconocimiento antes que recuerdo* (#6) · *Jakob's Law* ·
  WCAG 1.4.1 (no solo color). (Surgió en **Filtros · Por ingredientes** / **Carga manual**.)
