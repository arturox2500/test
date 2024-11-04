---
status: {pending}
date: {2024-10-31}
decision-makers: {Iván Gutiérrez González, Arturo Enrique Gutiérrez Mirandona}
informed: {Elinne Nathalie Freites Muñoz, Jorge Cimadevilla Aniz}
--- 

# Realizar pedidos de productos (RF-4)

## Context and Problem Statement

El sistema debe permitir que el cliente haga o encargue pedidos de productos de forma directa desde la plataforma. Este requisito es obligatorio para el correcto funcionamiento del sistema de gestión de pedidos y ventas.

## Decision Drivers

* RF-4: Realizar pedidos de productos.


## Considered Options

* 0004-1: Implementar la funcionalidad de pedidos de productos mediante un flujo en la interfaz de usuario que guíe al cliente a través del proceso de autenticación, selección de productos, y pago.
* 0004-2: Implementar la funcionalidad de pedidos de productos mediante una API externa que permita integraciones con otras plataformas, facilitando pedidos a través de distintos canales.

## Decision Outcome

Chosen option: 0004-1 - Implementación en la interfaz de usuario con flujo guiado, porque proporciona una experiencia directa y sencilla para el cliente en la plataforma.

### Consequences

* Good, because mejora la experiencia del usuario al tener un flujo de pedidos intuitivo y fácil de seguir.
* Bad, because limita la flexibilidad de integración con plataformas externas.

### Confirmation

La implementación se confirmará mediante pruebas de funcionalidad y usabilidad, asegurando que el proceso de pedidos sea accesible y fácil de completar para el cliente.

## Pros and Cons of the Options

### 0004-1 - Implementación en la interfaz de usuario con flujo guiado

* Good, because facilita la navegación y seguimiento del proceso de compra para los usuarios dentro de la misma plataforma.
* Good, because permite una mayor personalización del flujo de pedidos, ajustándose a las necesidades de los clientes de la compañía.
* Bad, because la falta de integración con otras plataformas limita el alcance de pedidos a la interfaz de la plataforma.

### 0004-2 - Implementación mediante una API externa

* Good, because facilita la integración con otras plataformas, lo que permite realizar pedidos desde múltiples canales.
* Good, because aumenta la flexibilidad del sistema al permitir extensiones en el futuro para nuevos tipos de plataformas.
* Bad, because la experiencia del usuario puede ser menos intuitiva y dependerá de la calidad de las plataformas externas.
* Bad, because podría incrementar la complejidad de las configuraciones y el mantenimiento técnico.