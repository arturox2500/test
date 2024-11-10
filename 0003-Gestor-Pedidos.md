---
status: {accepted}
date: {2024-11-10}
decision-makers: {Iván Gutiérrez González, Arturo Enrique Gutiérrez Mirandona}
consulted: {Elinee Nathalie Freites Muñoz, Jorge Cimadevilla Aniz}
informed: {Víctor Bartolomé Letosa, Alejandro Valor González}
---

# Gestionar los diferentes estados de un pedido.

## Context and Problem Statement

El problema que se quiere resolver es el cómo administrar los diferentes estados en los que puede estar un pedido, siendo estos preprocesado del pedido, autorización y aceptación. Así como saber actualizar las estadísticas de los clientes cuando se pasa de un estado a otro.


## Decision Drivers

* RF-3: Gestión de pedidos por fases.
* RF-5.2: Generación de estadísticas para los usuarios.

## Considered Options

* 0003-1 Patrón observer.
* 0003-2 Creación de una clase OrderAplication.
* 0003-3 Patrón State.

## Decision Outcome

Chosen option: 0003-2 Creación de una clase OrderAplication, because Resuelve el problema de la manera más sencilla y permite una mayor simplificación  del código.


### Consequences

* Good, because No implica una gran complicación a la hora de la creación de clases y código.
* Good, because Permite mantener la información en la base de datos posibilitando un análisis posterior de los datos y además, en caso de caída del sistema, el estado actual y el historial no se ven afectados.
* Bad, because No permite el cambio de estados de una manera dinámica en tiempo de ejecución.

### Confirmation

Aunque la implementación del patrón Observer o el patrón State son buenas opciones, estos se encargan de dinámicamente actuar de una forma u otra según cambios de estados en tiempo de ejecución, cosa que no es necesaria. Por lo que la opción más viable y simple sería la creación de la clase OrderAplication.


## Pros and Cons of the Options

### 0003-1 Patrón observer.

Este patrón se encarga de avisar a un objeto en caso de que el objeto al que este observando le suceda un evento. 

* Good, because Permite un cierto nivel de desacoplamiento permitiendo modificar funcionalidades sin que afecten al código principal.
* Good, because Permite añadir nuevos observadores sin cambiar la lógica del sistema.
* Bad, because Puede permitir bajada del rendimiento en caso de cambios de estados frecuentes y/o muchos observadores simultáneos.
* Bad, because Baja flexibilidad de un comportamiento dinámico negando la posibilidad de, al distinguir las lógicas en cada estado, cambiar las funciones de los objetos según cambios en los estados en tiempo de ejecución.

### 0003-2 Creación de una clase OrderAplication.

Esta opción se basa en crear una clase para guardar el estado de los pedidos, además de toda la información de estos, para según el estado en el que se encuentra (el valor de un atributo) se haga un código u otro.

* Good, because No implica una gran complicación a la hora de la creación de clases y código.
* Good, because Permite mantener la información en la base de datos posibilitando un análisis posterior de los datos y además, en caso de caída del sistema, el estado actual y el historial no se ven afectados.
* Bad, because No permite el cambio de estados de una manera dinámica en tiempo de ejecución.

### 0003-3 Patrón State.

Este patrón permite cambiar las funcionalidades de los objetos según en qué estado se encuentre, implementando el concepto de la Maquina de estados finitos.

* Good, because El hecho de que cada estado tenga su propia clase y por ende su propio código independiente proporciona una fácil adición de nuevos estados, una mayor claridad, una mayor mantenibilidad y organización.
* Good, because Proporciona una gran flexibilidad permitiendo que un objeto cambie de estados en tiempo de ejecución. 
* Bad, because Requiere una mayor complejidad en la estructura de las clases, ya que requiere una clase por cada estado posible.
* Bad, because Produce un mayor costo de memoria al crear y mantener instancias de varias clases de estados.



## More Information

Esta solución también realiza la funcionalidad pedida de poner un máximo de intentos por pedido para un cliente al contar con un estado para esta opción. Así como la actualización de las estadísticas para los clientes dado que al pasar de un estado a otro se modificarán.