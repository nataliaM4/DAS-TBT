---
status: "accepted"
date: 2024-11-06
decision-makers: Adrián Muñoz y Delia Martínez
consulted: ASC
informed: ASJ y ASC
---

# Seleccion del tipo de Acceso al Servidor

## Context and Problem Statement

Dado que el sistema propuesto se encuentra en una arquitectura cliente-servidor con microservicios, se necesita definir el tipo de API que se utilizará para la comunicación entre los clientes (PC y móvil) y los servicios backend, que acceden a datos personales y empresariales (clientes, pedidos, etc.).

## Decision Drivers

* RF-2.1: La aplicación debe permitir acceder a los clientes a sus datos personales.
* RF-2.2: La aplicación debe permitir acceder a la información sobre los pedidos y sobre los clientes de la empresa.

## Considered Options

* 0001-1: API Gateway Centralizado
* 0001-2: API Gateway Distribuido

## Decision Outcome

Chosen option: API Gateway Centralizado, porque es la que ofrece la mejor combinación de simplicidad de implementación, control centralizado sobre la seguridad y facilidad para gestionar el tráfico entre los servicios.

### Consequences

* Good, because proporciona un punto de entrada centralizado, lo que simplifica la gestión de la seguridad, el monitoreo y la configuración del tráfico de las solicitudes.
* Good, because permite escalar más fácilmente al concentrar el tráfico a través de un único Gateway, lo que facilita el control y optimización de las operaciones.
* Bad, because puede convertirse en un cuello de botella en caso de un aumento significativo en el tráfico, lo que podría afectar la disponibilidad y el rendimiento si no se dimensiona adecuadamente.
* Bad, because la gestión del punto de entrada único requiere un monitoreo constante y una capacidad de respuesta rápida ante fallos, lo que aumenta la complejidad operativa.

## Pros and Cons of the Options

### API Gateway Centralizado

Un único punto de entrada para gestionar todas las solicitudes de los clientes hacia los microservicios, simplificando la arquitectura y el control de seguridad.

* Good, because simplifica la gestión del tráfico, ya que todo pasa por un único punto de entrada, lo que facilita el control centralizado.
* Good, because mejora la seguridad, permitiendo implementar medidas de autenticación, autorización y cifrado de manera uniforme.
* Bad, because puede convertirse en un cuello de botella si el volumen de solicitudes aumenta significativamente, lo que podría afectar la escalabilidad.
* Bad, because si el Gateway falla, toda la comunicación con los microservicios puede verse afectada, lo que requiere una alta disponibilidad y monitoreo constante.

### API Gateway Distribuido

Varios puntos de entrada, cada uno gestionando parte del tráfico, lo que permite distribuir las cargas de trabajo y aumentar la resiliencia.

* Good, because distribuye la carga de trabajo entre varios Gateways, reduciendo el riesgo de un cuello de botella.
* Good, because mejora la resiliencia, ya que si un Gateway falla, los demás pueden seguir funcionando sin interrupciones en el servicio.
* Bad, because aumenta la complejidad operativa y puede generar costos adicionales al tener que implementar y mantener varios Gateways.
* Bad, because la seguridad puede ser más difícil de gestionar, ya que cada Gateway podría tener su propia configuración de autenticación y autorización, lo que aumenta el riesgo de inconsistencias.

