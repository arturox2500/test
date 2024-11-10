---
status: {accepted}
date: {2024-11-10}
decision-makers: {Iván Gutiérrez González, Arturo Enrique Gutiérrez Mirandona}
consulted: {Elinee Nathalie Freites Muñoz, Jorge Cimadevilla Aniz}
informed: {Víctor Bartolomé Letosa, Alejandro Valor González}
---

# Gestión de los datos de los usuarios.

## Context and Problem Statement

El problema a resolver es la funcionalidad por la cual los usuarios guardan, modifican y acceden a sus datos, personales o relacionados con los pedidos.

## Decision Drivers

* RF-9: Gestor de usuarios.

## Considered Options

* 0006-1-Creación de la clase Customer.
* 0006-2-Acceso directo a la BBDD.

## Decision Outcome

Chosen option: 0006-1-Creación de la clase Customer, because Es la opción que menos tiempo requiere a la hora de ejecución para implementar la funcionalidad.

### Consequences

* Good, because Da sencillez al diseño y es fácil de integrar.
* Good, because Permite el almacenado de los datos en la BBDD permitiendo la persistencia de estos y siendo fiable frente a posibles caídas del sistema.
* Bad, because Posee una escasa flexibilidad para cambios.

### Confirmation

Aunque la implementación de la funcionalidad con el solo uso de la BBDD resolvería el requisito explicado, sería costoso en tiempo y no permite, prácticamente, ningún tipo de flexibilidad y escalabilidad.

## Pros and Cons of the Options

### 0006-1-Creación de la clase Customer.

Esta opción se basa en la implementación de una clase, con la que se realizara la funcionalidad utilizando sus atributos y métodos.

* Good, because Da sencillez al diseño y es fácil de integrar.
* Good, because Permite el almacenado de los datos en la BBDD permitiendo la persistencia de estos y siendo fiable frente a posibles caídas del sistema.
* Bad, because Posee una escasa flexibilidad para cambios.

### 0006-2-Acceso directo a la BBDD.

El acceso directo a la BBDD se basa en que desde esta se hagan todas los cambios y las consultas necesarias frente a cualquier problema.

* Good, because Permite la persistencia de estos y siendo fiable frente a posibles caidas del sistema.
* Bad, because No permite ningñun tipo de flexibilidad ni la posible adición de métodos.
* Bad, because Provocaría una gran cantidad de consultas a la BBDD implicando más tiempo de ejecución.

