---
status: {accepted}
date: {2024-11-15}
decision-makers: {Iván Gutiérrez González, Arturo Enrique Gutiérrez Mirandona}
consulted: {Elinee Nathalie Freites Muñoz, Jorge Cimadevilla Aniz}
informed: {Víctor Bartolomé Letosa, Alejandro Valor González}
---

# Gestión de Incidencias

## Context and Problem Statement

Se requiere una solución para gestionar las incidencias en el sistema de manera eficiente, permitiendo a los administradores reportar y redireccionar incidencias cuando sea necesario.

## Decision Drivers

* RF-6: Funcionalidad de gestor de incidencias para reportar y redireccionar problemas.
* RF-6.1: Necesidad de contactar con un equipo especializado en caso de incidencias complejas.
* RF-6.2: Comunicación con el cliente para notificar la resolución de la incidencia.

## Considered Options

* 0007-1 - Implementación del patrón Observer para notificaciones de cambios en las incidencias.
* 0007-2 - Uso de una clase de gestión de incidencias con métodos especializados.
* 0007-3 - Implementación del patrón Chain of Responsibility junto con una clase de gestión de incidencias

## Decision Outcome

Chosen option: 0007-3 - Implementación del patrón Chain of Responsibility junto con una clase IncidenciasManager.

### Consequences

* Good, porque el patrón Chain of Responsibility permite gestionar y redirigir incidencias de forma flexible, asignando cada tipo al equipo adecuado según su gravedad.
* Good, porque la clase IncidenciasManager centraliza las notificaciones de resolución de incidencias, facilitando la comunicación con los usuarios.
* Bad, porque una mala estructuración de la cadena de manejadores podría generar redundancias en la gestión, afectando la eficiencia.

### Confirmation

La implementación será verificada mediante pruebas unitarias y de integración para asegurar que el patrón Chain of Responsibility maneja correctamente las redirecciones de incidencias y que la clase IncidenciasManager gestiona correctamente la comunicación con los usuarios.

## Pros and Cons of the Options

### 0007-1 - Implementación del patrón Observer para notificaciones de cambios en las incidencias

* Good, because permite enviar notificaciones automáticas a los componentes interesados en los cambios de estado de las incidencias.
* Good, because separa la gestión de incidencias de los componentes que las reciben, brindando mayor flexibilidad.
* Bad, because aumenta la complejidad del sistema al requerir la gestión de observadores y notificaciones.


### 0007-2 - Uso de una clase de gestión de incidencias con métodos especializados

* Good, because centraliza la gestión de incidencias y facilita el mantenimiento.
* Good, because permite implementar métodos específicos para reportar y redireccionar incidencias sin añadir complejidad.
* Bad, because puede requerir modificaciones futuras para adaptarse a mayores volúmenes de incidencias.

### 0007-3 - Implementación del patrón Chain of Responsibility junto con una clase de gestión de incidencias

* Good, because Chain of Responsibility permite gestionar incidencias de manera flexible y escalable, redirigiéndolas según el tipo sin cambiar la lógica central.
* Good, because IncidenciasManager centraliza las notificaciones a los usuarios sobre la resolución de incidencias.
* Bad, because demasiados manejadores pueden complicar el flujo y afectar la eficiencia, especialmente con incidencias complejas.