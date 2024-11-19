---
status: "proposed"
date: 2024-11-19
decision-makers: Adrián Muñoz y Delia Martínez
consulted: ASC
informed: ASJ y ASC
---

# Numero de clases para el pago 

## Context and Problem Statement



## Decision Drivers

* RF-06: La aplicación debe poder redirigirnos a la pasarela de pago STRIPE para realizar un pago.
* RD-02: Uso de STRIPE 

## Considered Options

* 0013-1: Crear una clase para el pago. 
* 0013-2: Que el pago se gestione con el pedido.
## Decision Outcome

Chosen option: 0013-1: Crear una clase para el pago.  

## Pros and Cons of the Options

### Crear una clase para el pago 
* Good, because separa las responsabilidades, haciendo el código más modular y fácil de mantener.
* Good, because permite manejar múltiples métodos de pago de manera independiente, facilitando la expansión o modificación de funcionalidades.
* Good, because mejora la reutilización del código al centralizar la lógica relacionada con los pagos en un solo lugar.

* Bad, because añade complejidad inicial al sistema, ya que requiere definir e integrar la clase de pago con las demás funcionalidades.
* Bad, because podría generar duplicación de datos o pasos si el pedido también necesita parte de la lógica del pago para su gestión.


### Pago gestionado junto con el pedido
* Good, because simplifica la arquitectura, ya que el pago está directamente integrado con el flujo del pedido.
* Good, because reduce la cantidad de clases y relaciones en el sistema, facilitando una implementación más rápida.

* Bad, because mezcla responsabilidades, haciendo el código menos modular y más difícil de mantener o escalar.
* Bad, because complica la implementación de múltiples métodos de pago, ya que se mezclaría con la lógica del pedido.
* Bad, because dificulta las pruebas unitarias al no estar las funcionalidades de pago desacopladas del pedido.

