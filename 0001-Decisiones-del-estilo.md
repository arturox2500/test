---
status: {proposed}
date: {2024-10-29}
decision-makers: {Iván Gutiérrez Gonzáles, Arturo Enrique Gutiérrez Mirandona}
informed: {Elinne Nathalie Freites Muñoz, Jorge Cimadevilla Aniz}
---

# Selección-Estilo-Arquitectónico

## Context and Problem Statement

El problema definido a continuación es la decisión sobre que estilo arquitectónico se va a seleccionar para resolver el problema propuesto.

## Considered Options

* 0001-1-Estilo-Cliente-Servidor
* 0001-2-Estilo-REST

## Decision Outcome

Chosen option: "0001-1-Estilo-Cliente-Servidor", because Permite el uso de estados simplificando el sistema y permitiendo un menor uso de información en cada petición, y además nos da una mayor seguridad y una menor redundancia en los datos.

### Consequences

* Good, because El centralismo en la parte del servidor da ventajas como la seguridad, la menor repetición de la información.
* Good, because Permite una gran escalabilidad, flexibilidad y portabilidad.
* Good, because Permite el uso de estados facilitando la complejidad en sesiones largas, transacciones, etc.
* Bad, because Posee una mayor dependencia del trafico en la red al tener más intercambios de información entre las partes.

### Confirmation

El estilo REST tiene una mayor escalabilidad, flexibilidad y portabilidad que el estilo cliente-servidor, pero para el sistema a construir es más inteligente el uso de estados ya que las principales funciones del sistema requieren unas sesiones largas entre el cliente y el servidor.

## Pros and Cons of the Options

### 0001-1-Estilo-Cliente-Servidor: 

Arquitectura la cual separa claramente las responsibilidades en el servidor y el cliente. Cada uno tiene funciones específicas y se comunican entre sí a través de una red (generalmente Internet).

* Good, because Permite una buena escalabilidad, podiendo aumentar la capacidad de clientes y servidores por separado.
* Good, because El centralismo en el servidor facilita la seguridad,  un bajo riesgo de posible redundancia en los datos, etc.
* Good, because Permite el uso de estados dentro del sistema ayudando a guardar la información del usuario a través del sistema.
* Good, because Permite la interoperabilidad pudiendose ejecutar en diferentes plataformas y/o dispositivos.
* Neutral, because El sistema tiene una gran dependecia con el servidor y si este deja de funcionar afectará a toda la infraestructura además de tener un mayor coste, pero también ayuda al mantenimiento (sobretodo en actualizaciones en el servidor) y a la seguridad (dejando un mecanismo central de autenticación).
* Bad, because Depende del tráfico de la red permitiendo posibles perdidas de información.

### 0001-2-Estilo-REST:

Arquitectura basada en el estilo Cliente-Servidor, pero con ciertas diferencias definidas posteriormente.

* Good, because Permite una gran escalabilidad en los sistemas.
* Good, because Permite una mayor flexibilidad y portabilidad al dar toda la información en cada petición posibilitando, entre otras cosas, alojar el front y el back en diferentes servidores.
* Good, because Al no tener estados se baja la cantidad de memoria que necesita el servidor.
* Neutral, because No posee una centralización del sistema en el servidor dejando parte de la estructura a crear para el cliente, pero es una bueno al no hacer que el sistema dependa completamente de una sola parte.
* Bad, because No tiene estados, teniendo que incluir toda la información en cada petición resultando en más complijidad para eliminar puntos de fallo.
* Bad, because No es ideal para operaciones complejas (sesiones largas, transacciones, etc) siendo más óptimos en operaciones independientes.