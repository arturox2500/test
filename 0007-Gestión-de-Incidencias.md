---
status: {accepted}
date: {2024-11-14}
decision-makers: {Iván Gutiérrez González, Arturo Enrique Gutiérrez Mirandona}
consulted: {Elinee Nathalie Freites Muñoz, Jorge Cimadevilla Aniz}
informed: {Víctor Bartolomé Letosa, Alejandro Valor González}
---

# Gestión de Incidencias

## Context and Problem Statement

Se requiere una solución para gestionar incidencias en el sistema que permita notificar rápidamente a los gestores de rutas sobre problemas que puedan afectar la operación (camión averiado, reparto no realizado y reparto realizado).

## Decision Drivers

* RF-6: Gestor de incidencias.

## Considered Options

* 0007-1 - Implementación del patrón Publisher-Subscriber.
* 0007-2 - Creación de una clase de gestión de incidencias.

## Decision Outcome

Chosen option: 0007-2 - Creación de una clase de gestión de incidencias, because Permite una comunicación directa y sencilla con la clase de gestión de rutas sin agregar complejidad innecesaria al sistema.

### Consequences

* Good, because Una clase dedicada permite un control directo y sencillo de la comunicación, manteniendo la simplicidad.
* Good, because Facilita el mantenimiento al centralizar la lógica de notificación en una clase.
* Bad, because Limita la flexibilidad para agregar otros módulos que podrían beneficiarse de recibir notificaciones de incidencias.

### Confirmation

La implementación será verificada mediante pruebas unitarias para asegurar que la clase de incidencias se comunica correctamente con la clase de gestión de rutas.

## Pros and Cons of the Options

### 0007-1 - Clase de gestión de incidencias con métodos directos para notificar a la clase de rutas
Permite que múltiples componentes se suscriban para recibir notificaciones de incidencias de forma extensible.

* Good, because La comunicación directa con la clase de rutas simplifica el diseño.
* Good, because Centraliza el control de las notificaciones, facilitando la gestión y el mantenimiento.
* Bad, because Limita la capacidad de escalar la notificación a otros componentes que podrían beneficiarse de recibir información sobre incidencias.

### 0007-2 - Implementación del patrón Publisher-Subscriber
Proporciona una comunicación directa y simplificada con la clase de gestión de rutas, manteniendo el sistema sencillo.

* Good, because El patrón Publisher-Subscriber permite que múltiples servicios o clases se suscriban a las notificaciones de incidencias sin modificar la lógica central.
* Good, because Facilita una arquitectura más extensible, permitiendo que en el futuro otros módulos puedan recibir alertas de incidencias.
* Bad, because Añade complejidad en la gestión de suscriptores y en la configuración inicial del patrón.

