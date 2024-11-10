---
status: "accepted"
date: 2024-11-07
decision-makers: Adrián Muñoz y Delia Martínez
consulted: ASC
informed: ASJ y ASC
---

# Selección de patrón de comunicación de incidencias en los pedidos

## Context and Problem Statement

El sistema debe adaptarse en tiempo real a las distintas situaciones que ocurren basándose en la información sobre las incidencias. ¿Qué tipo de información debería proporcionarse al sistema y cómo debería gestionarse internamente?

## Decision Drivers

* RF-5: Mostrar incidencias que ocurran durante el pedido.
* RF-5.1: Permitir a los clientes reportar incidencias.
* RF-5.2: Permitir gestionar las incidencias en el pedido.

## Considered Options

* 0003-1: Comunicación inmediata de incidencia a clase GestorPedidos mediante el patrón Mediator existente.
* 0003-2: Comunicación inmediata de incidencia a clase GestorPedidos haciendo uso del patrón Mediator existente y la incorporación de un patrón Observer.
* 0003-3: Comunicación periódica de incidencias a GestorPedidos, mediante el agrupamiento y envío de incidencias en un tiempo fijo determinado usando un patrón Composite.

## Decision Outcome

Chosen option: Comunicación inmediata de incidencia a clase GestorPedidos mediante el patrón Mediator existente.


* Good, because hay menor complejidad de acceso y almacenamiento de los datos.
* Good, because se obtiene información de forma inmediata.
* Bad, because existe pérdida de la posibilidad de atención preferente de incidencias prioritarias.

## Pros and Cons of the Options

### Comunicación inmediata de incidencia a clase GestorPedidos mediante el patrón Mediator existente

El patrón Mediator ya presente en la arquitectura comunicará a la clase GestorPedidos la incidencia recibida en el momento en el que se envíe, y haciendo uso de sus métodos internos GestorPedidos tratará la incidencia individualmente dependiendo de su tipo (camión averiado, pedido no realizado o retraso del camión).

* Good, because no es necesario añadir elementos software adicionales.
* Good, because se recibe la información de forma inmediata.
* Bad, because aumenta la complejidad de la clase receptora.

### Comunicación inmediata de incidencia a clase GestorPedidos haciendo uso del patrón Mediator existente y la incorporación de un patrón Observer.

El patrón Observer notificará a GestorPedidos de forma inmediata cuando se produzca una incidencia. GestorPedidos por su parte, haciendo uso de su patrón Mediator, comunicará la información necesaria (principalmente tipo, descripción, prioridad, fecha de generación, estado y comunicador) a las clases que la soliciten.

* Good, because se reutilizan elementos software ya presentes en la arquitectura.
* Good, because se recibe la información de forma inmediata.
* Bad, because posible saturación del sistema como consecuencia de notificaciones continuadas.

### Comunicación periódica de incidencias a GestorPedidos, mediante el agrupamiento y envío de incidencias en un tiempo fijo determinado usando un patrón Composite.

En cuanto se genere una incidencia, el patrón Composite la clasificará en función de uno o varios criterios (el más importante la prioridad que presente) y la añadirá a su estructura interna en forma de árbol. Transcurrido un tiempo determinado y modificable se enviará esta estructura, junto a los elementos necesarios para el acceso y consulta a cada elemento del árbol, a GestorPedidos, que será capaz de tratar las incidencias ordenadamente siguiendo el criterio seleccionado.

* Good, because se tratan las incidencias en orden de relevancia.
* Good, because almacenamiento y recopilación de datos de incidencias más preciso y eficaz.
* Bad, because transferencia de información más costosa por la inclusión de métodos para el acceso a la información.
* Bad, because almacenamiento más lento y costoso debido a la clasificación de incidencias.
