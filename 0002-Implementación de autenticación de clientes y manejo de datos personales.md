---
status: {accepted}
date: {2024-10-31}
decision-makers: {Iván Gutiérrez González, Arturo Enrique Gutiérrez Mirandona}
informed: {Elinne Nathalie Freites Muñoz, Jorge Cimadevilla Aniz}
--- 

# Implementación de autenticación de clientes (RF-1 y RF-2) y manejo de datos personales (RF-3, RF-3.1, RF-3.2)

## Context and Problem Statement

Para la nueva arquitectura basada en microservicios de la compañía de productos alimenticios, es necesario implementar funcionalidades básicas de autenticación, registro y gestión de datos personales para todos los roles involucrados (clientes, empleados y administradores). Esto permitirá un acceso seguro a la información personalizada, y garantizará la integridad de los datos de los usuarios.

## Decision Drivers

* RF-1: Iniciar sesión.
* RF-2: Registrarse.
* RF-3: Uso de datos personales de los clientes
* RF-3.1: Acceder datos personales de los clientes.
* RF-3.2: Modificar datos personales de los clientes.


## Considered Options

* 0002-1-Implementar un sistema de permisos basado en roles, con acceso y modificación de datos permitidos solo a los roles designados.
* 0002-2-Control de acceso mediante permisos asignados en la base de datos.

## Decision Outcome

Chosen option: 0002-1-Sistema de permisos basado en roles, because proporciona flexibilidad para gestionar acceso en función de rol, simplifica la administración de permisos y se alinea con los requisitos de seguridad.

### Consequences

* Good, because simplifica la gestión de permisos de acceso y modificación, facilitando el cumplimiento de las políticas de privacidad.
* Bad, because podría limitar la flexibilidad en configuraciones personalizadas de permisos específicos para cada rol.

### Confirmation

La implementación será confirmada mediante pruebas de integración y revisión de código para asegurar el cumplimiento de los requisitos de autenticación y seguridad.

## Pros and Cons of the Options

### 0002-1-Sistema de permisos basado en roles

* Good, because facilita la organización y revisión de permisos de manera escalable y centralizada.
* Good, because permite una gestión simplificada de los permisos al asignarlos a grupos de usuarios específicos.
* Bad, because requiere mantener roles actualizados con cambios en las políticas de la compañía.
* Bad, because podría limitar la capacidad de personalizar permisos a nivel individual.

### 0002-2-Control de acceso mediante permisos asignados en la base de datos

* Good, because permite un control directo desde la base de datos y centraliza la asignación de permisos en un solo lugar.
* Good, because centralizar los permisos en una base de datos facilita el seguimiento de accesos.
* Bad, because podría añadir dependencia en la base de datos para la administración de permisos y carece de flexibilidad para configuraciones dinámicas o de permisos por servicio.
* Bad, because podría ser menos eficiente si se requieren consultas frecuentes a la base de datos para verificar permisos en cada solicitud.

## More Information

Para una mayor definición de las acciones que se llevaran a cabo en esta base de datos es necesario entender que aquí se guardarán todos los datos de los clientes, empleados y administradores, siendo diferenciados por una extensión en sus nombres después del símbolo @. A la hora de las funciones todas estas las pueden llevan a cabo cada uno de los tipos de usuarios pero el hecho de modificar datos personales de otras cuentas esta solo permitido para administradores.
