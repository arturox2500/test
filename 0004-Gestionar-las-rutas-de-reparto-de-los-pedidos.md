---
status: {accepted}
date: {2024-11-10}
decision-makers: {Iván Gutiérrez González, Arturo Enrique Gutiérrez Mirandona}
consulted: {Elinee Nathalie Freites Muñoz, Jorge Cimadevilla Aniz}
informed: {Víctor Bartolomé Letosa, Alejandro Valor González}
---

# Implementación de patrones de diseño para la decisión de rutas de reparto

## Context and Problem Statement

El problema a resolver es optimizar las rutas de reparto mediante un sistema que elija automáticamente entre dos algoritmos en función de la demora del camión y otros factores en tiempo real, mejorando así la eficiencia logística.

## Decision Drivers

* RF-4: Gestión de rutas de reparto.

## Considered Options

* 0004-1 - Implementación del patrón Strategy
* 0004-2 - Implementación del patrón Observer

## Decision Outcome

Chosen option: 0004-1 - Implementación del patrón Strategy, because Permite seleccionar y cambiar entre algoritmos de optimización de manera flexible según las condiciones operativas, sin intervención manual, y mejora la eficiencia en la asignación de rutas.

### Consequences

* Good, because Facilita la selección dinámica de algoritmos y adapta la planificación de rutas automáticamente según la situación de reparto.
* Good, because Mejora la eficiencia al aplicar el algoritmo adecuado en función de la situación.
* Good, because Simplifica la adición de nuevos algoritmos en el futuro sin afectar la estructura principal del sistema.
* Bad, because Requiere una clara definición y encapsulación de cada algoritmo para mantener la cohesión y evitar dependencias innecesarias.

### Confirmation

La implementación se verificará mediante pruebas de simulación de condiciones de reparto variables para asegurar que la selección de algoritmos es eficiente y adecuada según los estados operativos. Además, se realizará una revisión de código para garantizar que las estrategias están correctamente encapsuladas y pueden ser fácilmente intercambiadas.

## Pros and Cons of the Options

### 0004-1 - Implementación del patrón Strategy

Se propone el uso del patrón Strategy para seleccionar algoritmos de optimización de rutas, permitiendo cambios según la demora del camión o la carga de la flota. Esto proporciona adaptabilidad y facilita la incorporación de nuevos algoritmos en un futuro.

* Good, because Permite encapsular cada algoritmo de optimización como una estrategia separada, facilitando el cambio de algoritmos en tiempo de ejecución según las necesidades operativas.
* Good, because Ofrece una estructura flexible que simplifica la adición de nuevos algoritmos en el futuro sin afectar la estructura principal.
* Good, because Mejora la eficiencia al aplicar el algoritmo adecuado en función de la situación, optimizando los tiempos de entrega.
* Bad, because Puede requerir lógica adicional para decidir cuándo aplicar cada algoritmo de optimización.
* Bad, because Requiere una clara definición y encapsulación de cada algoritmo para mantener la cohesión y evitar dependencias innecesarias.

### 0004-2 - Implementación del patrón Observer

Se propone implementar el patrón Observer para monitorear las rutas de reparto y las condiciones de los pedidos. Este patrón permite que los componentes reaccionen automáticamente a cambios en las condiciones de la ruta, como demoras o disponibilidad de repartidores, facilitando una adaptación inmediata del sistema a nuevas circunstancias.

* Good, because Permite actualizar en tiempo real las condiciones de reparto, lo que facilita una respuesta rápida ante cambios operativos.
* Good, because Desacopla la lógica de actualización, permitiendo que los componentes que dependen de las condiciones de reparto reciban información de manera automática.
* Good, because Mejora la sincronización entre diferentes componentes del sistema, asegurando que todos los módulos relevantes estén al tanto de los cambios en las rutas o demoras.
* Bad, because Requiere que los componentes interesados implementen lógica para reaccionar adecuadamente a los cambios notificados.
* Bad, because Puede aumentar la complejidad del sistema al manejar múltiples observadores y notificaciones, lo que podría impactar el rendimiento si no se gestiona correctamente.

