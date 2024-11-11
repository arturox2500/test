---
status: {accepted}
date: {2024-11-15}
decision-makers: {Iván Gutiérrez González, Arturo Enrique Gutiérrez Mirandona}
consulted: {Elinee Nathalie Freites Muñoz, Jorge Cimadevilla Aniz}
informed: {Víctor Bartolomé Letosa, Alejandro Valor González}
---

# Conexión con la pasarela de pago

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

### Opción 1: Clase PaymentGateway como microservicio externo

- Descripción: Crear una clase PaymentGateway que funcione como intermediario para gestionar pagos. Esta clase podría interactuar con una API de pasarela de pago externa como Stripe (según la especificación) para procesar las transacciones de manera segura.

- Clases relacionadas:

 * * PaymentGateway: Incluye métodos como processPayment(amount, customer) y savePaymentData(customer, paymentInfo).

 * * Customer: La clase Customer se relacionaría con PaymentGateway para realizar pagos. Se podría añadir el método makePayment(amount).

- Ventajas: Separa las preocupaciones de seguridad y procesamiento de pagos del resto del sistema, y permite utilizar una API de pagos externa.

- Desventajas: Aumenta la complejidad, ya que depende de un sistema externo.

### Opción 2: Interfaz IPaymentProcessor con implementación de PaymentGateway

- Descripción: Crear una interfaz IPaymentProcessor que defina los métodos relacionados con los pagos (processPayment, savePaymentData) y luego implementar esta interfaz en la clase PaymentGateway.

- Clases relacionadas:

 * * IPaymentProcessor (interfaz): Define métodos de pago como processPayment y savePaymentData.

 * * PaymentGateway (implementación): Implementa IPaymentProcessor y maneja los detalles de interacción con la pasarela externa.

- Ventajas: Facilita la extensión y el cambio de proveedor de pago si es necesario en el futuro.

- Desventajas: La implementación de la interfaz añade un nivel adicional de abstracción, lo cual puede ser innecesario en sistemas más simples.

### Opción 3: Método makePayment directamente en la clase Customer

- Descripción: Agregar métodos directamente en la clase Customer para procesar el pago y guardar los datos del cliente si se requiere autoguardado de información.

- Clases relacionadas:

 * * Customer: Añadir métodos makePayment(amount) y savePaymentData(paymentInfo) dentro de Customer.

- Ventajas: Simplifica la lógica de pagos al no necesitar clases adicionales.

- Desventajas: Mezcla la lógica de negocio del cliente con la de pagos, lo que puede dificultar la separación de responsabilidades.
