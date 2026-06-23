# TP Integrador UX — RecetApp

Entorno de trabajo compartido para el **Trabajo Práctico Final Integrador de UX/UI**
(UTN). Diseñamos la app mobile **RecetApp** combinando Claude Code + el MCP de Figma,
sobre un mismo archivo de Figma y un sistema de diseño común.

El objetivo de este repo es que todo el equipo trabaje con **el mismo contexto y las
mismas reglas**, de modo que al construir en Figma las vistas salgan coherentes sin
importar quién las haga.

## Qué hay en el repo

| Archivo / carpeta | Para qué sirve |
|---|---|
| `CLAUDE.md` | Instrucciones que Claude Code lee automáticamente al abrir la carpeta. |
| `.claude/skills/` | Skills del MCP de Figma (cómo usar `use_figma`, design system rules, etc.). |
| `RecetApp - Handoff y contexto.md` | **Documento principal.** Contexto completo: consigna, sistema de diseño, decisiones, sitemap, reglas de Figma MCP y roadmap. |
| `docs/roadmap-pantallas.md` | **Roadmap vivo** de todas las vistas a diseñar (Fase 4), por sitemap y con su estado. |
| `docs/contexto-figma.md` | node IDs de Figma, variables y estado de avance actual. |
| `docs/justificaciones-ux.md` | Fundamentación de las decisiones de diseño (leyes/patrones UX + accesibilidad) por pantalla. |
| `recetapp_tokens.json` | Design tokens (colores, tipografías, espaciado, radios). |
| `Sitemap - App recetas.jpg` | Mapa de navegación de la app. |
| `Clase *.pdf`, `Consigna TP Final.pdf` | Material de cátedra y consigna. |

## Cómo poner en marcha el entorno

### 1. Requisitos

- [Claude Code](https://claude.com/claude-code) instalado.
- Acceso al **archivo de Figma** del proyecto (fileKey `xm1jJVWebfvCmj0Yeb7rC3`).
  Pedile a Octavio que te invite con tu cuenta de Figma.

### 2. Clonar el repo

```bash
git clone git@github.com:octavaliente/tp-integrador-ux.git
cd tp-integrador-ux
```

### 3. Conectar el MCP de Figma (imprescindible)

El MCP de Figma es lo que permite que Claude lea y escriba en el archivo de diseño.
Activá el conector de Figma en Claude (Settings → Connectors → Figma) y autorizá tu
cuenta. Verificá la conexión preguntándole a Claude que use la tool `whoami` de Figma.

> La primera vez que Claude use una tool de Figma te va a pedir permiso. Podés
> permitir las de **lectura** (`get_metadata`, `get_screenshot`, `get_design_context`,
> `get_variable_defs`, `whoami`) para trabajar con menos interrupciones. Tus permisos
> quedan en `.claude/settings.local.json`, que es personal y no se comparte.

### 4. Abrir Claude Code en la carpeta

```bash
claude
```

Claude levanta `CLAUDE.md` y las skills automáticamente. **Antes de empezar a
construir, pedile que lea `RecetApp - Handoff y contexto.md` y `docs/contexto-figma.md`**
para arrancar con todo el contexto del proyecto.

## Forma de trabajo acordada

1. **Validar cada cosa en el chat antes de construirla en Figma**, e iterar.
2. Respetar el sistema de diseño y los tokens (`recetapp_tokens.json`).
3. Reutilizar los componentes del UI Kit ya existentes (ver `docs/contexto-figma.md`).
4. Mantener todo en **WCAG AA**.

## Presentación

Fecha objetivo: **2 de julio de 2026** (≤20 min, todos participan).
