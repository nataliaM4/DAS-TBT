---
status: "proposed"
date: 2024-11-07
decision-makers: Adrián Muñoz y Delia Martínez
consulted: ASC
informed: ASJ y ASC
---

# Validación de Pedidos basada en Arquitectura Cliente-Servidor

## Context and Problem Statement

La arquitectura monolítica existente está siendo reemplazada por una arquitectura cliente-servidor para mejorar la flexibilidad y escalabilidad del sistema. El servidor centralizará la lógica de negocio, gestionando el proceso de validación de pedidos. La aplicación debe validar los pedidos correctamente y cumplir con las políticas de negocio de la empresa. Se aplicarán los patrones de Validación basada en Domain-Driven Design (DDD) y Command Query Responsibility Segregation (CQRS) para garantizar un proceso de validación escalable y coherente.



## Decision Drivers


* **RF-3**: La aplicación debe proporcionar una manera de gestionar todas las peticiones de los pedidos de clientes.
* **RF-3.1**: La aplicación debe permitir al cliente realizar un pedido de los productos a la empresa. Cuando un pedido se realice correctamente el sistema de pedidos preprocesa el pedido, lo autoriza y lo acepta.


## Considered Options

* 0004-1: **Event Sourcing**: Un enfoque alternativo al CQRS podría ser Event Sourcing, que almacenaría el historial de todos los cambios en el proceso de validación de pedidos. Sin embargo, este enfoque podría agregar complejidad y sobrecarga al sistema.
* 0004-2: **API Gateway**: Otro enfoque alternativo podría ser el uso de un API Gateway para manejar las solicitudes entrantes y enrutar las peticiones al servidor de validación. Sin embargo, este enfoque podría introducir latencia adicional y complejidad al sistema.



## Decision Outcome

Se ha decidido aplicar el **Patrón de Validación basada en Domain-Driven Design (DDD) y Command Query Responsibility Segregation (CQRS)** para la validación de pedidos. A pesar de que **CQRS** puede introducir una sobrecarga de rendimiento, se considera adecuado para optimizar las operaciones de lectura y escritura relacionadas con la validación, desacoplando el proceso de validación de la lógica de negocio y proporcionando una solución escalable.

* **Good**, porque mejora la escalabilidad al permitir manejar pedidos concurrentes de manera eficiente.
* **Good**, porque permite optimizar las operaciones de lectura y escritura, mejorando el rendimiento general del proceso de validación.
* **Bad**, because el patrón CQRS podría agregar complejidad al sistema y afectar el rendimiento en entornos con altos volúmenes de pedidos.


## Pros and Cons of the Options

### **Event Sourcing**

* **Good**, because el Event Sourcing almacena el historial de los cambios en el proceso de validación de pedidos, lo que podría mejorar el rastreo de los cambios y la capacidad de revertirlos.
* **Bad**, because implementar Event Sourcing agregaría complejidad adicional al sistema y requeriría una mayor cantidad de recursos para gestionar el almacenamiento y la recuperación de eventos.

### **Uso de un API Gateway**

* **Good**, because un API Gateway podría proporcionar una interfaz centralizada para gestionar las solicitudes de validación de pedidos y mejorar la eficiencia en la gestión de los datos entre el cliente y el servidor.
* **Bad**, because el uso de un API Gateway podría introducir latencia adicional y un punto único de falla, lo que podría afectar el rendimiento del sistema y su disponibilidad.
