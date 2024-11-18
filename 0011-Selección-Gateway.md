---
status: {accepted}
date: {2024-11-14}
decision-makers: {Iván Gutiérrez González, Arturo Enrique Gutiérrez Mirandona}
consulted: {Elinee Nathalie Freites Muñoz, Jorge Cimadevilla Aniz}
informed: {Víctor Bartolomé Letosa, Alejandro Valor González}
---

# Selección del componente Gateway  

## Context and Problem Statement  

El sistema requiere un componente Gateway que facilite el acceso desde los clientes PC y móvil utilizando HTTP/REST, asegurando integración con la arquitectura basada en microservicios.  

## Decision Drivers  

* RF-11: Uso de Gateway.

## Considered Options  

* 0009-1: AWS API Gateway  
* 0009-2: Kong Gateway  

## Decision Outcome  

Chosen option: 0009-2: Kong Gateway, because proporciona flexibilidad, una integración robusta con Kubernetes y es compatible con AKS sin quedar atado al ecosistema de Amazon.  

### Consequences  

* Good, because Kong Gateway es altamente compatible con AKS y ofrece herramientas específicas para microservicios basados en Kubernetes.  
* Good, because ofrece flexibilidad en la integración con otros entornos, manteniendo la independencia del proveedor.  
* Good, because soporta autenticación, autorización y enrutamiento dinámico avanzado.  
* Bad, because su configuración inicial puede ser más compleja que la de AWS API Gateway.  

### Confirmation  

Aunque AWS API Gateway ofrece beneficios como integración directa con servicios de Amazon, el uso de AKS como plataforma base favorece una solución más flexible como Kong Gateway, ya que este está optimizado para arquitecturas híbridas y Kubernetes nativo, además de ser compatible con entornos multiplataforma.  

## Pros and Cons of the Options  

### 0009-1: AWS API Gateway  

AWS API Gateway es una solución nativa del ecosistema de Amazon para gestionar solicitudes API.  

* Good, because es fácil de implementar dentro del ecosistema AWS.  
* Good, because ofrece funcionalidades avanzadas como gestión de tráfico y monitoreo.  
* Neutral, because requiere integrarse con AKS a través de configuraciones adicionales.  
* Bad, because vincula fuertemente la arquitectura al ecosistema Amazon, lo cual limita la flexibilidad.  

### 0009-2: Kong Gateway  

Kong Gateway es un gateway API basado en código abierto, diseñado para integrarse con Kubernetes y entornos híbridos.  

* Good, because está optimizado para arquitecturas Kubernetes, como AKS.  
* Good, because ofrece soporte multiplataforma y no vincula el sistema a un único proveedor.  
* Good, because incluye herramientas avanzadas de autenticación, autorización y gestión de tráfico.  
* Bad, because la configuración inicial puede requerir mayor esfuerzo y experiencia técnica.  
