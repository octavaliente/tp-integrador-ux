# Mejoras pendientes — por grupo de vistas

> Backlog de **ajustes y mejoras** detectados durante la fundamentación, a resolver más adelante
> en Figma. Organizado por **grupo de vistas**. Cada ítem conserva su **fundamento** (criterio WCAG /
> heurística / ley) para no perder el porqué cuando se retome.
>
> Relacionado: fichas en [`justificaciones-ux.md`](justificaciones-ux.md) · reglas en
> [`reglas-transversales.md`](reglas-transversales.md) · estado en [`roadmap-pantallas.md`](roadmap-pantallas.md).
>
> Estado: ⬜ pendiente · 🟡 en curso · ✅ resuelto.

---

## Notificaciones (`292:5478`)

- ⬜ **M1 · Alternativa no-gestual para borrar.**
  Hoy borrar un aviso **solo** se logra por *swipe*. WCAG 2.2 exige una alternativa con un solo
  puntero. Propuesta: que **tocar la fila** abra un detalle con opción de borrar, o un **modo
  "gestionar"** con tachos visibles. *(Relacionado: el snackbar "Deshacer" debería seguir accesible
  un tiempo suficiente — WCAG 2.2.1 Tiempo ajustable.)*
  → `A11y` 2.5.1 Gestos del puntero (A) · 2.5.7 Movimientos de arrastre (AA) · `Regla` R17.
  **Prioridad: alta** (bloquea AA, que la consigna exige en todas las pantallas).

- ⬜ **M2 · Estado leído / no leído.**
  No hay distinción visible entre avisos leídos y no leídos (el roadmap la preveía). Si se suma,
  usar indicador **no solo color** (p. ej. punto + negrita en el no leído).
  → `A11y` 1.4.1 Uso del color · `Ley` Zeigarnik (tareas pendientes) · `Heurística` Visibilidad del estado (#1).
  **Prioridad: media.**

---

## Ingredientes (`163:605`)

- ⬜ **M3 · Consistencia de los tiles de carga.**
  La vista principal muestra *Manual · Ticket · Barras · **Atajo*** (el 4.º es el micrófono, pero
  etiquetado "Atajo"), mientras el estado vacío muestra *Manual · **Por voz** · Ticket · Barras*:
  difieren la **etiqueta** del método de voz y el **orden** de los tiles. Unificar a **"Por voz"**
  (no "Atajo", que confunde con un acceso directo) y un único orden en todas las vistas (principal,
  edición, vacío).
  → `Heurística` Consistencia y estándares (#4) · `A11y` 3.2.4 Identificación consistente.
  **Prioridad: media.**

---

## Recetas (`205:1472`)

- ⬜ **M4 · Estados vacíos / sin resultados.**
  Faltan los estados de **Buscar sin resultados**, **sin recetas guardadas** e **historial vacío**.
  Cada uno con ícono + mensaje y, si aplica, CTA — en línea con el estado vacío de Ingredientes.
  → `Heurística` Visibilidad del estado (#1) · Diseño estético y minimalista (#8).
  **Prioridad: media.**

- ⬜ **M5 · Filtros "Por ingredientes" con despensa vacía.**
  El modo **Por ingredientes** (`363:16472`) asume que hay ingredientes en la despensa. Falta el estado
  para **despensa vacía**: mensaje + CTA a cargar ingredientes (enlazar con el estado vacío de
  Ingredientes `166:801`), en vez de un grupo "Tu despensa" sin chips.
  → `Heurística` Visibilidad del estado (#1) · Ayuda y documentación / salida clara (#10).
  **Prioridad: media.**

- ⬜ **M6 · Chips single vs multi sin distinción visual.**
  En Filtros conviven chips **multi-select** (Restricciones, Tu despensa, Otros ingredientes) y
  **single-select** (Tiempo, Dificultad) con el **mismo aspecto**. Evaluar una pista de affordance
  (p. ej. microcopy "Elegí una" o forma) para no sugerir multi donde es single.
  → `A11y` 1.4.1 (no solo color) · `Heurística` Consistencia y estándares (#4).
  **Prioridad: baja.**

- ⬜ **M7 · Búsqueda de ingredientes sin resultados.**
  Falta el estado **"sin coincidencias"** de la búsqueda reutilizable (componente `369:4231`): cuando lo
  tipeado no matchea ningún ingrediente del catálogo, mostrar mensaje + opción de "agregar de todos
  modos" si corresponde. Aplica a Carga manual, Filtros "Por ingredientes" y Carga a lista.
  → `Heurística` Visibilidad del estado (#1) · Ayuda a reponerse de errores (#9) · `Regla` R18.
  **Prioridad: media.**

---

## Sistema Visual / tokens

- ⬜ **M5 · Sincronizar los valores finales de color.**
  La **paleta definitiva de 6 roles** (texto primario `#2B1B12`, secundario `#6E4631`, terciario/
  placeholder `#7D6657`, borde/divisor `#9C8674`) debe actualizarse en las **variables de Figma** y en
  `recetapp_tokens.json`, que aún tienen los valores previos (`#2E1E12`, `#5C4A3A`, `#A69D95`,
  `#C7C1BC`). El fondo `#FDF4E8` y el acento `#AF5012` no cambian.
  → consistencia tokens ↔ pantallas (Clase 10). **Prioridad: alta** (afecta todo el archivo).

<!-- A medida que surjan, sumar grupos: Home · Perfil · Planificación · Lista de compras -->
