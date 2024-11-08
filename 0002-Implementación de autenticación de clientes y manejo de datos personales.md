---
status: {accepted}
date: {2024-11-09}
decision-makers: {Iván Gutiérrez González, Arturo Enrique Gutiérrez Mirandona}
informed: {Elinne Nathalie Freites Muñoz, Jorge Cimadevilla Aniz}
---

# Gestión de las Bases de Datos

## Context and Problem Statement

El sistema requiere un componente de gestión de bases de datos que permita acceder, almacenar y sincronizar la información de las bases de datos SQL de Clientes y Pedidos. Este componente debe ser flexible, escalable y compatible con una arquitectura de microservicios.

## Decision Drivers

* RF-2: Gestor de base de datos.


## Considered Options

* 0002-1: Utilizar Amazon RDS Data API para gestionar el acceso y control de bases de datos SQL de manera segura y escalable en la nube de AWS.
* 0002-2: Implementar Google Cloud SQL API para la administración y acceso a bases de datos SQL con capacidades nativas de Google Cloud.
* 0002-3: Usar ODBC como una solución multiplataforma que facilite la interoperabilidad entre diferentes entornos y bases de datos SQL.

## Decision Outcome



### Consequences



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
* Bad, because Puede resultar más compleja de administrar en un entorno de microservicios en comparación con soluciones basadas en HTTP/REST.
