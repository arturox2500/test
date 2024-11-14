---
status: {accepted}
date: {2024-11-14}
decision-makers: {Iván Gutiérrez González, Arturo Enrique Gutiérrez Mirandona}
consulted: {Elinee Nathalie Freites Muñoz, Jorge Cimadevilla Aniz}
informed: {Víctor Bartolomé Letosa, Alejandro Valor González}
---

# Conexión con la pasarela de pago

## Context and Problem Statement

El problema a resolver es que tipo de API usar para hacer uso de una pasarela de pago proporcionada por la empresa STRIPE

## Decision Drivers

* RF-7: Uso de una pasarela de pago.
* RF-7.1: Autoguardado de datos de pago por cliente.
* RD-2: Relación con la empresa STRIPE para la pasarela de pagos.

## Considered Options

* 0008-1-Utilización de Setup Intents API
* 0008-2-Utilización de Stripe Checkout

## Decision Outcome

Chosen option: 0008-1-Utilización de Setup Intents API, because Nos permite el guardado del método de pago del cliente y es ideal para pagos recurrentes como es la compra de múltiples productos.

### Consequences

* Good, because Permite guardar el método del pago del cliente.
* Good, because Es ideal para pagos recurrentes.
* Good, because Posee una alta compatibilidad y seguridad.
* Bad, because Conlleva una complejidad extra al no realizar el cargo inicial.

### Confirmation

Aunque ambas APIs proveen una alta compatibilidad y seguridad a la hora del pago, el método escogido nos resuelve los dos requisitos funcionales de una vez.

## Pros and Cons of the Options

### 0008-1-Utilización de Setup Intents API

La Setup Intents API está diseñada para guardar métodos de pago de manera segura sin procesar un pago inmediato.

* Good, because Permite guardar el método del pago del cliente.
* Good, because Es ideal para pagos recurrentes.
* Good, because Posee una alta compatibilidad y seguridad.
* Bad, because Conlleva una complejidad extra al no realizar el cargo inicial.

### 0008-2-Utilización de Stripe Checkout

La Stripe Checkout es una API que se relaciona con la empresa STRIPE ideal para el uso de multiples métodos de pago.

* Good, because Es fácil de implementar.
* Neutral, because Posee una alta compatibilidad y seguridad.
* Bad, because No permite el autoguardado del método de pago.
