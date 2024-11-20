---
status: "accepted"
date: 2024-11-18
decision-makers: Adrián Muñoz y Delia Martínez
consulted: ASC
informed: ASJ y ASC
---

# Desacoplar y gestionar flotas y rutas de los camiones

## Context and Problem Statement

La aplicación nos debe permitir desacoplar y gestionar el reparto de las flotas de transporte a los clientes y las rutas de los camiones.

## Decision Drivers

* RF-7.1: Desacoplar y gestionar el repartos de las flotas y rutas de los camiones. 

## Considered Options

* 0009-1: Dividir en dos clases. 
* 0009-2: Mantener una sola clase. 

## Decision Outcome

Chosen option: 0009-1: Dividir en dos clases.  

## Pros and Cons of the Options

### Dividir en dos clases 
* Good, because al estar divididas es más sencillo realizar un seguimiento de la actividad de cada clase. 
* Good, because el sistema se puede volver más simple que si estuvieran las clases juntas. 

* Bad, because puede provocar que el servidor tenga una mayor carga además de que sea más complejo el diseño del sistema. 

### Mantener una sola clase
* Bad, because que haya tanto trabajo concentrado en un único punto hace que se convierta en un punto vulnerable ante fallos del sistema. 
