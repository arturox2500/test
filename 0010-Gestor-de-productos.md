---
status: {accepted}
date: {2024-11-23}
decision-makers: {Iván Gutiérrez González, Arturo Enrique Gutiérrez Mirandona}
consulted: {Elinee Nathalie Freites Muñoz, Jorge Cimadevilla Aniz}
informed: {Víctor Bartolomé Letosa, Alejandro Valor González}
---

# Gestor de productos

## Context and Problem Statement

Este problema se basa en la necesidad de gestionar los productos de la manera más simple posible, ya que esto es imprescindible para un sistema de venta y reparto de productos. 

## Decision Drivers

* RF-10: Gestor de productos.
* RF-10.1: Gestor de precios y ofertas.
* RF-10.2: Gestor de inventario.
* RF-10.3: Gestor de pedidos a fábrica/almacén.

## Considered Options

* 0010-1 Creación de una clase ProductManager.
* 0010-2 Patrón Facade.

## Decision Outcome

Chosen option: 0010-1 Creación de una clase ProductManager, because centraliza la lógica de productos y es la solución más sencilla de implementar y diseñar.

### Consequences

* Good, because Centraliza la lógica de los productos.
* Good, because Facilita el diseño y su implementación.
* Bad, because Permite una escasa escalabilidad.

### Confirmation

Como se ha mencionado antes, esta es la solución más óptima para este problema, aunque el patrón Facade sería una buena opción e incluso la opción ideal si se buscará una mayor escalabilidad para estas funcionalidades.

## Pros and Cons of the Options

### 0010-1 Creación de una clase ProductManager.

Esta solución se basa en la creación de una clase para interferir en todas las acciones referentes a los productos.

* Good, because Centraliza la lógica de los productos.
* Good, because Facilita el diseño y su implementación.
* Bad, because Permite una escasa escalabilidad.

### 0010-2 Patrón Facade.

Este patrón se basa en la creación de una interfaz, a la accede el usuario, que se encarga de, según qué acción (relacionada con precios o ventas, inventario o temas relacionado con el almacén), llamará a una clase o a otra.

* Good, because Facilita la expansión.
* Good, because Conlleva una interfaz simplificada para acceder a las funcionalidades de los productos.
* Bad, because Complica innecesariamente el diseño e implementación.

## More Information

Aunque esta decisión de basa en un requisito funcional no especificado literalmente en el anexo de la práctica esto es fundamental para el sistema como se ha mencionado en la cabecera. Se debería tener una forma de controlar los productos que se le venden y reparten a los clientes.
