---
status: {accepted}
date: {2024-11-14}
decision-makers: {Iván Gutiérrez González, Arturo Enrique Gutiérrez Mirandona}
consulted: {Elinee Nathalie Freites Muñoz, Jorge Cimadevilla Aniz}
informed: {Víctor Bartolomé Letosa, Alejandro Valor González}
---

# Ejecución de microservicios

## Context and Problem Statement

El problema se describe como la necesidad de ejecutar todos los microservicios utilizados por el sistema de manera individual y monitorizada.

## Decision Drivers

* RF-8: Ejecución de microservicios.

## Considered Options

* 0009-1-Azure Kubernetes Services
* 0009-2-Red Hat OpenShift

## Decision Outcome

Chosen option: 0009-1-Azure Kubernetes Services, because Posee un factor de seguridad y costes reducidos mayor a las demás opciones.

### Consequences

* Good, because Optimiza costes ahorrando recursos inactivos.
* Good, because Provee un acceso seguro.
* Bad, because Implica una curva de aprendizaje inicial.

### Confirmation

Aunque hay muchos tipos de plataformas para el despliegue de microservicios diferenciándose sobre todo en qué tipo de entornos trabaja (Amazon, Google, Microsoft, etc.), dado que no se nos implica un entorno en concreto lo más diferenciante sería la seguridad y el bajo coste.

## Pros and Cons of the Options

### 0009-1-Azure Kubernetes Services

Azure Kubernetes Services es una plataforma implementada por Microsoft y gestionada en Azure.

* Good, because Optimiza costes ahorrando recursos inactivos.
* Good, because Provee un acceso seguro.
* Bad, because Implica una curva de aprendizaje inicial.

### 0009-2-Red Hat OpenShift

Red Hat OpenShift es una plataforma de ejecución de microservicios (contenedores) basada en Kubernetes.

* Good, because Permite un despliegue en múltiples entornos como hibrido o en servidores remotos.
* Good, because Permite una mayor flexibilidad y escalabilidad, sobre todo para empresas grandes.
* Neutral, because Provee una acceso seguro pero de menor calidad.
* Bad, because Implica grandes costes en comparación a otras plataformas.
