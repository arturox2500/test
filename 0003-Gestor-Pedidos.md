---
status: {proposed}
date: {2024-11-05}
decision-makers: {Iván Gutiérrez González, Arturo Enrique Gutiérrez Mirandona}
informed: {Elinne Nathalie Freites Muñoz, Jorge Cimadevilla Aniz}
---

# Gestionar los diferentes estados de un pedido.

## Context and Problem Statement

El problema que se quiere resolver es el cómo administrar los diferentes estados en los que puede estar un pedido, siendo estos intento, pedido, autorización y aceptación.


## Decision Drivers

* RF-3: Gestión de pedidos por fases

## Considered Options

* 0003-1 Patrón Observer.
* 0003-2 Usar la BBDD para la persistencia de los estados.
* 0003-3 Patrón State.

## Decision Outcome

Chosen option: 0003-3 Patrón State, because Proporciona una mayor claridad del código al mantener las lógicas de los distintos estados en diferentes clases.


### Consequences

* Good, because La diferenciación de la lógica de cada estado produce una gran ventaja en claridad, facilidad al añadir estados nuevos, mantenibilidad y organización.
* Good, because Permite el cambio del estado de una clase, y por tanto sus funcionalidades, en tiempo de ejecución.
* Bad, because Requiere una mayor complejidad en la estructura de clases propiciando un mayor uso de la memoria.

### Confirmation

En relación a las otras dos opciones el uso de la base de datos sería una solución al problema de una manera muy estática y rígida imposibilitando su utilización en un sistema de microservicios que busca precisamente esas características. Y la opción del patrón observer es válida para este problema pero su enfoque es diferente teniendo que crear funciones que observen al objeto pedido para cambiar las funcionalidades posibles.
En definitiva, el patrón State es la solución que permite de manera más sencilla el cambio de comportamiento según el cambio de estado.


## Pros and Cons of the Options

### 0003-1 Patrón observer.

Este patrón se encarga de avisar a un objeto en caso de que el objeto al que este observando le suceda un evento. 

* Good, because Permite un cierto nivel de desacoplamiento permitiendo modificar funcionalidades sin que afecten al código principal.
* Good, because Permite añadir nuevos observadores sin cambiar la lógica del sistema.
* Bad, because Puede permitir bajada del rendimiento en caso de cambios de estados frecuentes y/o muchos observadores simultáneos.
* Bad, because Baja flexibilidad de un comportamiento dinámico negando la posibilidad de, al distinguir las lógicas en cada estado, cambiar las funciones de los objetos según cambios en los estados en tiempo de ejecución.

### 0003-2 Usar la BBDD para la persistencia de los estados.

Esta opción se basa en guardar los estados en la BBDD de los pedidos llamando a las funciones necesarias según el estado en el que se encuentra el objeto.

* Good, because Permite mantener la información en la base de datos posibilitando un análisis posterior de los datos y además, en caso de caída del sistema, el estado actual y el historial no se ven afectados.
* Bad, because Muy baja flexibilidad de un comportamiento dinámico teniendo que acceder a la base de datos en muchas ocasiones.
* Bad, because Produce una alta complejidad en el código al no tener bien divididos las funcionalidades de cada estado.
* Bad, because La necesidad de escribir en la base de datos cada vez que se cambie de estados puede ralentizar el sistema.

### 0003-3 Patrón State.

Este patrón permite cambiar las funcionalidades de los objetos según en que estado se encuentre, implementando el concepto de la Maquina de estados finitos.

* Good, because El hecho de que cada estado tenga su propia clase y por ende su propio código independiente proporciona una fácil adición de nuevos estados, una mayor claridad, una mayor mantenibilidad y organización.
* Good, because Proporciona una gran flexibilidad permitiendo que un objeto cambie de estados en tiempo de ejecución. 
* Bad, because Requiere una mayor complejidad en la estructura de las clases, ya que requiere una clase por cada estado posible.
* Bad, because Produce un mayor costo de memoria al crear y mantener instancias de varias clases de estados.



## More Information

Esta solución también realiza la funcionalidad pedida de poner un máximo de intentos por pedido para un cliente al contar con un estado para esta opción.