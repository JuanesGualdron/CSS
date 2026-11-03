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
