---
status: "aceptada"
date: 2024-11-06
decision-makers: Adrián Muñoz y Delia Martínez
consulted: ASC
informed: ASJ y ASC
---

# Selección de Estilo de Arquitectura para Migración a Microservicios

## Context and Problem Statement

Se necesita establecer un estilo arquitectónico para el sistema de la compañía de productos alimenticios. Dado que se quiere transformar la arquitectura monolítica de la compañía en una basada en microservicios, el objetivo de esta decisión es seleccionar el modelo arquitectónico adecuado que permita un sistema modular y escalable.

## Decision Drivers

* RF-01: Necesidad de cambiar a una arquitectura que soporte microservicios, lo cual facilitará el mantenimiento y la escalabilidad.

## Considered Options

* 0000-1-Arquitectura-Orientada-a-Servicios
* 0000-2-Arquitectura-Cliente-Servidor

## Decision Outcome

Opción elegida: 0000-2-Arquitectura-Cliente-Servidor, porque esta opción permite una implementación sencilla y estructurada, centralizando la lógica de negocio en el servidor y facilitando la comunicación entre cliente y servidor. Esto proporciona un control unificado de la lógica de negocio y una menor complejidad inicial en la transición hacia microservicios.

### Positive Consequences

* Simplifica la comunicación interna al mantener una estructura centralizada de gestión de datos y lógica de negocio.
* La latencia en la comunicación puede reducirse al tener menos componentes intermedios en la arquitectura.

## Pros and Cons of the Options

### 0000-1-Arquitectura-Orientada-a-Sercicios

La arquitectura SOA (Orientada a Servicios) permite una estructura modular en la cual cada microservicio opera de forma independiente y se conecta a través de un componente Gateway que centraliza la autenticación y enrutamiento de solicitudes. Cada microservicio abarca un módulo específico, como clientes, pedidos, rutas y pagos, y cada módulo se comunica mediante protocolos estándar como HTTP/REST.

* Buena, porque facilita la migración a microservicios sin interrumpir los servicios actuales, además de permitir escalabilidad horizontal de módulos críticos.
* Buena, porque reduce el acoplamiento entre módulos y permite mejorar la seguridad en el acceso a cada componente.
* Mala, porque depende de una mayor cantidad de servicios individuales, lo cual requiere una gestión detallada y monitoreo de cada uno de ellos.

### 0000-2-Arquitectura-Cliente-Servidor

Esta opción aplica una estructura de cliente-servidor en la que el servidor centraliza la lógica de negocio y el acceso a la base de datos. Se utilizan dos capas principales: una capa de cliente que envía las solicitudes y una capa de servidor que gestiona la lógica de negocio y datos.

* Buena, porque simplifica la comunicación interna y es fácil de implementar sin una gran cantidad de componentes adicionales.
* Buena, porque reduce la latencia de comunicación al tener una arquitectura unificada y centralizada.
* Mala, porque limita la flexibilidad de la arquitectura, lo que dificultaría el escalado independiente de cada módulo y podría hacer el sistema menos resiliente frente a fallos en el servidor.
