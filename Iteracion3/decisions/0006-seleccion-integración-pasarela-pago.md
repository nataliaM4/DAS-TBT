---
status: "propsed "
date: 2024-11-11
decision-makers: Adrián Muñoz y Delia Martínez
consulted: ASC
informed: ASJ y ASC
---

# Selección de Patrón de Integración de Pasarela de Pago

## Context and Problem Statement

La empresa planea migrar su arquitectura monolítica a microservicios para mejorar la flexibilidad y escalabilidad. El sistema actual usa dos bases de datos SQL para gestionar datos de clientes y pedidos. Se busca integrar la pasarela de pago Stripe de forma flexible y segura, soportando múltiples métodos de pago y garantizando un flujo de pago seguro, con la posibilidad de cambiar a otras pasarelas de pago si es necesario.

## Decision Drivers

* RF-6: La aplicación debe poder redirigirnos a la pasarela de pago STRIPE para realizar un pago

## Considered Options

* 0006-1: Patrón de Integración Stripe SDK: Usar el SDK de Stripe para integrar la pasarela de pago.
* 0006-2: Integración Personalizada: Desarrollar una solución de integración personalizada.
* 0006-3: Patrón de Integración de Pasarela de Pago: Utilizar un patrón más general que permita la integración con Stripe y otras pasarelas de pago.

## Decision Outcome

Chosen option: Patrón de Integración Stripe SDK, porque facilita la integración con Stripe de manera rápida y eficiente, asegurando un flujo de pago seguro. Aunque el Patrón de Integración de Pasarela de Pago también es adecuado, la opción de usar el SDK de Stripe es la más específica y directa para la integración con Stripe.


* Good, because facilita la integración con Stripe de manera rápida y eficiente.
* Good, because asegura un flujo de pago seguro y permite manejar múltiples métodos de pago.
* Bad, because no es tan flexible como el Patrón de Integración de Pasarela de Pago si se desea cambiar a otra pasarela de pago.
* Bad, because puede no ser tan adecuado si se requieren características específicas de otras pasarelas de pago.

## Pros and Cons of the Options

### Patrón de Integración Stripe SDK

* Good, because facilita la integración con Stripe de manera rápida y eficiente.
* Bad, because no es tan flexible como el Patrón de Integración de Pasarela de Pago si se desea cambiar a otra pasarela de pago.

### Integración Personalizada

* Good, because proporciona total flexibilidad en la integración.
* Bad, because es costoso y consume mucho tiempo de desarrollo.

### Patrón de Integración de Pasarela de Pago

* Good, because permite integrar otras pasarelas de pago sin cambios significativos en la infraestructura.
* Good, because mejora la escalabilidad y flexibilidad del sistema.
* Bad, because puede introducir una complejidad adicional al ser más general.