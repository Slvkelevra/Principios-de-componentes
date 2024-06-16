# Principios de componentes
Estos principios definen cómo deberán "ordernarse" los distintos componentes construidos, cumpliendo los principios SOLID.
Veremos la relación de estos principios con los principios **SOLID**.

## 1. Componentes
Los componentes son unidades modulares y reutilizables con responsabilidades específicas en un sistema. En el contexto de Clean Architecture, representan diferentes capas y responsabilidades del sistema. No son simplemente los *módulos* de python (los .py)
## 2. Cohesión de los componentes
Al escribir software, debemos preguntarnos ¿A qué módulo corresponderá cada clase?. Existen **tres principios** de la cohesión de componentes:
- **REP** (principio de equivalencia reuso/lanzamiento): definiremos los siguientes conceptos:
  - **Unidades de Reutilización**: Son componentes de software que pueden ser reutilizados en diferentes aplicaciones o contextos. Estos pueden ser clases, módulos, bibliotecas o paquetes.
  - **Unidades de Lanzamiento**: Son los componentes de software que se versionan y distribuyen juntos. Esto significa que cuando se hace un cambio en una unidad, se lanza una nueva versión de toda la unidad. Si utilizamos el esquema de [versionado semántico](https://semver.org/), tendríamos una versión MAJOR.MINOR.PATCH, en las que cada una de ellas nos define el nuevo lanzamiento. Desde el punto de vista de la arquitectura, un módulo debe tener un versionado y una documentación. Un componente debe tener un propósito común que compartan todos esos módulos. Vamos, que si un componente hace pizzas, los módulos no pueden hacer hamburguesas.
    
  Imaginemos que tenemos una librería de autenticación que hemos desarrollado para un proyecto específico, pero que podría ser útil en otros proyectos. Siguiendo el principio de equivalencia reutilización/lanzamiento:
    - Reutilización: debemos asegurarnos de que la librería está diseñada de manera que pueda ser fácilmente integrada en diferentes proyectos. Esto podría implicar crear interfaces claras, proporcionar documentación detallada, y evitar dependencias innecesarias.
    - Lanzamiento: debemos liberar la librería como un componente independiente. Esto podría incluir crear un repositorio separado para la librería, versionarla correctamente, y proporcionar instrucciones claras de instalación y uso.
- **CCP** (principio de cierre común): nos dice que se encierre en un mismo componente los módulos,
   clases, etc, que cambien **por la misma razón**. Esto es lo mismo que nos dice el principio SRP:
   un módulo solo debe ser responsable de un único actor.
- **CRP** (principio de reuso común): este principio nos dice que clases y módulos que se usan juntos,
   deben estar en el mismo componente. Por ejemplo. si un componente *utilizador* depende de una clase 
  del componente *utilizado*, entonces habrá una dependencia débil. Esto quiere decir que 
  cada vez que cambie el módulo *utilizador*, deberá cambiar el componente *utilizado*
  por lo que probablemente deban ir en el mismo componente. Es el ISP llevado a componentes:
  **no depender de piezas que no se necesitan**
## 3. Acoplamiento de componentes
Al igual que con la cohesión de los componentes, tenemos otros tres principios 
para el acoplamiento:
- **ADP** (principio de dependencias acíclicas): esto nos dice que los componentes
  que se liberan no deben depender de otros y se deben liberar para funcionar 
  de manera independiente. Si esto no se cumple, un módulo en el que estamos 
  trabajando que depende de otro módulo de otro compañero (que también está 
  trabajando en él) puede ser que hoy funcione y mañana no. 
- **SBP** (principio de dependencias estables): nos dice que el grafo de dependencias 
  debe ir de más estable a menos estable. De esta manera, se minimizan los efectos
  de los cambios de un módulo en otro. **Los módulos con dependencias, deben 
  depender de módulos más estables que ellos mismos**
- **SAP** (principio de abstracciones estables): El SAP sugiere que si un módulo 
  es estable (es decir, difícil de cambiar porque muchos otros módulos dependen de él), 
  debería ser abstracto. Esto permite que el módulo sea flexible y extensible 
  sin necesidad de cambios significativos. En otras palabras, los módulos que 
  son difíciles de cambiar deben ser fáciles de extender (deben ser lo más 
  abstractos posible).


