---
status: {accepted}
date: {2024-11-10}
decision-makers: {Iván Gutiérrez González, Arturo Enrique Gutiérrez Mirandona}
consulted: {Elinee Nathalie Freites Muñoz, Jorge Cimadevilla Aniz}
informed: {Víctor Bartolomé Letosa, Alejandro Valor González}
---

# Gestión de las Bases de Datos

## Context and Problem Statement

El sistema requiere un componente de gestión de bases de datos que permita acceder, almacenar y sincronizar la información de las bases de datos SQL de Clientes y Pedidos. Este componente debe ser flexible, escalable y compatible con una arquitectura de microservicios.

## Decision Drivers

* RF-2: Gestor de base de datos.


## Considered Options

* 0002-1: Utilizar Amazon RDS Data API.
* 0002-2: Utilizar Google Cloud SQL API.
* 0002-3: Utilizar ODBC.

## Decision Outcome

Chosen option: 0002-3 Usar ODBC, because Nos ofrece una solución multiplataforma y flexible que permite a la arquitectura de microservicios acceder a las bases de datos SQL de los clientes y de pedidos.

### Consequences

* Good, because Proporciona una solución multiplataforma y es compatible con numerosos sistemas de bases de datos SQL.
* Good, because ODBC es un estándar ampliamente soportado, lo cual facilita la integración con diversas herramientas y plataformas.
* Bad, because Puede ser menos eficiente en términos de rendimiento en comparación con APIs nativas, ya que introduce una capa adicional en la comunicación entre el servicio y la base de datos.

### Confirmation

La elección se confirmará mediante pruebas de conectividad, rendimiento y escalabilidad, asegurando que el acceso a las bases de datos sea eficiente y cumpla con los requisitos de la aplicación.

## Pros and Cons of the Options

### 0002-1 - Amazon RDS Data API

* Good, because Permite una administración centralizada y segura de bases de datos SQL en la nube de AWS.
* Good, because Simplifica la implementación de microservicios al usar conexiones sin estado mediante HTTP/REST.
* Bad, because Limita la flexibilidad del sistema a la infraestructura de AWS, dificultando una potencial migración a otro proveedor de nube.

### 0004-2 - Google Cloud SQL API

* Good, because Permite una integración fluida con los servicios de Google Cloud, siendo útil en entornos que ya operan en esa nube.
* Good, because Ofrece opciones avanzadas de recuperación ante desastres y alta disponibilidad.
* Bad, because También limita el sistema a un proveedor de servicios específico (Google Cloud).
* Bad, because Podría incrementar los costos de operación en comparación con otros proveedores.

### 0002-3 - ODBC

* Good, because Proporciona una solución multiplataforma y es compatible con numerosos sistemas de bases de datos SQL.
* Good, because Permite flexibilidad en entornos híbridos (local y en la nube), facilitando la interoperabilidad entre distintos proveedores.
* Bad, because Requiere configuraciones adicionales y puede introducir cierta latencia en comparación con las APIs específicas de la nube.
