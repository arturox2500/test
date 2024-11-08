---
status: {accepted}
date: {2024-11-09}
decision-makers: {Iván Gutiérrez González, Arturo Enrique Gutiérrez Mirandona}
informed: {Elinne Nathalie Freites Muñoz, Jorge Cimadevilla Aniz}
---

# Implementación de patrones de diseño para la generación de estadísticas en tiempo real

## Context and Problem Statement

En la arquitectura de microservicios de la compañía de productos alimenticios, es necesario gestionar y generar estadísticas en tiempo real sobre el estado de los pedidos, la situación de los camiones y otros aspectos del sistema. El módulo de estadísticas debe proporcionar actualizaciones automáticas a los componentes interesados para que estén al tanto de la información más actualizada.

## Decision Drivers

* RF-5.1: Gestor de estadísticas para las rutas.

## Considered Options

* 0005-1 - Implementación del patrón Observer
* 0005-2 - Implementación del patrón Publisher-Subscriber

## Decision Outcome

Chosen option: 0005-1 - Implementación del patrón Observer, because Facilita una actualización en tiempo real de las estadísticas, desacoplando los componentes que generan las actualizaciones de aquellos que las consumen, y mejorando la sincronización entre los diferentes módulos del sistema.

### Consequences

* Good, because Permite la actualización en tiempo real de las estadísticas sin necesidad de que los componentes consumidores soliciten la información continuamente.
* Good, because Facilita que los módulos interesados en las estadísticas, como los camiones o el estado de los pedidos, reaccionen de manera inmediata a los cambios operativos.
* Good, because Mejora la escalabilidad al permitir que se añadan nuevos observadores sin necesidad de modificar los componentes generadores de estadísticas.
* Bad, because Puede requerir un esfuerzo inicial significativo para garantizar que los cambios en el sistema estén bien definidos y notificados de manera eficiente.

### Confirmation

La implementación será verificada mediante pruebas de integración para asegurar que las actualizaciones en tiempo real se distribuyen correctamente a todos los componentes interesados. Además, se realizarán pruebas de carga para evaluar el rendimiento del sistema bajo alta demanda de actualizaciones.

## Pros and Cons of the Options

### 0005-1 - Implementación del patrón Observer

El patrón Observer se utilizará para que los componentes que generan estadísticas notifiquen automáticamente a los módulos interesados cuando haya cambios en la información relevante, como el estado de los pedidos o la ubicación de los camiones.

* Good, because Permite que los módulos de estadísticas envíen actualizaciones en tiempo real sin necesidad de intervenciones manuales.
* Good, because Desacopla los componentes generadores de estadísticas de los consumidores, permitiendo una mayor flexibilidad y escalabilidad en el sistema.
* Good, because Mejora la sincronización entre los módulos del sistema al garantizar que todos los componentes estén actualizados con la misma información.
* Bad, because Puede aumentar la complejidad del sistema si no se gestionan adecuadamente los observadores y las notificaciones, especialmente cuando hay un gran volumen de componentes interesados.

### 0005-2 - Implementación del patrón Publisher-Subscriber

El patrón Publisher-Subscriber también podría ser utilizado para la distribución de estadísticas en tiempo real. En este caso, los publicadores generan eventos que se distribuyen a través de un canal de eventos, permitiendo que los suscriptores los reciban automáticamente.

* Good, because Permite una comunicación eficiente entre los componentes sin que los suscriptores necesiten realizar solicitudes continuas.
* Good, because Permite que los suscriptores reaccionen en tiempo real a los cambios de estadísticas.
* Good, because Permite un control centralizado sobre qué componentes reciben las actualizaciones.
* Bad, because La gestión de los suscriptores podría ser más compleja, especialmente cuando el número de componentes interesados aumenta significativamente, lo que podría impactar el rendimiento.
