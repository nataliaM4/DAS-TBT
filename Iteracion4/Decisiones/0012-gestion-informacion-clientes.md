---
status: "proposed"
date: 2024-11-19
decision-makers: Adrián Muñoz y Delia Martínez
consulted: ASC
informed: ASJ y ASC
---

# Gestión de Información de los Clientes

## Context and Problem Statement

La aplicación debe proporcionar al cliente estadísticas sobre el número de pedidos que se han realizado, el gasto total de todos los pedidos y la fecha del primer pedido realizado.

## Decision Drivers

* RF-4.2: Proporcionar información de los clientes.

## Considered Options

* 0012-1: Crear una única clase que gestione toda la información estadística del cliente.
* 0012-2: Dividir la funcionalidad en varias clases: una para gestionar pedidos y otra para procesar estadísticas del cliente.

## Decision Outcome

Chosen option: 0012-1: Crear una única clase que gestione toda la información estadística del cliente, porque permite cubrir el requerimiento RF-4.2 de manera eficiente y directa, sin agregar complejidad innecesaria.

## Pros and Cons of the Options

### Crear una única clase para gestionar la información estadística del cliente

* Good, because es simple. Centralizar los datos en una sola clase facilita la implementación inicial y reduce la complejidad del sistema.
* Good, because es eficiente. Todas las estadísticas están disponibles en un solo lugar, lo que minimiza las dependencias entre clases.
* Good, because ofrece claridad. Una única entidad encapsula toda la información relevante para las estadísticas del cliente.
* Bad, because tiene escalabilidad limitada. Si se requiere agregar nuevas estadísticas o funcionalidades avanzadas, podría ser necesario refactorizar la clase.
* Bad, because está acoplada. Combinar la gestión de pedidos con las estadísticas puede dificultar futuras extensiones o modificaciones.

### Dividir la funcionalidad en varias clases

* Good, because mejora la modularidad al asignar responsabilidades específicas a cada clase, facilitando la escalabilidad y el mantenimiento.
* Good, because ofrece mayor flexibilidad para introducir nuevas estadísticas o integrar herramientas externas de análisis.
* Bad, because añade complejidad inicial, con más clases y relaciones entre ellas.
* Bad, because incrementa el tiempo y el esfuerzo de desarrollo, lo cual no es necesario para cubrir el requerimiento actual.
