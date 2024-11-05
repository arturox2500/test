---
status: {proposed}
date: {2024-11-05}
decision-makers: {Iván Gutiérrez González, Arturo Enrique Gutiérrez Mirandona}
informed: {Elinne Nathalie Freites Muñoz, Jorge Cimadevilla Aniz}
---

# Gestionar los diferentes estados de un pedido.

## Context and Problem Statement

El problema que se quiere resolver es el como administrar los diferentes estados en los que puede estar un pedido, siendo estos intento, pedido, autorización y aceptación.

<!-- This is an optional element. Feel free to remove. -->
## Decision Drivers

* RF-3: Gestión de pedidos por fases

## Considered Options

* 0003-1 Patrón Observer.
* 0003-2 Usar la BBDD para la persistencia de los estados.
* 0003-3 Patrón State.

## Decision Outcome

Chosen option: "{title of option 1}", because {justification. e.g., only option, which meets k.o. criterion decision driver | which resolves force {force} | … | comes out best (see below)}.

<!-- This is an optional element. Feel free to remove. -->
### Consequences

* Good, because {positive consequence, e.g., improvement of one or more desired qualities, …}
* Bad, because {negative consequence, e.g., compromising one or more desired qualities, …}
* … <!-- numbers of consequences can vary -->

<!-- This is an optional element. Feel free to remove. -->
### Confirmation

{Describe how the implementation of/compliance with the ADR can/will be confirmed. Is the chosen design and its implementation in line with the decision? E.g., a design/code review or a test with a library such as ArchUnit can help validate this. Note that although we classify this element as optional, it is included in many ADRs.}

<!-- This is an optional element. Feel free to remove. -->
## Pros and Cons of the Options

### 0003-1 Patrón observer.

<!-- This is an optional element. Feel free to remove. -->
{example | description | pointer to more information | …}

* Good, because {argument a}
* Good, because {argument b}
<!-- use "neutral" if the given argument weights neither for good nor bad -->
* Neutral, because {argument c}
* Bad, because {argument d}
* … <!-- numbers of pros and cons can vary -->

### 0003-2 Usar la BBDD para la persistencia de los estados.

{example | description | pointer to more information | …}

* Good, because {argument a}
* Good, because {argument b}
* Neutral, because {argument c}
* Bad, because {argument d}
* …

### 0003-3 Patrón State.

{example | description | pointer to more information | …}

* Good, because {argument a}
* Good, because {argument b}
* Neutral, because {argument c}
* Bad, because {argument d}
* …


<!--Chat gpt-->
## More Information

Resumen explicativo y comparativo de las tres opciones: patrón Observer, base de datos para la persistencia de estados y máquina de estados finita, enfocadas en la gestión de estados de un pedido.

* 1.- Patrón Observer

Qué es: En este patrón, un objeto central (por ejemplo, el pedido) notifica automáticamente a otros objetos (observadores) cuando su estado cambia. Los observadores pueden ser otros componentes interesados en los cambios de estado, como un módulo de notificaciones o de estadísticas.

-Pros:

Desacoplamiento: Los observadores no dependen directamente del pedido, lo que permite agregar o modificar funcionalidades sin afectar al código principal.

Extensibilidad: Es fácil añadir nuevos observadores sin cambiar la lógica central.

-Contras:

Complejidad: Con muchos observadores, el seguimiento y manejo de notificaciones puede complicarse.

Carga: Si los cambios de estado son frecuentes y hay muchos observadores, puede afectar al rendimiento.

* 2.- Base de Datos para la Persistencia de Estados

Qué es: Cada cambio de estado del pedido se guarda en una base de datos. Esto permite registrar el estado actual y el historial completo de transiciones para futuras consultas o auditorías.

-Pros:

Persistencia: El historial de estados se mantiene almacenado, permitiendo un análisis posterior.

Resiliencia: En caso de caída del sistema, el estado actual y el historial están guardados y pueden recuperarse fácilmente.

-Contras:

Complejidad de transacciones: Es necesario asegurarse de que los cambios de estado se guarden correctamente, especialmente en sistemas distribuidos.

Rendimiento: Cada cambio de estado requiere una escritura en la base de datos, lo que puede ralentizar el sistema si hay muchos cambios frecuentes.

* 3.- Patrón State:

Qué es: State es un patrón de diseño de comportamiento que permite a un objeto alterar su comportamiento cuando su estado interno cambia. Parece como si el objeto cambiara su clase. El patrón State está estrechamente relacionado con el concepto de la Máquina de estados finitos.

-Pros:

Organización y Mantenibilidad: Cada estado tiene su propia clase, lo que organiza el código al encapsular la lógica de cada estado de manera separada. / Al separar la lógica por estado, el código es más fácil de entender, mantener y extender. Es sencillo modificar un estado sin afectar a los demás.

Facilita la Adición de Nuevos Estados o Transiciones: Para añadir un nuevo estado, solo es necesario crear una nueva clase que implemente la lógica de ese estado, sin tener que modificar el código existente. / Si en el futuro se requiere un nuevo estado en el flujo de un pedido, este patrón permite incluirlo con cambios mínimos en el código actual.

Flexibilidad en el Comportamiento Dinámico: El objeto puede cambiar de estado en tiempo de ejecución, y cada estado puede tener su propio comportamiento específico, facilitando la adaptación a distintas condiciones y reglas de negocio en tiempo real. / Esto permite una gran flexibilidad si el comportamiento del sistema cambia en función del estado actual.

Soporte para Extensiones de los Estados: Si los estados requieren acciones específicas adicionales (por ejemplo, notificaciones o validaciones), estas pueden implementarse directamente en la clase correspondiente al estado sin afectar el resto del sistema.

-Contras:

Mayor Complejidad en la Estructura de Clases: Implementar el patrón State requiere crear una clase para cada estado, lo que puede incrementar significativamente el número de clases. / En sistemas grandes o con muchos estados, la gestión de clases adicionales puede volverse difícil y llevar a una estructura de código más compleja.

Mayor Costo en Términos de Memoria y Rendimiento: Crear y mantener instancias de varias clases de estado puede aumentar el uso de memoria y reducir el rendimiento si el sistema gestiona un alto volumen de pedidos o cambios de estado. / Esto puede no ser un problema significativo en sistemas de baja concurrencia, pero podría volverse un inconveniente en sistemas de alta concurrencia.

* Resumen Comparativo

-Observer: Ideal para notificar cambios sin acoplamiento; útil en sistemas que requieren actualizaciones automáticas de otras partes.

-Base de Datos para Persistencia: Asegura que los estados y su historial estén disponibles para auditoría y recuperación; ideal para trazabilidad, pero tiene un coste de rendimiento.

-El patrón State: Es una excelente opción si el sistema tiene estados bien definidos y el flujo es predecible, ofreciendo una buena organización y encapsulamiento de la lógica de estados. Sin embargo, si el flujo es demasiado dinámico o los estados comparten mucha lógica, puede introducir una complejidad innecesaria y sobrecargar el sistema en términos de clases y mantenimiento.