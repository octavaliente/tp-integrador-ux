# Contexto

@README.md
@docs/contexto-figma.md
@docs/reglas-transversales.md

# Skills disponibles

Dentro de la carpeta de archivos, en @.claude/skills existen Skills disponibles para ayudarte en el uso de Figma MCP

# Forma de trabajo desde Wireframes

Te voy a enviar wireframes e ideas sobre las vistas (Lo mas importante es que captes la intención), las cuales definen los lineamientos para luego construir las diferentes pantallas.

Cuando te pase esto, necesito que seas crítico y apliques todas las reglas existentes sobre patrones de diseño y UX para alcanzar wireframes robustos y consistentes en toda la App.

Es importante que: 
- Inicialmente iteremos el wireframe buscando una optima colocación de componentes y arquitectura de la información.

Los wireframes que te voy pasando estan relacionados tambien al @docs/roadmap-pantallas.md

Cuando definamos una nueva regla transversal a toda la app debemos anotarla por separado y usarlas, por ejemplo: 
- Siempre que accedamos a una subpantalla en la vista usar un icono de volver. 

# Implementación de wireframes

Siempre validar la idea final antes de pasar a la implemnetación figma

En figma: Siempre partir desde UI Kit y luego ir a la implementación.

# Implmentación Figma

- Cargar la skill figma-use antes de cada use_figma.
- Plan con rate limit: agrupar el trabajo por llamada y minimizar verificaciones.
- Construir con auto-layout; atar TODO a variables/estilos y usar component properties (nada hardcodeado).
- Reutilizar instancias del UI Kit; no recrear lo que ya existe.
- Verificar con screenshot y registrar node IDs nuevos en docs/contexto-figma.md.

# Respuestas finales

Al terminar una vista: justificaciones (@docs/justificaciones-ux.md), marcar (@docs/roadmap-pantallas.md), anotar reglas transversales nuevas (@docs/reglas-transversales.md) y registrar node IDs (@docs/contexto-figma.md).

# Reglas

Fidelidad a los patrones UX
Accesibilidad WCAG AA.
Consistente con enunciado de TP.
Evitar uso excesivo de Cards.
Siempre mantener consistencia con UI Kit y mantenerlo siempre actualizado.

