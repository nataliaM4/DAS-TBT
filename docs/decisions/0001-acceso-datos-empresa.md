# Acceso datos empresa

* Status: proposed
* Date: 2024-10-30

## Context and Problem Statement

La empresa necesita migrar su arquitectura de un sistema monolítico a una arquitectura de microservicios. La aplicación debe permitir almacenar los datos de clientes y pedidos en bases de datos separadas para garantizar una gestión independiente de cada tipo de información, mejorar la escalabilidad y cumplir con los estándares de seguridad y protección de datos.

## Decision Drivers

* Requisito Funcional 01: La información de los clientes y de los pedidos debe almacenarse en bases de datos independientes.
* Requisito Funcional 02: Se debe garantizar la gestión independiente de cada tipo de información.

## Considered Options

* 0001-1: Data Segregation Pattern (Patrón de segregación de datos con bases de datos separadas para clientes y pedidos)
* 0001-2: Single Database with Separate Tables (Una sola base de datos con tablas separadas para clientes y pedidos)
* 0001-3: Data Warehouse for Historical Data (Uso de un almacén de datos para almacenamiento histórico y reducción de necesidad de bases de datos separadas)

## Decision Outcome

Chosen option: "0001-1: Data Segregation Pattern", because Esta decisión cumple con el requisito de almacenar los datos de clientes y pedidos en bases de datos separadas, permitiendo una gestión independiente de cada tipo de información, mejorando la seguridad de los datos y facilitando el cumplimiento de regulaciones de protección de datos.

### Positive Consequences

* Mejora la seguridad de los datos y reduce el riesgo de brechas de seguridad.
* Facilita el cumplimiento de estándares de protección de datos.
* Permite la escalabilidad y mejora el rendimiento al gestionar cada servicio de datos de forma específica.

### Negative Consequences

* Incrementa la complejidad de la arquitectura del sistema y requiere recursos adicionales para la gestión y mantenimiento.
* Puede generar costos adicionales, incluyendo infraestructura, software y personal.
* Necesita una estrategia de sincronización de datos entre ambas bases de datos.
