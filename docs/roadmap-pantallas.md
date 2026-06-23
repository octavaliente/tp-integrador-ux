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
| 2 | **Recetas** (lista / guardadas) | Recetas | ⬜ | — |
| 3 | **Detalle de receta** | Recetas | ⬜ | — |
| 4 | **Buscar recetas** | Recetas | ⬜ | — |
| 5 | **Planificación** | Planificación | ⬜ | — |
| 6 | **Lista de compras** | Planificación | ⬜ | — |
| 7 | **Ingredientes** (ver / ingresar) | Ingredientes | ⬜ | — |
| 8 | **Perfil** (+ 4 subpantallas) | Perfil | ✅ | `112:166` |
| 9 | **Notificaciones** | (raíz) | ⬜ | — |
| 10 | Pantalla **"????"** del sitemap | (raíz) | 🔵 | — |

> Orden sugerido de diseño (por reutilización y dependencias): **Recetas → Detalle → Buscar →
> Planificación / Lista de compras → Ingredientes → Perfil → Notificaciones.** Recetas y los
> feeds reutilizan la *Card de receta · compacta* (`55:16`) y la grilla de 2 columnas ya creadas.

---

## Componentes/assets que probablemente haya que sumar al UI Kit

A crear/validar a medida que aparezcan (registrar en `contexto-figma.md`):

- [ ] **Card de receta · ancha** (lista de 1 columna con más metadatos).
- [ ] **Ítem de lista de compras** (checkbox + cantidad + ingrediente + precio).
- [ ] **Stepper / control de porciones** (− 4 +).
- [ ] **Fila de paso de preparación** (número + texto, estado completado).
- [ ] **Tabla / fila de info nutricional** (nutriente + valor).
- [ ] **Toggle / switch** y **selector segmentado** (filtros, restricciones del perfil).
- [ ] **Ítem de notificación** (ícono + texto + tiempo + estado leído/no leído).
- [ ] **Campo de búsqueda con resultados** y **chips de filtro activos**.
- [ ] **Estados vacíos** (sin ingredientes, sin recetas guardadas, sin notificaciones).
- [ ] **Encabezado de pantalla interna** (back + título + acción contextual).

---

# Pantallas

## 1. Home ✅ — `56:2`

- [x] Validar estructura en chat
- [x] Construir en Figma
- [x] Documentar justificación → [`justificaciones-ux.md` § Home](justificaciones-ux.md#pantalla-home-562)
- [x] Registrar node ID

Sugerencias de recetas según los ingredientes del usuario + atajos. **Terminada y validada.**

---

## 2. Recetas (lista / guardadas) ⬜

Pestaña "Recetas" de la tab bar. Cubre el feed principal de recetas y la sección de
**recetas guardadas** e **historial cocinado**.

- [ ] Validar estructura en chat
- [ ] Construir en Figma
- [ ] Documentar justificación
- [ ] Registrar node ID

**Alcance (del sitemap):**
- [ ] Listado / grilla de recetas (reutiliza card compacta `55:16` + grilla 2 col).
- [ ] **Recetas guardadas** (filtro/sección de favoritos).
- [ ] **Historial cocinado** (recetas ya preparadas).
- [ ] Acceso a **Guardar receta** (acción de bookmark, ya en la card).
- [ ] Acceso a **Buscar recetas** (→ pantalla 4) y a **Detalle** (→ pantalla 3).
- [ ] Entrada a **Añadir receta a planificación** (acción contextual).

**A decidir en validación:** ¿tabs internos (Todas / Guardadas / Historial) o filtros? ¿estado vacío?

---

## 3. Detalle de receta ⬜

Vista de una receta abierta. Es la pantalla más densa del sitemap.

- [ ] Validar estructura en chat
- [ ] Construir en Figma
- [ ] Documentar justificación
- [ ] Registrar node ID

**Alcance (del sitemap):**
- [ ] **Foto del plato** (hero).
- [ ] **Dificultad y tiempo** de cocción.
- [ ] **Precio estimado**.
- [ ] **Ajustar porciones** (stepper que recalcula cantidades).
- [ ] **Pasos de preparación** (lista numerada).
- [ ] **Info nutricional** a nivel receta **y** a nivel ingrediente.
- [ ] **Reemplazar ingrediente** (sustitución).
- [ ] Acción **Guardar receta**.
- [ ] Acción **Añadir a planificación**.

**A decidir en validación:** ¿scroll largo único o secciones colapsables / tabs (Ingredientes / Pasos / Nutrición)? ¿cómo se muestra la info nutricional por ingrediente (modal, expandible)?

---

## 4. Buscar recetas ⬜

- [ ] Validar estructura en chat
- [ ] Construir en Figma
- [ ] Documentar justificación
- [ ] Registrar node ID

**Alcance (del sitemap):**
- [ ] Búsqueda **por ingredientes** (los que el usuario tiene).
- [ ] Búsqueda **por filtros**: cantidad (de personas/porciones), restricciones.
- [ ] Estado de resultados (reutiliza grilla/card) y estado vacío / sin resultados.

**A decidir en validación:** ¿búsqueda en pantalla propia o overlay sobre Recetas? ¿chips de filtro activos? relación con el buscador sticky del Home.

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

## 7. Ingredientes (ver / ingresar) ⬜

Pestaña "Ingredientes" de la tab bar. Cubre **ver** la despensa e **ingresar** nuevos.

- [ ] Validar estructura en chat
- [ ] Construir en Figma
- [ ] Documentar justificación
- [ ] Registrar node ID

**Alcance (del sitemap):**
- [ ] **Ver ingredientes** (despensa actual).
- [ ] **Ingresar ingredientes** por 4 métodos:
  - [ ] **Foto del ticket**
  - [ ] **Código de barras**
  - [ ] **Manual**
  - [ ] **Por voz**
- [ ] Estado vacío (sin ingredientes cargados).

**A decidir en validación:** ¿los 4 métodos en una hoja de selección (bottom sheet) o pantallas separadas? Relación con los atajos "Cargar ingrediente / Cargar ticket" del Home.

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

## 9. Notificaciones ⬜

Accesible desde la campana del Home.

- [ ] Validar estructura en chat
- [ ] Construir en Figma
- [ ] Documentar justificación
- [ ] Registrar node ID

**Alcance:**
- [ ] Lista de notificaciones (leídas / no leídas).
- [ ] Tipos: sugerencias, recordatorios de planificación, vencimiento de ingredientes (a definir).
- [ ] Estado vacío.

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
