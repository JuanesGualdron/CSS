# Taller SENA - Maquetación y Estilos CSS (Modelo Monolítico)

Este repositorio contiene el desarrollo del taller escolar, enfocado en una arquitectura web monolítica de una sola página (`index.html`) con navegación interna simulada (`#`) y una hoja de estilos independiente (`estilos.css`).

## 📊 Cálculo de Puntos de Especificidad en CSS

Para garantizar el control del diseño y evitar conflictos visuales en las reglas aplicadas, se utilizó el sistema de ponderación de especificidad estándar:

- **Selectores de Etiqueta (Tipo):** **1 punto** (Ej: `body`, `article`, `footer`).
- **Selectores de Clase:** **10 puntos** (Ej: `.btn-comprar`, `.btn-especial`).
- **Selectores de ID:** **100 puntos** _(Evitados/Refactorizados en este proyecto para cumplir con las buenas prácticas de reutilización)._

### Demostración Técnica y Refactorización

Durante el desarrollo se analizó el conflicto de especificidad generado originalmente por el uso de selectores de ID (`#btn-destacado`). Para resolverlo de manera óptima:

1. Se eliminó el selector de ID en los estilos y el HTML.
2. Se reemplazó por una clase adicional (`.btn-especial`) que permite mantener la especificidad controlada, facilitando la reutilización del código CSS sin sobrecargar el peso de los selectores.

# Actividad: Modelo de Caja y Estilos Tradicionales (SENA)

## Descripción del Proyecto
Catálogo web monolítico desarrollado con HTML5 y CSS3, aplicando el modelo de caja tradicional, selectores específicos y flujo de bloques sin utilizar tecnologías modernas como Flexbox o Grid CSS.

## Hallazgos y Aprendizajes del Modelo de Caja
1. **`box-sizing: border-box`**: Fundamental para evitar que los rellenos (`padding`) y bordes (`border`) sumen un ancho extra no deseado al tamaño total de las cajas, facilitando los cálculos de porcentaje en las tarjetas.
2. **Padding y Margin**: 
   - El `padding` actúa como un "aire interno" de protección para que el texto y los elementos no queden pegados a los bordes de los artículos.
   - El `margin` funciona como un "campo de fuerza exterior" que separa las cajas entre sí para evitar colisiones visuales.
3. **Alineación con `inline-block`**: Al no permitirnos usar Flexbox ni Grid, el uso de `display: inline-block` combinado con `vertical-align: top` y anchos porcentuales (`width: 22%`) nos permitió alinear las 4 tarjetas de productos de forma horizontal en una sola fila.
4. **Control de alturas**: El uso de `min-height` fue clave para solucionar la diferencia de longitudes provocada por las distintas cantidades de texto en cada tarjeta, logrando una apariencia visual limpia y uniforme.

## Hallazgos: Centralización de Identidad Visual y Espaciado

1. **Lista completa de variables declaradas:**
   - **Colores:** `--color-primario` (#008cba), `--color-secundario` (#1e293b), `--color-fondo` (#f4f6f8), `--color-texto` (#444444), `--color-blanco` (#ffffff), `--color-borde` (#cbd5e1), `--color-enlace` (#0066cc) y `--color-secundario-texto` (#94a3b8).
   - **Tipografía:** `--fuente-principal` ('Inter', Arial, sans-serif).
   - **Espaciados (Box Model Tokens):** `--espaciado-pequeno` (8px), `--espaciado-medio` (16px) y `--espaciado-grande` (24px).

2. **Ventaja de reutilizar medidas de margen y relleno:** 
   Estandarizar los espaciados en tokens evita la dispersión de valores arbitrarios o "números mágicos" en el código. Esto permite mantener una proporción visual perfectamente armónica en el flujo de aire de las cajas y facilita modificaciones globales masivas con solo cambiar una línea central en la pseudoclase `:root`.

3. **Prevención de colisiones visuales a medida que la hoja de estilos crece:** 
   Al centralizar la identidad visual en variables globales, se elimina la duplicación de códigos hexadecimales y medidas sueltas. Esto previene inconsistencias estéticas y asegura que cualquier componente nuevo que se agregue al catálogo herede automáticamente la misma escala, manteniendo la interfaz limpia, mantenible y predecible a largo plazo.

   ## Hallazgos: Pseudoclases y Pseudoelementos

1. **Diferencia funcional entre pseudoclases y pseudoelementos:**
   - Una **pseudoclase** (como `:hover`, `:active` o `:focus`) reacciona de forma dinámica a los estados de interacción del usuario o del sistema sobre un elemento existente en el DOM.
   - Un **pseudoelemento** (como `::before` o `::after`) permite generar e inyectar contenido decorativo o virtual directamente en el DOM renderizado sin necesidad de alterar la estructura estática del archivo HTML.

2. **Importancia técnica de la pseudoclase `:focus` en accesibilidad:**
   - El uso de `:focus` con contornos personalizados (`outline`) es una buena práctica crítica de accesibilidad web (A11y). Permite que los usuarios que navegan mediante dispositivos de asistencia o exclusivamente con la tecla `Tab` identifiquen de manera clara y visual en qué elemento o categoría están ubicados en todo momento.

3. **Buenas prácticas al inyectar elementos decorativos desde CSS:**
   - Inyectar etiquetas de oferta, iconos o viñetas decorativas mediante `::before` y `::after` evita "ensuciar" el marcado HTML con elementos vacíos o puramente estéticos. Esto mantiene el HTML limpio, semántico y enfocado únicamente en la estructura de la información, delegando toda la responsabilidad visual y ornamental a la hoja de estilos.