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

## Agregados al UI Kit (no listados en el handoff)

- `icon/carrot` = `54:23`, `icon/basket` = `54:30` (Tabler outline, trazo atado a `text/primary` `VariableID:3:55`).
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

## Variables

- **Color semántico:** IDs `VariableID:3:52`..`3:70`
  (page/surface/subtle · text/primary=`3:55` secondary=`3:56` · border/default=`3:58` · action/default=`3:60` · feedback/error=`3:68`)
- **Medidas:** `VariableID:8:3`..`8:18`

## Próximas pantallas del sitemap

Recetas · Detalle de receta · Planificación · Perfil · Ingredientes · Notificaciones.

**Método acordado:** validar estructura en el chat → construir en Figma.
