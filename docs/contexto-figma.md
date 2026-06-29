# Contexto de Figma — node IDs y estado actual

> Copia de la memoria de trabajo del proyecto. Sirve para que todo el equipo
> arranque con los mismos identificadores de Figma y el mismo estado de avance.
> El contexto completo (sistema de diseño, sitemap, reglas, roadmap) está en
> [`../RecetApp - Handoff y contexto.md`](../RecetApp%20-%20Handoff%20y%20contexto.md).

## Archivo de Figma

- **fileKey:** `xm1jJVWebfvCmj0Yeb7rC3`
- **Cuenta:** `ovaliente@frba.utn.edu.ar` (tier *student*)
- **Páginas:** Portada `0:1` · Foundations `15:2` · UI Kit `15:3` · Pantallas `15:4`

## Estado actual (Fase 4)

Primera pantalla terminada: **Home** = nodo `56:2` (página Pantallas).

Estructura validada: header (saludo + campana con badge), fila de 4 atajos
(Cargar ingrediente/ticket, Recetas guardadas, Lista de compras), buscador
sticky, "Sugerencias para ti" en grilla de 2 columnas con scroll infinito,
tab bar de 5 destinos (Home/Recetas/Planificación/Ingredientes/Perfil).

## Pantallas terminadas

- **Home** = `56:2`.
- **Perfil** = `112:166` (principal) + subpantallas:
  - Restricciones personales (multi-select) = `112:197`
  - Objetivo nutricional (single-select) = `112:221`
  - Peso y altura (inputs) = `112:245`
  - Personas en casa (input) = `112:269`
  - *Actividad deportiva* y *Restricciones familiares* aún no construidas: reutilizan las
    plantillas single/multi-select (clonar de `112:221` / `112:197`).
- **Ingredientes** = `163:605` (vista principal · pestaña raíz) + variantes y flujo de carga:
  - Ingredientes · **modo edición** = `165:663` (filas con tacho + stepper; "Listo" auto-guarda)
  - Ingredientes · **estado vacío** = `166:801`
  - **Carga manual** (subpantalla) = `167:847` — lista de resultados ahora con instancias del componente **Resultado de búsqueda** `369:4231` (misma búsqueda que Filtros/Planificación).
  - **Carga por voz** (subpantalla) = `168:888`
  - **Foto del ticket** = `169:898` y **Código de barras** = `182:1372` — mismo visor de cámara; cambian el marco-guía y el título (antes documentado como una sola pantalla con overlay variable).
  - **Revisar ingredientes** (vista previa · convergencia voz/ticket/código) = `169:1050`
- **Recetas** = `205:1472` (pestaña raíz · navegación interna por **segmented control**) + secciones y flujo:
  - Recetas · **Mis recetas** (guardadas) = `207:1656`
  - Recetas · **Historial** (cocinado, agrupado por día · **lista de filas, no grilla** — patrón distinto de Buscar/Guardadas) = `207:1888` *(existe copia WIP `260:4401`, confirmar canónico)*
  - **Filtros** (subpantalla modal, sin tab bar) · navegación de **modo por segmented**:
    - modo **Por características** (atributos: Tiempo, Dificultad, Restricciones, Porciones) = `208:1976`
    - modo **Por ingredientes** = `363:16472` — campo de búsqueda `364:8056` + grupo **"Tu despensa"** (chips multi-select `364:8062`) + grupo **"Otros ingredientes"** (`365:8072`, chips que se suman por búsqueda). contenido `363:16484`.
    - modo **Por ingredientes · búsqueda activa** (overlay: al escribir, los grupos se reemplazan por la **lista de resultados**) = `374:11270` (resultados `374:11316`).
    - **Segmented relabelado** a **Por ingredientes / Por características** en ambos frames (antes "Por filtros", circular dentro de "Filtros"). **Se descartó "Coincidencia"** (no aportaba como filtro): la reemplaza **"Otros ingredientes"**, alimentado por la búsqueda. Headers de grupo en `Texto/H3` (igual que el otro modo).
  - **Detalle de receta** (push · **mantiene tab bar**; card hero + acordeones) = `232:2751` (uso · 393×852) / `210:2007` (frame extendido para documentar)
    *(en Figma el frame está extendido —393×1193— con los 3 acordeones desplegados para ver todos los componentes; el default en uso es la primera sección abierta, R16)*
- **Notificaciones** = `292:5478` (centro de avisos · se llega desde la campana del Home; push, mantiene tab bar, Home activo) + estados:
  - **Sin notificaciones** (vacío, ✓ + mensaje) = `303:10452`
  - **Swipe para borrar** (revela tacho `action/default`) = `303:8407` (izq) · `303:10170` (der)
  - **Eliminada** (snackbar "Deshacer") = `303:10647`

## Agregados al UI Kit (no listados en el handoff)

- `icon/carrot` = `54:23`, `icon/basket` = `54:30` (Tabler outline, trazo atado a `text/primary` `VariableID:3:55`).
- `icon/minus` = `158:120`, `icon/trash` = `158:124` (Tabler outline 2px, trazo atado a `text/primary`).
- `icon/sustituir` = `201:168` (flechas de intercambio · reemplazar ingrediente; Tabler outline 2px).
- Componente **"Card de receta · compacta"** = `55:16` (172px; foto + bookmark guardar, título, tiempo, dificultad, precio). Usar para feeds de 2 columnas.

## Componentes de Perfil (UI Kit · sección "Perfil · componentes", x≈100/520 y≈1190)

Ya promovidos a componentes con variables/estilos atados y *component properties*:
- **Encabezado de subpantalla** = `123:27` (back 32 + título `Texto/H3`, alto fijo 52). Prop texto **Título**.
- **Fila de ajuste** = `123:31` (título `Texto/H3` `text/secondary` + valor `Body M` + chevron `›`). Props texto **Título**, **Valor**.
- **Input con unidad** = `123:36` (caja `bg/surface` + `border/default` + `radius/sm`). Props texto **Valor**, **Unidad** + boolean **Mostrar unidad**.
- **Fila seleccionable** (set) = `124:40` — **solo cuadrado** (checkbox); variantes **Estado**: Seleccionado/No. Prop texto **Etiqueta**. Activo en `action/default`. (Se descartó la variante radio.)

> **Las pantallas de Perfil ya usan instancias de estos componentes** (`112:166` y las 4
> subpantallas). Para valores vacíos ("Ninguna") se override el color del valor a
> `text/disabled` en la instancia. El **panel inset** (vertical `bg/surface` + `radius/lg` +
> divisores `border/default`) se mantiene como patrón de auto-layout, no como componente
> (es contenedor con hijos variables).

## Componentes de Ingredientes (UI Kit)

Promovidos a componentes con variables/estilos atados y *component properties*:
- **Stepper de cantidad** = `159:120` (− / valor / +; `bg/surface` + `border/default` + `radius/md`;
  íconos `icon/minus` + `icon/plus` en `action/default`). Prop texto **Cantidad** (`Cantidad#159:0`).
- **Campo de búsqueda** = `159:133` (`icon/search` + texto; `bg/surface` + `border/default` +
  `radius/sm`). Prop texto **Texto** (`Texto#159:1`). Reutilizable para *Buscar recetas*.
- **Fila de ingrediente** (set) = `161:148` — variante **Modo**: **Vista** (`161:127`: miniatura +
  nombre `Body L` + cantidad `Body M`) / **Edición** (`161:131`: botón **tacho** `feedback/error` +
  miniatura + nombre + **Stepper**). Nombre/cantidad por override directo en la instancia.
- **Resultado de búsqueda** (set) = `369:4231` — fila de candidato de la **búsqueda de ingredientes**:
  miniatura 36 (`radius/sm`) + nombre `Body L` + círculo de acción 30. Variante **Estado**:
  **Agregar** (`369:4224`: nombre `text/primary` + círculo con borde + `icon/plus`) / **Seleccionado**
  (`369:4230`: nombre `action/default` + círculo relleno `action/default` + `icon/check` blanco).
  Prop texto **Nombre** (`Nombre#369:0`). **Reutilizable**: Carga manual, Filtros "Por ingredientes",
  Carga de ingrediente a la lista (Planificación). Extraído de las filas inline de Carga manual.

> El **botón de micrófono** (Carga por voz) y el **obturador** (Cámara) se construyeron
> inline en su pantalla (uso único, no ameritan componente). La **status bar** se clona del
> Home (`71:348`). La **tab bar** ahora es un **componente** del UI Kit (ver abajo).

## Componente Tab bar (UI Kit) — `179:446`

**Tab bar** = set de variantes con propiedad **Activo** (`Home` · `Recetas` · `Planificación` ·
`Ingredientes` · `Perfil`). Ítem activo en `action/default` (trazo + etiqueta), inactivos en el
gris de la barra. Íconos de **contorno**: al recolorear, tocar **solo el trazo (stroke)**, nunca
el `fill` (los íconos tienen un fill de fondo y rellenarlos los vuelve cuadrados sólidos).
**Ya instanciado en todas las vistas raíz:** Home `56:2`, Perfil `112:166`, Ingredientes
`163:605` / `165:663` / `166:801` — reemplaza las tab bars clonadas que eran inconsistentes.
Orden de destinos: **Home · Recetas · Planificación · Ingredientes · Perfil** (ver nota en R2).
Ya instanciado también en las vistas de **Recetas** (`205:1472` / `207:1656` / `207:1888` / `210:2007`).

## Componentes de Recetas (UI Kit)

Promovidos a componentes con variables/estilos atados y *component properties*:
- **Segmented control · 3 opciones** = `202:199` y **· 2 opciones** = `203:185` (set, prop **Activo**).
  Track `neutral/100` + segmento activo `bg/surface` elevado (sombra) + label `text/primary`; inactivos
  `text/secondary`. Etiquetas por override del texto `label`. Es la **navegación de secciones** (Recetas)
  y de **modo** (Filtros) — distinto de los chips a propósito (ver R14).
- **Card de receta · ancha** = `204:168` (hero del Detalle): foto + nombre + meta (tiempo/dificultad/precio)
  + acciones **Guardar**/**Planificar**. Prop texto **Nombre** (`Nombre#204:0`).
- **Chip "Filtro seleccionado"** (`20:4`) actualizado a **relleno `action/default` + texto `action/on`**
  (antes era "suave"); los filtros usan chips **sin ✓** (selección comunicada por el relleno).

> El **acordeón** del Detalle (header título + chevron + cuerpo colapsable) y las **filas de paso /
> nutricional** se construyeron **inline** (patrón, no componente). El Detalle es subpantalla de
> **contenido** (push) → mantiene la tab bar; **Filtros** es **modal** → sin tab bar (ver R15).

## Variables

- **Color semántico:** IDs `VariableID:3:52`..`3:70`
  (page/surface/subtle · text/primary=`3:55` secondary=`3:56` · border/default=`3:58` · action/default=`3:60` · feedback/error=`3:68`)
- **Medidas:** `VariableID:8:3`..`8:18`

## Próximas pantallas del sitemap

Planificación · Lista de compras.
(Home, Perfil, Ingredientes, **Recetas** —Buscar/Mis recetas/Historial, Filtros, Detalle— y **Notificaciones** ya terminadas.)

**Método acordado:** validar estructura en el chat → construir en Figma.
