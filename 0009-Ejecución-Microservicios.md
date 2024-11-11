---
status: {accepted}
date: {2024-11-15}
decision-makers: {Iván Gutiérrez González, Arturo Enrique Gutiérrez Mirandona}
consulted: {Elinee Nathalie Freites Muñoz, Jorge Cimadevilla Aniz}
informed: {Víctor Bartolomé Letosa, Alejandro Valor González}
---

# Ejecución de microservicios

## Context and Problem Statement

{Describe the context and problem statement, e.g., in free form using two to three sentences or in the form of an illustrative story. You may want to articulate the problem in form of a question and add links to collaboration boards or issue management systems.}


## Decision Drivers

* {decision driver 1, e.g., a force, facing concern, …}
* {decision driver 2, e.g., a force, facing concern, …}


## Considered Options

* {title of option 1}
* {title of option 2}
* {title of option 3}


## Decision Outcome

Chosen option: "{title of option 1}", because {justification. e.g., only option, which meets k.o. criterion decision driver | which resolves force {force} | … | comes out best (see below)}.


### Consequences

* Good, because {positive consequence, e.g., improvement of one or more desired qualities, …}
* Bad, because {negative consequence, e.g., compromising one or more desired qualities, …}



### Confirmation

{Describe how the implementation of/compliance with the ADR can/will be confirmed. Is the chosen design and its implementation in line with the decision? E.g., a design/code review or a test with a library such as ArchUnit can help validate this. Note that although we classify this element as optional, it is included in many ADRs.}


## Pros and Cons of the Options

### {title of option 1}


{example | description | pointer to more information | …}

* Good, because {argument a}
* Good, because {argument b}
* Neutral, because {argument c}
* Bad, because {argument d}


### {title of other option}

{example | description | pointer to more information | …}

* Good, because {argument a}
* Good, because {argument b}
* Neutral, because {argument c}
* Bad, because {argument d}
* …

## More Information

### Opción 1: Clase MicroserviceManager

- Descripción: Crear una clase MicroserviceManager que centralice la ejecución y gestión de los microservicios, incluyendo su registro, disponibilidad y la ejecución de instancias.

- Clases relacionadas:
 
 * * MicroserviceManager: Podría incluir métodos como executeMicroservice(serviceName) y registerMicroservice(service).

 * * Customer o OrderApplication: Estas clases podrían llamar a MicroserviceManager para ejecutar microservicios específicos.

- Ventajas: Facilita la centralización y control de los microservicios en un solo componente.

- Desventajas: Si no se diseña correctamente, puede convertirse en un punto de fallo único o un cuello de botella.

### Opción 2: Interfaz IMicroservice y múltiples microservicios que la implementen

- Descripción: Crear una interfaz IMicroservice que defina los métodos básicos para cualquier microservicio, como start, stop, y execute. Luego, cada microservicio específico (como OrderService, RouteService, etc.) implementaría esta interfaz.

- Clases relacionadas:

 * * IMicroservice: Define la estructura base para microservicios.

 * * OrderService, RouteService, etc.: Implementan IMicroservice y se integran en el sistema.

- Ventajas: Cada microservicio puede desarrollarse, desplegarse y gestionarse de forma independiente.

- Desventajas: Aumenta el número de clases y complejidad de gestión.

### Opción 3: Métodos en OrderApplication o RoutesService para ejecución de microservicios específicos

- Descripción: Si la arquitectura de microservicios es relativamente simple, podrías agregar métodos de ejecución directamente en las clases de negocio principales, como OrderApplication o RoutesService.

- Clases relacionadas:

 * * OrderApplication: Podría tener métodos como executeOrderMicroservice.

 * * RoutesService: Podría tener métodos específicos para microservicios relacionados con la gestión de rutas.

- Ventajas: Simplifica la arquitectura, eliminando la necesidad de un gestor de microservicios o interfaces adicionales.
- Desventajas: Limita la extensibilidad y modularidad, ya que cada clase se encargará de ejecutar sus propios microservicios.