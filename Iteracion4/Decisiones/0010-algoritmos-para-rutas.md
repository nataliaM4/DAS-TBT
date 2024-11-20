---
status: "accepted"
date: 2024-11-18
decision-makers: Adrián Muñoz y Delia Martínez
consulted: ASC
informed: ASJ y ASC
---

# Algoritmos de selección de rutas para reparto

## Context and Problem Statement

Se deben utilizar dos algoritmos para optimizar los repartos de los camiones teniendo en cuenta las rutas utilizadas y la demora del camión.

## Decision Drivers

* RF-7.2: Dos algoritmos de selección de rutas. 

## Considered Options

* 0010-1: Patrón Strategy.
* 0010-2: Strategy and Template Method. 
* 0010-3: Strategy and Factory Method. 
## Decision Outcome

Chosen option: 0008-1: Patrón Strategy. 

## Pros and Cons of the Options

### Patrón Strategy
* Good, because tiene flexibilidad y desacoplamiento que permite encapsular cada algoritmo de optimización en su propia clase.
* Good, because proporciona mayor claridad y cohesión a cada algoritmo, lo que mejora la legibilidad y organización.

* Bad, because necesita un cliente persistente, dado que el código debe saber cuándo y cómo cambiar entre estrategias, lo que puede requerir lógica adicional para determinar qué estrategia usar en cada caso.
  
### Strategy and Template Method
* Good, because cuenta con una plantilla general que reduce la magnitud de los cambios necesarios, lo que facilita la información coherente y entendible. Se mantiene la estructura dado que se pueden alterar los datos específicos. 

* Bad, because a medida que el sistema de selección de algoritmos se va expandiendo, el Template Method puede volverse un punto crítico de fragilidad, dificultando su mantenimiento y escalabilidad. 

### Strategy and Factory Method. 
* Good, because el proceso de selección se realiza de forma automática, simplificando la interacción del usuario. 
* Good, because es fácil de cambiar o añadir nuevas estrategias sin impactar en el resto del sistema. 

* Bad, because implementa la lógica para la selección automática lo que hace que incremente la complejidad del problema. 

* Bad, because si la lógica de selección no está bien implementada, la automatización puede generar errores inesperados. 
