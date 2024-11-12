---
status: "proposed"
date: 2024-11-12
decision-makers: Adrián Muñoz y Delia Martínez
consulted: ASC
informed: ASJ y ASC
---

# Tres intentos para realizar pedidos

## Context and Problem Statement

Para realizar un pedido, el cliente tendrá como máximo tres intentos para la finalización de este. 

## Decision Drivers

- RF-3.2: Tres intentos para realizar un pedido.

## Considered Options

- 0008-1: **Error Handling and Retries Pattern** para la gestión de pedidos.
- 0008-2: **Retry Mechanism at Client-Side** usando JavaScript y mecanismos de caché.
- 0008-3: **Queue-Based Retry System** para procesar pedidos a través de una cola con reintentos a intervalos fijos.

## Decision Outcome

Chosen option: **Error Handling and Retries Pattern** para la gestión de pedidos.

## Pros and Cons of the Options

## Retry Mechanism at Client-Side
- Good, because reduce de latencia y sobrecarga al gestionar los reintentos directamente en el cliente, mejorando el rendimiento general en algunas situaciones.
- Bad, because aumenta la complejidad en el lado del cliente, presenta posibles riesgos de seguridad y podría ser más difícil de mantener y controlar en comparación con una solución centralizada en el servidor.

## Queue-Based Retry System
- Good, because mejora la tolerancia a fallos y la gestión de errores, desacoplando la lógica de reintentos del proceso principal, lo que puede reducir la latencia y la sobrecarga en el sistema.
- Bad, because la implementación de un sistema basado en colas puede introducir complejidad adicional en la arquitectura y posibles problemas de rendimiento si no se dimensiona correctamente, además de añadir latencia debido al procesamiento en cola.