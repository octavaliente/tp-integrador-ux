# Roadmap de pantallas — RecetApp (Fase 4)

> Documento vivo. Lista **todas las vistas a diseñar** según el sitemap, con su
> estado y los pasos del flujo de trabajo acordado. Se va completando a medida que
> el agente avanza: al terminar una pantalla, marcar sus casillas, registrar el
> **node ID** de Figma y enlazar su justificación.
>
> - Sitemap de origen: [`../Sitemap - App recetas.jpg`](../Sitemap%20-%20App%20recetas.jpg)
> - Contexto completo: [`../RecetApp - Handoff y contexto.md`](../RecetApp%20-%20Handoff%20y%20contexto.md)
> - node IDs y estado: [`contexto-figma.md`](contexto-figma.md)
> - Justificación UX por pantalla: [`justificaciones-ux.md`](justificaciones-ux.md)

---

## Cómo se usa este documento

**Flujo por pantalla** (método acordado, no saltear pasos):

1. **Validar estructura en el chat** con el usuario (secciones, jerarquía, patrones).
2. **Construir en Figma** sobre la plantilla iPhone 15 (393×852), reutilizando el UI Kit y los tokens.
3. **Documentar la justificación** (leyes/patrones UX + accesibilidad WCAG AA) en [`justificaciones-ux.md`](justificaciones-ux.md).
4. **Registrar el node ID** en [`contexto-figma.md`](contexto-figma.md) y en la tabla de abajo.

**Leyenda de estado:**

- ✅ Terminada (validada + en Figma + documentada)
- 🟡 En curso
- ⬜ Pendiente
- 🔵 A definir (requiere decisión del usuario antes de diseñar)

Recordatorios de entorno: **rate limit del plan** → agrupar llamadas en Figma; cargar la skill
`figma-use` antes de cada `use_figma`; mantener todo en **WCAG AA**.

---

## Resumen de avance

| # | Pantalla / vista | Sección sitemap | Estado | node ID |
|---|---|---|---|---|
| 1 | **Home** | (raíz) | ✅ | `56:2` |
| 2 | **Recetas** (Buscar / Mis recetas / Historial) | Recetas | ✅ | `205:1472` |
| 3 | **Detalle de receta** | Recetas | ✅ | `210:2007` |
| 4 | **Buscar recetas** (+ Filtros: 2 modos) | Recetas | ✅ | `205:1472` · `208:1976` · `363:16472` |
| 5 | **Planificación** | Planificación | ⬜ | — |
| 6 | **Lista de compras** | Planificación | ⬜ | — |
| 7 | **Ingredientes** (ver / ingresar) | Ingredientes | ✅ | `163:605` |
| 8 | **Perfil** (+ 4 subpantallas) | Perfil | ✅ | `112:166` |
| 9 | **Notificaciones** | (raíz) | ✅ | `292:5478` |
| 10 | Pantalla **"????"** del sitemap | (raíz) | 🔵 | — |

> Orden sugerido de diseño (por reutilización y dependencias): **Recetas → Detalle → Buscar →
> Planificación / Lista de compras → Ingredientes → Perfil → Notificaciones.** Recetas y los
> feeds reutilizan la *Card de receta · compacta* (`55:16`) y la grilla de 2 columnas ya creadas.

---

## Componentes/assets que probablemente haya que sumar al UI Kit

A crear/validar a medida que aparezcan (registrar en `contexto-figma.md`):

- [x] **Card de receta · ancha** (hero del Detalle) → `204:168` (prop Nombre).
- [ ] **Ítem de lista de compras** (checkbox + cantidad + ingrediente + precio).
- [x] **Stepper / control de cantidad** (− N +) → `159:120` (sirve también para porciones del Detalle).
- [x] **Fila de ingrediente** (set Vista/Edición: miniatura + nombre + cantidad/stepper + tacho) → `161:148`.
- [x] **Fila de paso de preparación** (número + texto) → inline en Detalle (acordeón Preparación).
- [x] **Fila de info nutricional** (nutriente + valor) → inline en Detalle (acordeón Nutrición).
- [x] **Segmented control** (2/3 opciones) → `203:185` / `202:199`. (Toggle/switch aún pendiente.)
- [x] **Acordeón** (sección colapsable: header título + chevron) → patrón inline en Detalle.
- [x] **icon/sustituir** (reemplazar ingrediente, flechas de intercambio) → `201:168`.
- [ ] **Ítem de notificación** (ícono + texto + tiempo + estado leído/no leído).
- [x] **Campo de búsqueda** → `159:133`. **Resultado de búsqueda** (fila de candidato `+`/`✓`, reutilizable en Carga manual / Filtros / Carga a lista) → `369:4231` (R18). (Chips de filtro activos en barra de resultados: pendientes.)
- [ ] **Estados vacíos** (sin ingredientes ✅ `166:801`; faltan sin recetas guardadas, sin notificaciones).
- [x] **Encabezado de pantalla interna** → reusa `123:27` (back + título); acción contextual ad-hoc (p. ej. "Limpiar" en Filtros).

---

# Pantallas

## 1. Home ✅ — `56:2`

- [x] Validar estructura en chat
- [x] Construir en Figma
- [x] Documentar justificación → [`justificaciones-ux.md` § Home](justificaciones-ux.md#pantalla-home-562)
- [x] Registrar node ID

Sugerencias de recetas según los ingredientes del usuario + atajos. **Terminada y validada.**

---

## 2. Recetas (Buscar / Mis recetas / Historial) ✅ — `205:1472`

Pestaña "Recetas" de la tab bar con **navegación interna por segmented control** (3 secciones).

- [x] Validar estructura en chat
- [x] Construir en Figma
- [x] Documentar justificación → [`justificaciones-ux.md` § Recetas](justificaciones-ux.md#pantalla-recetas-2051472--detalle-filtros)
- [x] Registrar node ID

**Alcance (del sitemap):**
- [x] **Buscar** (tab por defecto) = `205:1472` — buscador + botón de filtros + grilla 2 col con card compacta (`55:16`).
- [x] **Mis recetas** (guardadas) = `207:1656` — misma grilla 2 col.
- [x] **Historial cocinado** = `207:1888` — grilla 2 col agrupada por día (Hoy / Ayer / fecha).
- [x] **Guardar receta** (bookmark en la card).
- [x] Acceso a **Buscar recetas/Filtros** (→ pantalla 4) y a **Detalle** (→ pantalla 3).
- [ ] *Añadir receta a planificación* → vive en el Detalle (acción "Planificar" de la card hero).

**Decisiones validadas:** navegación interna por **segmented control** (no chips), feeds en **2 columnas**, Historial **por día**. La tab bar inferior se mantiene.

---

## 3. Detalle de receta ✅ — `210:2007`

Vista de una receta abierta. Subpantalla de **contenido** (push): mantiene la tab bar + encabezado de volver.

- [x] Validar estructura en chat
- [x] Construir en Figma
- [x] Documentar justificación → [`justificaciones-ux.md` § Recetas](justificaciones-ux.md#pantalla-recetas-2051472--detalle-filtros)
- [x] Registrar node ID

**Alcance (del sitemap):**
- [x] **Card hero ancha** (`204:168`): foto + nombre + tiempo/dificultad/precio + **Guardar** + **Añadir a planificación**.
- [x] **Ajustar porciones** (stepper en el acordeón Ingredientes).
- [x] **Pasos de preparación** (lista numerada, acordeón Preparación).
- [x] **Info nutricional por porción** (acordeón Nutrición).
- [x] **Reemplazar ingrediente** (ícono `sustituir` `201:168` por fila).
- [x] Acciones **Guardar receta** y **Añadir a planificación** (en la card hero).

**Decisiones validadas:** secciones densas en **acordeones** (default en uso: primera sección abierta, R16; en el archivo de Figma se muestran los 3 desplegados —frame extendido a 393×1193— para documentar todos los componentes). Info nutricional **por porción** (a nivel receta); la nutrición por ingrediente individual queda fuera de alcance por ahora.

---

## 4. Buscar recetas (+ Filtros: 2 modos) ✅ — `205:1472` · `208:1976` · `363:16472`

- [x] Validar estructura en chat
- [x] Construir en Figma
- [x] Documentar justificación → [`justificaciones-ux.md` § Recetas](justificaciones-ux.md#pantalla-recetas-2051472--detalle-filtros)
- [x] Registrar node ID

**Alcance (del sitemap):**
- [x] Buscador (tab **Buscar** de Recetas, `205:1472`) + **botón de filtros** con badge de filtros activos.
- [x] **Filtros** (subpantalla modal, sin tab bar) · segmented de **modo**: **Por ingredientes / Por características**.
  - [x] Modo **Por características** (`208:1976`): grupos de chips (Tiempo, Dificultad, Restricciones), **Porciones** con stepper, botón fijo "Aplicar filtros · N recetas".
  - [x] Modo **Por ingredientes** (`363:16472`): campo de búsqueda + grupo **"Tu despensa"** (chips multi-select) + grupo **"Otros ingredientes"** (chips que se suman por búsqueda). **Búsqueda activa** (overlay con lista de resultados, componente `369:4231`) = `374:11270`.
- [x] Resultados reutilizan grilla 2 col + card compacta. (Estado vacío / sin resultados: pendiente.)

**Decisiones validadas:** los filtros viven en una **subpantalla propia**; selección con **chips sin ✓** (relleno calabaza) dentro de grupos rotulados; **cada modo muestra un set distinto** (atributos vs. ingredientes). **Relabel:** "Por filtros" → "Por características" (nombra por el *input* de cada modo). En "Por ingredientes" se **descartó** el control de *Coincidencia* (no aportaba como filtro) y se usa **"Otros ingredientes"** alimentado por la **búsqueda de ingredientes reutilizable** (componente `369:4231`, R18). Pendiente: chips de filtros activos en la barra de resultados; estado vacío de despensa y de resultados sin match (ver `mejoras-pendientes.md`).

---

## 5. Planificación ⬜

Pestaña "Planificación" de la tab bar.

- [ ] Validar estructura en chat
- [ ] Construir en Figma
- [ ] Documentar justificación
- [ ] Registrar node ID

**Alcance (del sitemap):**
- [ ] **Planificación semanal** (calendario / agenda de comidas).
- [ ] **Sugerencias de recetas** para planificar.
- [ ] Acceso a **Lista de compras** (→ pantalla 6).

**A decidir en validación:** ¿vista semanal por día o por comida (desayuno/almuerzo/cena)? ¿cómo se asigna una receta a un slot?

---

## 6. Lista de compras ⬜

Sub-vista de Planificación; también accesible desde el atajo del Home.

- [ ] Validar estructura en chat
- [ ] Construir en Figma
- [ ] Documentar justificación
- [ ] Registrar node ID

**Alcance:**
- [ ] Lista de ingredientes a comprar (checkbox + cantidad + precio).
- [ ] Agrupación (por receta / por categoría de góndola) — a definir.
- [ ] Total estimado.
- [ ] Estado vacío.

---

## 7. Ingredientes (ver / ingresar) ✅ — `163:605`

Pestaña "Ingredientes" de la tab bar. Cubre **ver** la despensa e **ingresar** nuevos.

- [x] Validar estructura en chat
- [x] Construir en Figma
- [x] Documentar justificación → [`justificaciones-ux.md` § Ingredientes](justificaciones-ux.md#pantalla-ingredientes-163605--flujo-de-carga)
- [x] Registrar node ID

**Alcance (del sitemap):**
- [x] **Ver ingredientes** (despensa actual) → lista con miniatura + cantidad (`163:605`); **modo edición** con stepper + tacho (`165:663`); **estado vacío** (`166:801`).
- [x] **Ingresar ingredientes** por 4 métodos:
  - [x] **Manual** → `167:847` (lista de resultados con el componente reutilizable **Resultado de búsqueda** `369:4231`, R18)
  - [x] **Por voz** → `168:888`
  - [x] **Foto del ticket** → `169:898` (misma pantalla que código, overlay variable)
  - [x] **Código de barras** → variante de `169:898`
- [x] **Revisar ingredientes** (vista previa de confirmación, convergencia voz/ticket/código) → `169:1050`.
- [x] Estado vacío (sin ingredientes cargados) → `166:801`.

**Decisiones validadas:** los 4 métodos como **accesos directos** arriba (espejo de los atajos
del Home, redundancia intencional); **modo edición explícito** (Editar → Listo, auto-guarda);
voz/ticket/código **convergen en una Vista previa** editable, manual va directo; **una sola
pantalla de cámara** para ticket y código; quitar ingrediente con **ícono de tacho**.

**Reglas transversales que surgieron acá** (ver [`reglas-transversales.md`](reglas-transversales.md)):
R11 encabezado de pestaña raíz, R12 captura automática → vista previa, R13 edición de listas por modo explícito.

---

## 8. Perfil ✅ — `112:166`

Pestaña "Perfil" de la tab bar. Datos que personalizan las sugerencias.

- [x] Validar estructura en chat
- [x] Construir en Figma
- [x] Documentar justificación → [`justificaciones-ux.md` § Perfil](justificaciones-ux.md#pantalla-perfil-112166--subpantallas)
- [x] Registrar node ID

**Decisiones validadas:** pantalla **única de ajustes en lista** (no onboarding), **sin
cards** (filas + divisores), agrupada en *Sobre mí* / *Mi hogar*. Identidad solo lectura;
alcance ceñido a los 6 campos del sitemap.

**Alcance (del sitemap):**
- [x] **Peso y altura** → input ×2 con unidad (`112:245`)
- [x] **Objetivo nutricional** → selección única (`112:221`)
- [x] **Restricciones personales** → selección múltiple (`112:197`)
- [x] **Cantidad de personas en casa** → input (`112:269`)
- [x] **Tipo de actividad deportiva** → reutiliza plantilla de selección única (clonar de `112:221` en Fase 5)
- [x] **Restricciones familiares** → reutiliza plantilla de selección múltiple (clonar de `112:197` en Fase 5)

**Reglas transversales que surgieron acá** (ver [`reglas-transversales.md`](reglas-transversales.md)):
R1 encabezado de subpantalla fijo (back + título), R3 gutter 16, R4 paneles inset,
R5 listas con filas/divisores (no cards), R6 valor visible + vacío en `text/disabled`,
R7 auto-guardado sin "Guardar".

---

## 9. Notificaciones ✅ — `292:5478`

Accesible desde la campana del Home (push · mantiene tab bar, Home activo).

- [x] Validar estructura en chat
- [x] Construir en Figma
- [x] Documentar justificación → [`justificaciones-ux.md` § Notificaciones](justificaciones-ux.md#pantalla-notificaciones-2925478--estados)
- [x] Registrar node ID

**Alcance (del sitemap):**
- [x] Lista de notificaciones (filas + divisor + tiempo relativo) = `292:5478`.
- [x] Tipos: recordatorio de compra, recordatorio de planificación, sugerencia de recetas.
- [x] **Estado vacío** (✓ + "¡Ninguna novedad por ahora!") = `303:10452`.
- [x] **Borrar** por swipe (`303:8407` izq / `303:10170` der) + **Deshacer** (snackbar, `303:10647`).
- [ ] Leído / no leído → pendiente (**M2** en [`mejoras-pendientes.md`](mejoras-pendientes.md#notificaciones-2925478)).

**Regla transversal nueva:** R17 (acciones destructivas con Deshacer). Mejora de accesibilidad
pendiente: **M1** (alternativa no-gestual al borrado).

---

## 10. Pantalla "????" del sitemap 🔵

En el sitemap hay un **nodo gris sin nombre** que apunta hacia Home. Probablemente sea un
**Splash / Onboarding / Login** previo a la app, o un placeholder que quedó sin definir.

- [ ] **Definir con el usuario** qué es este nodo (¿splash? ¿onboarding? ¿descartar?).
- [ ] Validar estructura en chat
- [ ] Construir en Figma
- [ ] Documentar justificación
- [ ] Registrar node ID

---

## Fuera del diseño de pantallas (fases siguientes)

Recordatorio del roadmap general (no son pantallas, pero cierran la Fase 4 y abren las próximas):

- [ ] **Fase 5** — repaso/maquetado final de todas las pantallas en Figma + chequeo AA con **STARK**.
- [ ] **Fase 6** — evaluación heurística (Nielsen) y ajustes.
- [ ] **Fase 7** — documento de fundamentación.
- [ ] **Fase 8** — presentación final (deck 5 bloques, 2/7/2026).
