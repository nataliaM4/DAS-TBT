# Selección-Estilo-Arquitectura

* Status: accepted
* Deciders: Adrián Muñoz y Delia Martínez
* Date: 2024-10-31


## Context and Problem Statement

Se necesita establecer un estilo arquitectónico para el sistema de la compañía de productos alimenticios. Dado que se quiere transformar la arquitectura monolítica de la compañía en una basada en microservicios, el objetivo de esta decisión es seleccionar el modelo arquitectónico adecuado que permita un sistema modular y escalable.

## Decision Drivers

* Necesidad de cambiar a una arquitectura que soporte microservicios, lo cual facilitará el mantenimiento y la escalabilidad.
* Requerimiento de una capa de acceso a datos que centralice y gestione la información de los clientes, pedidos, y demás datos empresariales.
* Necesidad de contar con una capa de lógica de negocio que permita la integración eficiente de los diferentes módulos críticos, semi críticos, y no críticos de la empresa.

## Considered Options

* 0001-1-Arquitectura-Oriented-Services
* 0001-2-Arquitectura-Cliente-Servidor

## Decision Outcome

Chosen option: "0001-1-Arquitectura-Oriented-Services", porque esta opción ofrece la mayor flexibilidad para integrar los microservicios de manera autónoma y gestionar la carga de trabajo distribuida, mientras que facilita la comunicación entre módulos críticos de manera segura y escalable.

### Positive Consequences

* Cada servicio puede ser gestionado, actualizado o escalado de manera independiente, lo que permite un sistema más resiliente.
* Los errores en un módulo no afectan directamente el funcionamiento de otros servicios.

## Pros and Cons of the Options

### 0001-1-Arquitectura-Oriented-Services

La arquitectura SOA (Orientada a Servicios) permite una estructura modular en la cual cada microservicio opera de forma independiente y se conecta a través de un componente Gateway que centraliza la autenticación y enrutamiento de solicitudes. Cada microservicio abarca un módulo específico, como clientes, pedidos, rutas y pagos, y cada módulo se comunica mediante protocolos estándar como HTTP/REST.

* Good, because facilita la migración a microservicios sin interrumpir los servicios actuales, además de permitir escalabilidad horizontal de módulos críticos.
* Good, because reduce el acoplamiento entre módulos y permite mejorar la seguridad en el acceso a cada componente.
* Bad, because depende de una mayor cantidad de servicios individuales, lo cual requiere una gestión detallada y monitoreo de cada uno de ellos.

### 0001-2-Arquitectura-Cliente-Servidor

Esta opción aplica una estructura de cliente-servidor en la que el servidor centraliza la lógica de negocio y el acceso a la base de datos. Se utilizan dos capas principales: una capa de cliente que envía las solicitudes y una capa de servidor que gestiona la lógica de negocio y datos.

* Good, because simplifica la comunicación interna y es fácil de implementar sin una gran cantidad de componentes adicionales.
* Good, because reduce la latencia de comunicación al tener una arquitectura unificada y centralizada.
* Bad, because limita la flexibilidad de la arquitectura, lo que dificultaría el escalado independiente de cada módulo y podría hacer el sistema menos resiliente frente a fallos en el servidor.
