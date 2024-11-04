---
status: {proposed}
date: {2024-11-4}
decision-makers: {Iván Gutiérrez González, Arturo Enrique Gutiérrez Mirandona}
informed: {Elinne Nathalie Freites Muñoz, Jorge Cimadevilla Aniz}
---

# Modificar los estados de un pedido.

## Context and Problem Statement

{Describe the context and problem statement, e.g., in free form using two to three sentences or in the form of an illustrative story. You may want to articulate the problem in form of a question and add links to collaboration boards or issue management systems.}

<!-- This is an optional element. Feel free to remove. -->
## Decision Drivers

* RF-6: Controlar los diferentes estados en los que puede estar un pedido.

## Considered Options

* 0005-1 Patrón observer.
* 0005-2 Usar la BBDD para la persistencia de los estados.
* 0005-3 Maquina de estados finita.

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

### 0005-1 Patrón observer.

<!-- This is an optional element. Feel free to remove. -->
{example | description | pointer to more information | …}

* Good, because {argument a}
* Good, because {argument b}
<!-- use "neutral" if the given argument weights neither for good nor bad -->
* Neutral, because {argument c}
* Bad, because {argument d}
* … <!-- numbers of pros and cons can vary -->

### 0005-2 Usar la BBDD para la persistencia de los estados.

{example | description | pointer to more information | …}

* Good, because {argument a}
* Good, because {argument b}
* Neutral, because {argument c}
* Bad, because {argument d}
* …

### 0005-3 Maquina de estados finita.

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

* 3.- Máquina de Estados Finita (FSM)

Qué es: Es una estructura que define un conjunto de estados finitos y las transiciones posibles entre ellos. En este caso, el pedido podría pasar por estados como "creado", "preprocesado", "autorizado", etc., siguiendo un flujo predefinido.

-Pros:

Control claro: Las reglas de transición entre estados están claramente definidas, minimizando errores y manteniendo un flujo lógico.

Simplicidad en el flujo: Muy útil para sistemas que requieren una secuencia de estados predecible.

-Contras:

Rigidez: Una FSM puede ser difícil de cambiar o extender si el flujo se vuelve más complejo.

Escalabilidad limitada: No es ideal si hay muchas variaciones en el flujo, ya que agregar nuevos estados o transiciones puede complicar la FSM.

* Resumen Comparativo

-Observer: Ideal para notificar cambios sin acoplamiento; útil en sistemas que requieren actualizaciones automáticas de otras partes.

-Base de Datos para Persistencia: Asegura que los estados y su historial estén disponibles para auditoría y recuperación; ideal para trazabilidad, pero tiene un coste de rendimiento.

-FSM: Proporciona una estructura clara para flujos predefinidos y secuenciales; excelente para control, pero menos flexible y escalable para flujos complejos.