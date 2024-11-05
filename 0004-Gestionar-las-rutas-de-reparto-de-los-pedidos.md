---
status: {proposed}
date: {2024-11-05}
decision-makers: {Iván Gutiérrez González, Arturo Enrique Gutiérrez Mirandona}
informed: {Elinne Nathalie Freites Muñoz, Jorge Cimadevilla Aniz}
--- 

# Implementación de la funcionalidad para gestionar rutas de reparto de pedidos (RF-7)

## Context and Problem Statement

En la nueva arquitectura basada en microservicios de la compañía de productos alimenticios, es necesario implementar la funcionalidad que permita a los administradores gestionar y modificar las rutas de reparto de los pedidos. Esto es crucial para mantener flexibilidad en la asignación de rutas de entrega y optimizar el proceso de reparto. Además, garantizar la coherencia en la planificación de rutas puede mejorar los tiempos de entrega y la satisfacción del cliente.

## Decision Drivers

* RF-4: Gestión de rutas de reparto.

## Considered Options

* 0004-1 - Implementación de un sistema de gestión de rutas en la interfaz de usuario: Permitir a los administradores modificar las rutas de reparto directamente desde la interfaz gráfica, con opciones de selección de rutas y asignación de repartidores.
* 0004-2 - Optimización de rutas mediante selección adaptativa de algoritmos: Implementar un sistema que optimice automáticamente las rutas de reparto mediante algoritmos adaptativos, ajustando la planificación en función de la demora del camión y disponibilidad de repartidores, con mínima intervención manual.
* 0004-3 - Integración con un servicio externo de optimización de rutas: Utilizar un servicio externo especializado en planificación de rutas para gestionar de forma dinámica las asignaciones de repartidores.

## Decision Outcome

Chosen option: 0006-2 - Optimización de rutas mediante selección adaptativa de algoritmos, because reduce la intervención manual y mejora la eficiencia en la asignación de rutas al sugerir opciones optimizadas basadas en datos de localización y disponibilidad.

### Consequences

* Good, because reduce la intervención manual al sugerir rutas automáticamente, mejorando la eficiencia en la planificación de reparto.
* Bad, because limita la flexibilidad de los administradores para ajustar rutas específicas en tiempo real si las condiciones cambian drásticamente.


### Confirmation

La implementación se verificará mediante pruebas de usabilidad y simulaciones de reparto para asegurar que la gestión de rutas es eficiente y que la interfaz permite una gestión intuitiva y ágil.

## Pros and Cons of the Options

### 0004-1 - Implementación de un sistema de gestión de rutas en la interfaz de usuario

* Good, because permite al administrador modificar rutas en tiempo real según las condiciones y disponibilidad de repartidores.
* Good, because ofrece un alto nivel de control sobre la planificación de rutas, asegurando una gestión precisa.
* Bad, because requiere intervención manual continua, lo que podría aumentar la carga de trabajo de los administradores.
* Bad, because la dependencia de intervención humana podría generar errores si no se actualizan correctamente las rutas.

### 0004-2 - Optimización de rutas mediante selección adaptativa de algoritmos

* Good, because reduce la intervención manual al sugerir rutas automáticamente, mejorando la eficiencia en la planificación de reparto.
* Good, because facilita la asignación de rutas basadas en datos, mejorando la precisión en la estimación de tiempos de entrega.
* Bad, because limita la flexibilidad de los administradores para ajustar rutas específicas si las condiciones cambian drásticamente.

### 0004-3 - Integración con un servicio externo de optimización de rutas

* Good, because aprovecha tecnología avanzada de optimización, lo que podría reducir los tiempos de entrega y mejorar la eficiencia.
* Good, because disminuye la carga de trabajo de los administradores, delegando la planificación a un servicio especializado.
* Bad, because dependenderia de un proveedor externo, lo que puede tener implicaciones de costos y confiabilidad.
* Bad, because puede limitar la capacidad de hacer ajustes específicos en función de las necesidades de la empresa.

## More Information
Los administradores deberán iniciar sesión con permisos elevados para acceder a esta funcionalidad, y cualquier modificación de rutas quedará registrada para mantener un historial de cambios.
