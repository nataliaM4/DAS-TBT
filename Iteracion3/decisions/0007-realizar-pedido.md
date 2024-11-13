---
status: "proposed"
date: 2024-11-12
decision-makers: Adrián Muñoz y Delia Martínez
consulted: ASC
informed: ASJ y ASC
---

# Realizar un pedido

## Context and Problem Statement

La aplicación debe permitir al cliente realizar un pedido de los productos de la empresa. Cuando un pedido se realice correctamente, el sistema de pedidos procesa el pedido, lo autoriza y lo acepta.

## Decision Drivers

* RF-3.1: Realizar pedido

## Considered Options

* 0007-1: Domain-Driven Design para el sistema de gestión de pedidos.
* 0007-2: Event Sourcing para un sistema más flexible y escalable.

## Decision Outcome

Chosen option: 0007-1: Domain-Driven Design para el sistema de gestión de pedidos.

## Pros and Cons of the Options

### Event Sourcing

* Good, because: Proporciona una forma flexible y escalable de manejar el estado del sistema, permitiendo un seguimiento completo de los eventos y facilitando la evolución del sistema.
* Bad, because: Impone cambios significativos en la arquitectura actual, lo que podría incrementar la complejidad y los costos de implementación y mantenimiento.
