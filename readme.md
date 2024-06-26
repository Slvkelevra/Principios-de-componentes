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
# Arquitectura
Una buena arquitectura, para que nos hagamos una idea, es la que hace que el 
sistema sea fácil de comprender, fácil de desarrollar, fácil de mantener y 
fácil de implementar. 
Hay que tener en cuenta que no es lo mismo desarrollar que implementar. En el 
desarrollo, se elabora el software desde el inicio hasta el final. La implementación
implica la puesta de ese desarrollo en un entorno operativo, conectando todos 
los posibles equipos de desarrollo en un único "ejecutable".

## 1. Desarrollo
Los sistemas deben de ser **fáciles de desarrollar**. Los sistemas con difícil desarrollo
finalmente no son saludables. Si el equipo de desarrollo está dividido en subequipos,
deberemos dividir en piezas muy acotadas para que los equipos puedan trabajar
de manera individual sin entorpecer el trabajo de otros equipos.
## 2. Implementacion
Los sistemas deben de ser fácilmente implementables. Imaginemos un sistema de 
microservicios. El desarrollo de cada microservicio es muy sencillo. Tienen las
responsabilidades y los límites muy acotados. Sin embargo, si nos encontramos con
una cantidad inmensa, será muy difícil su implementación. Un buen arquitecto
facilita que cada una de las piezas software puedan desplegarse de manera 
independiente, sin tener dependencias de otras piezas.
## 3. Mantenimiento
Es el más costoso. Una buena arquitectura mitiga estos costos, de indagar dónde
es el mejor sitio donde incluir nuevas funcionalidades. El separar el sistema
en componentes y aislarlos, es posible facilitar la inserción de futuras funciones.
# Reglas de negocio
Las reglas de negocio son reglas o procedimientos que generan o ahorran dinero 
a las empresas. Es decir, son reglas que generan dinero a la empresa, se programen
o se hagan manualmente. Estas reglas que existen aunque no sean en un ordenador
se les llama **Reglas de negocio fundamentales**. Además, estas reglas necesitan
de una información para poder implementarlas. A esta información se le llama 
**Información fundamental**. Ambas están estrechamente unidades, por lo que 
al conjunto se le llama **objeto Entidad**
## Entidades
Una entidad sería, por ejemplo, una clase que contiene los atributos y unos 
métodos que presentan las reglas de negocio fundamentales. Esta entidad, además,
debe cumplir con los principios SOLID (SRP, que solo debe tener la lógica de
esa regla de negocio, etc).
## Casos de uso
Se trata de una descripción del modo en el que se utiliza un sistema automatizado.
Se especifica la entrada de datos, lo que se debe hacer con ellos y la salida.
Un caso de uso describe las reglas de negocio específicas, en vez de las reglas
Fundamentales de las entidades.

**Reglas de negocio Fundamentales (entidades) =! Reglas de negocio (casos de uso)**
Por ejemplo, un caso de uso podría ser:
-------------------------------------------------------------------------
-------------------------------------------------------------------------
Reunir información de contacto para nuevo préstamo.

Entrada:Nombre, dirección, fecha de nacimiento, DNI
Salida: Misma información para verificación
Curso principal:
1. Aceptar y validar nombre
2. Validar dirección y otros datos
3. Obtener puntuación de crédito
4. Devolver True si es mayor que 500. False si es menor
-------------------------------------------------------------------------
-------------------------------------------------------------------------

Muy importante: **las Entidades no conocen los casos de uso que los gobiernan**
Es decir, las entidades son independientes de los casos de uso. Las Entidades, 
como hemos mencionado, son la lógica de negocio fundamental (atributos y métodos)
que manipulan esos atributos) y los casos de uso son una lógica no fundamental.
Las Entidades son de alto nivel (son generalizaciones que se pueden utilizar 
en muchas aplicaciones). Los casos de uso son de bajo nivel (son específicos
de una aplicación).
Los casos de uso dependen de las Entidades, pero las Entidades no dependen de los
casos de uso (por eso en las arquitecturas Clean, las entidades se encuentran 
en la parte más interna, porque no suelen cambiar).
## Diferencias Clave
- Enfoque:
  - Casos de Uso: Enfocados en la interacción del usuario con el sistema.
  - Lógica de Negocio Fundamental: Enfocada en cómo el sistema realiza las tareas y maneja los datos.

- Perspectiva:
  - Casos de Uso: Desde la perspectiva del usuario.
  - Lógica de Negocio Fundamental: Desde la perspectiva del sistema y el negocio.

- Objetivo:
  - Casos de Uso: Definir qué debe hacer el sistema para satisfacer al usuario.
  - Lógica de Negocio Fundamental: Definir cómo el sistema debe funcionar internamente para cumplir con las reglas del negocio.

- Nivel de Abstracción:
  - Casos de Uso: generalmente más abstractos, describiendo interacciones.
  - Lógica de Negocio Fundamental: Más detallada, describiendo procesos y reglas específicas.

## Conclusión
Las **entidades** encapsulan la información fundamental y algunas reglas de negocio 
fundamentales relacionadas con la integridad y validación de los datos. 
Los **casos de uso** describen cómo los usuarios interactúan con el sistema y 
cómo se aplican las reglas de negocio en esos contextos, pero no son las reglas
de negocio en sí mismas. En resumen:

**Entidades** = Información Fundamental + Algunas Reglas de Negocio Fundamentales 
(relacionadas con la integridad de los datos).

**Casos de Uso** = Descripción de Interacciones del Usuario + Aplicación de Reglas de Negocio (pero no las reglas en sí).

Un ejemplo podría ser el siguiente:

### Entidad: "Usuario"

- Atributos (Información Fundamental): Nombre, Email, Contraseña, Fecha de Registro.
- Reglas de Negocio: El Email debe ser único, la Contraseña debe tener al menos 8 caracteres, la Fecha de Registro no puede ser futura.

### Caso de Uso: "Registrar Usuario"

- Descripción:
  - El usuario ingresa su nombre, email y contraseña.
  - El sistema valida que el email no está en uso (Regla de Negocio).
  - El sistema valida que la contraseña cumple con los requisitos (Regla de Negocio).
  - El sistema crea una nueva entrada en la entidad Usuario con los datos proporcionados.
  - El sistema envía un correo de confirmación al nuevo usuario.

# Arquitecturas de gritan
Cuando miramos unos planos, vemos algo. En el caso de ver el plano de una casa, 
probablemente veremos un hogar. Si miramos los de una biblioteca, veremos una 
biblioteca. Al mirar la arquitectura de una aplicación, debemos ver lo que 
hace la aplicación. 
Las arquitecturas deben soportan los casos de uso (como los planos de una casa
soportan las necesidades de un hogar). 
Por ejemplo, un arquitecto no propone los materiales de los tabiques. Simplemente
indica que es una "separación". Podría ser de ladrillos, manera, etc. 
En una arquitectura de una aplicación debe ser igual. Es muy común acoplarse
a la arqutiectura que nos propone un framework, pero puede no ser suficiente.
La arquitectura, inicialmente, debe ser capaz de soportar los casos de uso y 
no los detalles de construcción, como los materiales. 
Una buena arquitectura permite que las decisiones como **frameworks, base de datos,
etc** se puedan posponer.
# Arquitectura limpia
Las arquitecturas limpias se corresponden con aquellas que separan las 
responsabilidades. Lo hacen separándolas mediante capas. Estas arquitecturas
producen sistemas con las siguientes características:
1. Independencia de frameworks: no nos obliga a acoplarnos a un framework.
2. Comprobable: las reglas de negocio se pueden comprobar sin una UI o base de datos, 
ya que se encuentran en una capa independiente.
3. **Independencia de la base de datos**: podemos utilizar cualquier base de 
datos, ya que no nos acoplamos a ninguna.
4. **Independencia de cualquier agente externo**: no nos acoplamos a sistemas
externos, como brokers de mensajería. Las reglas de negocio son independientes.

# La regla de la dependencia
Es la regla más importante de las arquitecturas clean. Nos dice que el flujo
va de fuera hacia dentro. Es decir, capas interiores no deben de saber nada 
sobre las capas exteriores.
# Entidades (Entities)
Incluyen las reglas de negocio fundamentales. Pueden tener métodos o no.
Mientras se puedan compartir entre aplicaciones, son entidades.
# Casos de uso (Services)
Se corresponde con los servicios. Con las reglas de negocio específicas de la 
aplicación. Esta capa no se ve afectada por cambios en el dominio o 
cambios en la capa de controller o interface.
# Adaptadores de interfaz (Controller)
Aquí se implementan, por ejemplo, los endpoints de un API RESTFull. Aquí
se utiliza, por ejemplo, los frameworks Flask o FastAPI. Utilizan las 
implementaciones de los repositorios y modelos de la capa inmediata 
anterior (Infraestructura)
# Infraestructura
Aquí se se implementan las interfaces de la capa repositorio y los modelos 
de la base de datos.
