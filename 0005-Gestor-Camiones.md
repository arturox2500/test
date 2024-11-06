---
status: {proposed}
date: {2024-11-05}
decision-makers: {Iván Gutiérrez González, Arturo Enrique Gutiérrez Mirandona}
informed: {Elinne Nathalie Freites Muñoz, Jorge Cimadevilla Aniz}
---

# Eficiencia de la utilización de los camiones

## Context and Problem Statement

El problema resuelto a continuación abarca la gestión de que camiones van a entregar cada paquete, intentando que se optimize el uso de os camniones disminuyendo costes como el de la gasolina y los tiempos.

<!-- This is an optional element. Feel free to remove. -->
## Decision Drivers

* RF-5: Optimización de rutas para camiones.

## Considered Options

* 0005-1-Algoritmo heurístico
* 0005-2-Algoritmo de programación lineal

## Decision Outcome

Chosen option: 0005-1-Algoritmo heurístico, because {justification. e.g., only option, which meets k.o. criterion decision driver | which resolves force {force} | … | comes out best (see below)}.

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

### 0005-1-Algoritmo heurístico

<!-- This is an optional element. Feel free to remove. -->
{example | description | pointer to more information | …}

* Good, because {argument a}
* Good, because {argument b}
<!-- use "neutral" if the given argument weights neither for good nor bad -->
* Neutral, because {argument c}
* Bad, because {argument d}
* … <!-- numbers of pros and cons can vary -->

### 0005-2-Algoritmo de programación lineal

{example | description | pointer to more information | …}

* Good, because {argument a}
* Good, because {argument b}
* Neutral, because {argument c}
* Bad, because {argument d}
* …

<!-- This is an optional element. Feel free to remove. -->
## More Information

### Opción 1: Microservicio de Asignación de Camiones basado en Algoritmos de Optimización Heurística

En esta solución, se implementa un microservicio que emplea algoritmos de optimización heurística para asignar cada camión a una ruta en función de ciertos criterios predefinidos, como la proximidad, la capacidad de carga y la urgencia de entrega.

- Descripción: El microservicio toma como entrada la lista de camiones disponibles y las rutas pendientes de asignación. Usando un algoritmo de heurística, como el Algoritmo de Vecino Más Cercano o una variante de Algoritmo Genético, calcula la asignación óptima de camión-ruta considerando factores como:

    --Distancia al punto de partida de la ruta: Asigna el camión más cercano para reducir el tiempo y el coste de transporte.

    --Capacidad del camión: Solo asigna rutas que respeten la capacidad de carga del camión.

    --Nivel de urgencia de la entrega: Rutas con alta prioridad o demoras se asignan a camiones disponibles inmediatamente.

- Ventajas:

Este enfoque es flexible y se adapta a condiciones cambiantes (ej., diferentes ubicaciones de camiones y rutas a lo largo del día).
La implementación de heurísticas permite soluciones rápidas y suficientemente optimizadas sin necesidad de alta capacidad computacional.

- Desventajas:

La solución heurística puede no siempre dar la asignación óptima en todos los casos, pero debería ser adecuada para la mayoría de las operaciones cotidianas.

### Opción 2: Microservicio de Asignación de Camiones con un Sistema de Optimización Basado en Programación Lineal

Esta opción utiliza un enfoque de programación lineal, ideal para problemas de asignación en los que se busca minimizar un coste objetivo, como el tiempo o el coste de transporte.

- Descripción: Este microservicio recibe las rutas y camiones disponibles y, a través de un solver de programación lineal (como Google OR-Tools o Gurobi), resuelve el problema como un modelo de optimización matemática. Los parámetros del modelo incluyen:

    --Coste de asignación: Cada posible asignación de camión-ruta tiene un coste basado en factores como la distancia o el tiempo estimado de llegada.

    --Restricciones: Incluyen la capacidad de carga del camión y limitaciones en el número de rutas por camión.

    --Función objetivo: Minimizar el coste total de asignación o maximizar la puntualidad de entregas, priorizando rutas con mayor urgencia.

- Ventajas:

Proporciona una solución optimizada y generalmente exacta.
Puede ser ajustado para cumplir diferentes objetivos (minimizar coste, maximizar eficiencia, reducir tiempos de entrega).

- Desventajas:

La programación lineal requiere mayor capacidad computacional, especialmente con gran número de rutas y camiones.
Puede ser menos flexible en condiciones de alta variabilidad si no se ajusta frecuentemente el modelo.
