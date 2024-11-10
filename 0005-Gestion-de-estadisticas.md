---
status: {accepted}
date: {2024-11-10}
decision-makers: {Iván Gutiérrez González, Arturo Enrique Gutiérrez Mirandona}
consulted: {Elinee Nathalie Freites Muñoz, Jorge Cimadevilla Aniz}
informed: {Víctor Bartolomé Letosa, Alejandro Valor González}
---

# Gestión y generación de las estadisticas

## Context and Problem Statement

El problema a resolver es gestionar y generar estadísticas en tiempo real sobre el estado de los pedidos, la situación de los camiones y otros aspectos del sistema, proporcionando actualizaciones automáticas a los componentes interesados para mantenerlos informados con los datos más actuales.

## Decision Drivers

* RF-5.1: Gestor de estadísticas para las rutas.
* RF-5.2: Generación de estadísticas para los usuarios.

## Considered Options

* 0005-1 - Implementación del patrón Observer
* 0005-2 - Uso de una clase intermediaria gestionar estadísticas. 
* 0005-3 - Implementación del patrón Publisher-Subscriber

## Decision Outcome

Chosen option: 0005-2 - Uso de la clase intermediaria para gestionar estadísticas, because Permite organizar las estadísticas de manera centralizada, reduciendo la complejidad y facilitando el mantenimiento. 

### Consequences

* Good, because EstadisticasManager centraliza la lógica de generación de estadísticas, reduciendo la complejidad de los servicios de negocio.
* Good, because La escalabilidad del sistema, ya que EstadisticasManager puede ser extendida para generar nuevas estadísticas sin necesidad de modificar otros módulos.
* Bad, because Puede requerir un diseño cuidadoso para optimizar las consultas a los repositorios y evitar cargas innecesarias en el sistema de bases de datos.

### Confirmation

La implementación será verificada mediante pruebas de integración para asegurar que las actualizaciones en tiempo real se distribuyen correctamente a todos los componentes interesados.

## Pros and Cons of the Options

### 0005-1 - Implementación del patrón Observer

El patrón Observer se utilizará para que los componentes que generan estadísticas notifiquen automáticamente a los módulos interesados cuando haya cambios en la información relevante, como el estado de los pedidos o la ubicación de los camiones.

* Good, because Permite que los módulos de estadísticas envíen actualizaciones en tiempo real sin necesidad de intervenciones manuales.
* Good, because Desacopla los componentes generadores de estadísticas de los consumidores, permitiendo una mayor flexibilidad y escalabilidad en el sistema.
* Good, because Mejora la sincronización entre los módulos del sistema al garantizar que todos los componentes estén actualizados con la misma información.
* Bad, because Puede aumentar la complejidad del sistema si no se gestionan adecuadamente los observadores y las notificaciones, especialmente cuando hay un gran volumen de componentes interesados.

### 0005-2 - Uso de una clase intermediaria gestionar estadísticas.

StatisticsManager interactúa con UserRepository y Order Repository para obtener la información necesaria y expone métodos especializados para generar estadísticas de clientes y pedidos (por ejemplo, generateStatisticsClients y generateStatisticsOrders).

* Good, because EstadisticasManager centraliza la lógica de generación de estadísticas, reduciendo la complejidad de los servicios de negocio.
* Good, because La clase intermediaria permite la recolección y procesamiento de datos de manera eficiente, obteniendo la información directamente de los repositorios sin afectar la cohesión de los servicios de negocio.
* Good, because La escalabilidad del sistema, ya que EstadisticasManager puede ser extendida para generar nuevas estadísticas sin necesidad de modificar otros módulos.
* Bad, because Puede requerir un diseño cuidadoso para optimizar las consultas a los repositorios y evitar cargas innecesarias en el sistema de bases de datos.


### 0005-3 - Implementación del patrón Publisher-Subscriber

El patrón Publisher-Subscriber también podría ser utilizado para la distribución de estadísticas en tiempo real. En este caso, los publicadores generan eventos que se distribuyen a través de un canal de eventos, permitiendo que los suscriptores los reciban automáticamente.

* Good, because Permite una comunicación eficiente entre los componentes sin que los suscriptores necesiten realizar solicitudes continuas.
* Good, because Permite que los suscriptores reaccionen en tiempo real a los cambios de estadísticas.
* Good, because Permite un control centralizado sobre qué componentes reciben las actualizaciones.
* Bad, because La gestión de los suscriptores podría ser más compleja, especialmente cuando el número de componentes interesados aumenta significativamente, lo que podría impactar el rendimiento.
