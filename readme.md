# Principios de componentes
Estos principios definen cómo deberán "ordernarse" los distintos componentes construidos, cumpliendo los principios SOLID.
Veremos la relación de estos principios con los principios **SOLID**.

## 1. Componentes
Los componentes son unidades modulares y reutilizables con responsabilidades específicas en un sistema. En el contexto de Clean Architecture, representan diferentes capas y responsabilidades del sistema. No son simplemente los *módulos* de python (los .py)
## 2. Cohesión de los componentes
Al escribir software, debemos preguntarnos ¿A qué módulo corresponderá cada clase?. Existen **tres principios** de la cohesión de componentes:
- **REP** (principio de equivalencia reuso/lanzamiento): definiremos bien los siguientes conceptos:
  - Unidades de Reutilización: Son componentes de software que pueden ser reutilizados en diferentes aplicaciones o contextos. Estos pueden ser clases, módulos, bibliotecas o paquetes.
  - Unidades de Lanzamiento: Son los componentes de software que se versionan y distribuyen juntos. Esto significa que cuando se hace un cambio en una unidad, se lanza una nueva versión de toda la unidad. Si utilizamos el esquema de [versionado semántico](https://semver.org/), tendríamos una versión MAJOR.MINOR.PATCH, en las que cada una de ellas nos define el nuevo lanzamiento. Desde el punto de vista de la arquitectura, un módulo debe tener un versionado y una documentación. Un componente debe tener un propósito común que compartan todos esos módulos. Vamos, que si un componente hace pizzas, los módulos no pueden hacer hamburguesas. 
