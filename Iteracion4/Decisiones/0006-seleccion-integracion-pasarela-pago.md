---
status: "accepted "
date: 2024-11-20
decision-makers: Adrián Muñoz y Delia Martínez
consulted: ASC
informed: ASJ y ASC
---

# Selección de Patrón de Integración de Pasarela de Pago

Esta decisión reemplaza a la "0006-Seleccion-integracion-pasarela-pago". 

## Context and Problem Statement

La aplicación debe poder redirigirnos a la pasarela de pago STRIPE para realizar un pago.

## Decision Drivers

* RD-02: Uso de STRIPE 

## Considered Options

* 0006-1: Uso del componente STRIPE para garantizar la seguridad de los pagos.

## Decision Outcome

Chosen option: 0006-1: Uso del componente STRIPE para garantizar la seguridad de los pagos.

## Pros and Cons of the Options

### Pasarela de pago STRIPE

* Good, because posee soporte global, STRIPE está disponible en más de 40 países y permite aceptar pagos en múltiples monedas, lo que lo hace ideal para negocios con clientes internacionales.
* Good, because tiene servicios adicionales, STRIPE ofrece servicios adicionales como STRIPE Atlas para crear empresas globalmente, STRIPE Billing para suscripciones recurrentes, y STRIPE Radar para detectar fraudes, lo que hace que sea una solución completa.
* Good, because facilidad de uso, la interfaz de usuario de STRIPE es intuitiva tanto para comerciantes como para los usuarios que hacen pagos, mejorando la experiencia general del cliente.
* Bad, because tarifas, las tarifas de STRIPE pueden ser más altas en comparación con otras opciones, especialmente para pagos internacionales o pagos con tarjeta de crédito extranjera. Esto puede ser un inconveniente para negocios que tienen márgenes de beneficio bajos.
* Bad, because soporte limitado en algunos países, aunque STRIPE está disponible en muchos países, no está disponible en todos, lo que limita su uso para empresas en ciertas regiones.
* Bad, because tarifas, las tarifas de STRIPE pueden ser más altas en comparación con otras opciones, especialmente para pagos internacionales o pagos con tarjeta de crédito extranjera. Esto puede ser un inconveniente para negocios que tienen márgenes de beneficio bajos.
* Bad, because soporte limitado en algunos países, aunque STRIPE está disponible en muchos países, no está disponible en todos, lo que limita su uso para empresas en ciertas regiones.
