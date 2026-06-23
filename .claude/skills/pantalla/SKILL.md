---
name: pantalla
description: Diseñar una pantalla nueva de RecetApp (TP UX) de punta a punta — análisis crítico del wireframe, validación de la estructura en el chat, construcción en Figma partiendo del UI Kit, y documentación. Usar cuando el usuario pase un wireframe/idea de una vista o pida diseñar/armar una pantalla del roadmap.
disable-model-invocation: false
---

# Diseñar una pantalla — RecetApp

Flujo estándar para cada vista. Reemplaza tener que re-explicar la intención: el usuario
pasa un wireframe/idea (lo importante es **captar la intención**, no copiar el boceto) y vos
llevás el proceso hasta dejar la pantalla terminada y documentada.

## Antes de empezar
Leé el contexto vigente (gran parte ya entra por `CLAUDE.md`): `@docs/contexto-figma.md`
(node IDs, variables, componentes), `@docs/reglas-transversales.md`, `@docs/roadmap-pantallas.md`
(alcance de la pantalla) y `RecetApp - Handoff y contexto.md`.

## Pasos
1. **Analizar crítico.** Tomá la intención del wireframe y aplicá patrones UX, leyes y las
   reglas transversales. Sé crítico: sugerí mejoras o justificá la propuesta si está bien.
   Cruzá con el sitemap (arquitectura de información) y con lo ya construido.
2. **Iterar estructura en el chat.** Acordá secciones, jerarquía y colocación de componentes
   **antes** de tocar Figma. Si hay decisiones de fondo, preguntá (pocas, concretas). Si
   ayuda a "imaginarlo", mostrá una maqueta visual (Artifact HTML con los tokens reales).
3. **UI Kit primero.** Identificá qué componentes faltan y creálos/validalos en la página
   UI Kit (`15:3`) con variables/estilos atados y *component properties*. Recién después
   maquetás la vista con **instancias** (no recrear).
4. **Construir la pantalla.** Sobre la plantilla iPhone 15 (393×852), reutilizando tab-bar /
   status bar y los componentes. Verificá con `screenshot` y devolvé los node IDs.
5. **Documentar (4 docs).** Justificaciones → `@docs/justificaciones-ux.md`; marcar completada
   → `@docs/roadmap-pantallas.md`; reglas transversales nuevas → `@docs/reglas-transversales.md`;
   node IDs → `@docs/contexto-figma.md`.

## Reglas que no se negocian
- WCAG AA: contraste 4.5:1, táctil ≥44 px, **no depender solo del color**. Acento/acción =
  **calabaza 600 `#AF5012`** (el 500 no pasa).
- Evitar uso excesivo de **Cards** (listas/ajustes → filas + divisores).
- Todo atado a variables/estilos del sistema; nada hardcodeado. Mantener el UI Kit actualizado.

## Figma — gotchas que ahorran tiempo
- Cargá la skill **figma-use** antes de cada `use_figma`. Plan con **rate limit**: agrupá el
  trabajo por llamada; ante error el script es **atómico** (no reintentar a ciegas).
- **Cargá las fuentes** (Inter Regular/Medium, Poppins Medium/SemiBold) antes de escribir texto
  o setear *text properties*.
- Para instanciar un componente: leé `node.componentPropertyDefinitions` y usá la **key completa
  con sufijo** (`Título#123:1`) en `setProperties`. Variantes: `set.defaultVariant.createInstance()`;
  la prop de variante va con nombre plano (`Estado`), las de texto/bool con `#id`.
- Tab-bar / status bar: cloná las del Home. Activo = `action/default` (`VariableID:3:60`),
  inactivo = `text/secondary` (`VariableID:3:56`).
- Estados vacíos ("Ninguna"): override del color del valor a `text/disabled` en la instancia.
