---
parent: Decisions
nav_order: 100
title: 0002-Patrón de Segregación de Datos
status: Proposed
date: 2024-10-29
decision-makers: ["Arquitecto Senior", "Líder de Ingeniería de Software", "Gerente de Proyecto"]
consulted: ["Administrador de Bases de Datos", "Experto en Seguridad"]
informed: ["Equipo de Desarrollo", "Propietario del Producto"]
---

# Patrón de Segregación de Datos para Información de Clientes y Pedidos

## Contexto y Declaración del Problema

La empresa necesita migrar su arquitectura de un sistema monolítico a una arquitectura basada en microservicios. La aplicación debe permitir almacenar los datos de clientes y pedidos en bases de datos separadas para garantizar una gestión independiente de cada tipo de información, mejorar la escalabilidad y cumplir con los estándares de seguridad y protección de datos.

## Impulsores de la Decisión

* **Requisito Funcional 01**: La información de clientes y pedidos debe almacenarse en bases de datos independientes.
* **Requisito Funcional 02**: Se debe garantizar la gestión independiente de cada tipo de información.
* **Requisito de Seguridad**: La solución debe mejorar la seguridad de los datos y reducir el riesgo de fugas de información.
* **Requisito de Escalabilidad**: La arquitectura debe facilitar la escalabilidad del sistema, permitiendo un mejor manejo del rendimiento y capacidad.

## Opciones Consideradas

* **0002-1: Patrón de Segregación de Datos**: Bases de datos separadas para clientes y pedidos.
* **0002-2: Base de Datos Única con Tablas Separadas**: Una sola base de datos con tablas separadas para clientes y pedidos.
* **0002-3: Almacén de Datos para Información Histórica**: Uso de un almacén de datos para el almacenamiento histórico, reduciendo la necesidad de bases de datos separadas.

## Resultado de la Decisión

Opción seleccionada: **0002-1: Patrón de Segregación de Datos**, porque cumple con el requisito de almacenar los datos de clientes y pedidos en bases de datos separadas, permitiendo una gestión independiente de cada tipo de información, mejorando la seguridad de los datos y facilitando el cumplimiento de regulaciones de protección de datos.

### Consecuencias

* **Positivas**: Mejora la seguridad de los datos y reduce el riesgo de brechas de seguridad.
* **Positivas**: Facilita el cumplimiento de los estándares de protección de datos.
* **Positivas**: Permite la escalabilidad y mejora el rendimiento al gestionar cada servicio de datos de forma independiente.
* **Negativas**: Aumenta la complejidad de la arquitectura del sistema y requiere recursos adicionales para la gestión y mantenimiento.
* **Negativas**: Puede generar costos adicionales, incluyendo infraestructura, software y personal.
* **Negativas**: Requiere una estrategia de sincronización de datos entre ambas bases de datos.

## Confirmación

La conformidad con esta decisión se confirmará mediante revisiones de diseño y código, así como auditorías de bases de datos para asegurar que los datos de clientes y pedidos se gestionen de forma independiente y que se implementen controles de acceso específicos para cada base de datos.

## Pros y Contras de las Opc

**0002-1: Data Segregation Pattern**
* Pros:
Mejora la seguridad de los datos y reduce el riesgo de brechas de seguridad.
Facilita el cumplimiento de estándares de protección de datos.
Permite la escalabilidad y mejora el rendimiento al gestionar cada servicio de datos de forma específica.

* Cons:
Incrementa la complejidad de la arquitectura del sistema y requiere recursos adicionales para la gestión y mantenimiento.
Puede generar costos adicionales, incluyendo infraestructura, software y personal.
Necesita una estrategia de sincronización de datos entre ambas bases de datos.


**0002-2: Single Database with Separate Tables**
* Pros:
Menor complejidad y costos de infraestructura en comparación con bases de datos separadas.
Simplifica la gestión y el mantenimiento de una sola base de datos.

* Cons:
Menor seguridad en el manejo de datos sensibles de clientes y pedidos en una misma base de datos.
Dificultad para escalar cada tipo de información de forma independiente.
Complica el cumplimiento de estándares de protección de datos.


**0002-3: Data Warehouse for Historical Data**
* Pros:
Facilita el análisis de datos históricos sin necesidad de bases de datos separadas.
Mejora el rendimiento de las consultas al reducir la carga en la base de datos de producción.

* Cons:
No cumple con el requisito de almacenar datos de clientes y pedidos en bases de datos independientes en el sistema en tiempo real.
Incrementa la complejidad de la arquitectura al añadir un componente de almacén de datos.
No aporta una mejora de seguridad para los datos en tiempo real.
