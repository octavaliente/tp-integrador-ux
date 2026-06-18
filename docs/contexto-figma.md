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

## Agregados al UI Kit (no listados en el handoff)

- `icon/carrot` = `54:23`, `icon/basket` = `54:30` (Tabler outline, trazo atado a `text/primary` `VariableID:3:55`).
- Componente **"Card de receta · compacta"** = `55:16` (172px; foto + bookmark guardar, título, tiempo, dificultad, precio). Usar para feeds de 2 columnas.

## Variables

- **Color semántico:** IDs `VariableID:3:52`..`3:70`
  (page/surface/subtle · text/primary=`3:55` secondary=`3:56` · border/default=`3:58` · action/default=`3:60` · feedback/error=`3:68`)
- **Medidas:** `VariableID:8:3`..`8:18`

## Próximas pantallas del sitemap

Recetas · Detalle de receta · Planificación · Perfil · Ingredientes · Notificaciones.

**Método acordado:** validar estructura en el chat → construir en Figma.
