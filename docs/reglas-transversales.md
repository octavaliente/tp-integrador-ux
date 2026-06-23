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
  - Las pestañas raíz (Home, Recetas, Ingredientes, Planificación, Perfil) **no** llevan volver.

- **R2 — Tab bar siempre presente y con estado activo claro.** 5 destinos fijos en el
  orden **Home · Recetas · Ingredientes · Planificación · Perfil**. El ítem activo se
  distingue por **color `action/default` (calabaza 600)** en ícono **y** etiqueta; los
  inactivos en `text/secondary`. La etiqueta de texto está siempre visible (no depender
  solo del color → WCAG 1.4.1).

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
