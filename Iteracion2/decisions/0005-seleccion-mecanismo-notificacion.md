---
status: "rejected "
date: 2024-11-07
decision-makers: Adrián Muñoz y Delia Martínez
consulted: ASC
informed: ASJ y ASC
---

# Selección de Mecanismo de Notificación en Tiempo Real para el Sistema de Gestión de Pedidos

## Context and Problem Statement

El sistema de gestión de pedidos existente requiere un mecanismo de notificación en tiempo real para informar a los gestores de rutas sobre incidencias que ocurren durante el proceso de gestión de pedidos. Esta decisión responde a la necesidad de un mecanismo de notificación seguro, confiable y escalable que pueda manejar patrones de tráfico cambiantes.

## Decision Drivers

* RF-5: Mostrar incidencias que ocurran durante el pedido.
* RF-5.1: Permitir a los clientes reportar incidencias.
* RF-5.2: Permitir gestionar las incidencias en el pedido.

## Considered Options

* Uso del patrón de Cola de Mensajes (Message Queue Pattern).
* Uso de protocolo HTTP/REST.
* Uso de protocolo MQTT.
* Uso de WebSockets.

## Decision Outcome

Chosen option: Patrón de Cola de Mensajes, porque proporciona una solución flexible y escalable para la notificación en tiempo real, permitiendo manejar patrones de tráfico cambiantes de manera eficiente.


* Good, because proporciona una solución escalable y flexible para el mecanismo de notificación.
* Bad, because puede introducir latencia adicional, lo que podría impactar el rendimiento general del sistema.
* Good, because permite notificaciones en tiempo real a los gestores de rutas.

## Pros and Cons of the Options

### Patrón de Cola de Mensajes

* Good, because es flexible y escalable, permitiendo manejar variaciones en el tráfico.
* Good, because permite notificaciones en tiempo real a los gestores de rutas.
* Bad, because podría introducir latencia adicional, lo que afectaría al rendimiento general del sistema.

### Protocolo HTTP/REST

* Good, because es un estándar ampliamente utilizado y fácil de implementar.
* Bad, because puede introducir latencia adicional y afectar el rendimiento general del sistema.

### Protocolo MQTT

* Good, because es eficiente y escalable.
* Bad, because puede requerir infraestructura adicional y recursos.

### WebSockets

* Good, because permite comunicación en tiempo real.
* Bad, because puede requerir infraestructura adicional y recursos.
