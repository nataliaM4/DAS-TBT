---
status: "proposed"
date: 2024-11-19
decision-makers: Adrián Muñoz y Delia Martínez
consulted: ASC
informed: ASJ y ASC
---

# Gestión de Información del Pedido

## Context and Problem Statement

La aplicación tiene que poder proporcionar el peso, volumen, remitente y destinatario de los pedidos, así como la situación en tiempo real de los camiones.

## Decision Drivers

* RF-4.1: Proporcionar información del pedido.

## Considered Options

* 0011-1: Crear una única clase que gestione toda la información requerida del pedido.
* 0011-2: Dividir la funcionalidad en varias clases: una para la información del pedido y otra para la ubicación de los camiones.

## Decision Outcome

Chosen option: 0011-1: Crear una única clase que gestione toda la información requerida del pedido, porque es suficiente para cubrir el requerimiento RF-4.1 de forma eficiente, manteniendo un diseño simple y escalable.

## Pros and Cons of the Options

### Clase única para gestionar la información del pedido

* Good, because es simple. Menor número de clases facilita la implementación inicial y el mantenimiento.
* Good, because es eficiente. Centraliza todos los datos del pedido, evitando dependencias innecesarias.
* Good, because es clara. Una sola entidad representa toda la información relevante de un pedido.
* Bad, because tiene escalabilidad limitada. Si se requieren funcionalidades avanzadas (como cálculos complejos o actualizaciones en tiempo real), podría ser necesario refactorizarla.
* Bad, because está acoplada. Combinar datos físicos (peso, volumen) con la ubicación de los camiones podría generar responsabilidades adicionales no deseadas.

### Dividir la funcionalidad en varias clases

* Good, because mejora la modularidad al asignar una responsabilidad específica a cada clase, facilitando la extensión del sistema en el futuro.  
* Good, because ofrece mejor escalabilidad, siendo adaptable a sistemas con mayores requerimientos.  
* Bad, because añade complejidad inicial, con más clases y relaciones entre ellas.  
* Bad, because incrementa el coste y el tiempo de desarrollo, lo cual no es necesario para cubrir los requerimientos actuales.  