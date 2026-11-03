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