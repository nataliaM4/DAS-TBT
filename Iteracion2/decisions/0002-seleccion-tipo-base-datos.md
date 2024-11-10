---
status: "accepted"
date: 2024-11-06
decision-makers: Adrián Muñoz y Delia Martínez
consulted: ASC
informed: ASJ y ASC
---

# Seleccion de tipo de Base de Datos

## Context and Problem Statement

El sistema necesita almacenar datos de clientes y pedidos en dos bases de datos distintas. La decisión es sobre si utilizar una base de datos SQL o NoSQL para ambos tipos de datos.

## Decision Drivers

* RF-2.1: La aplicación debe permitir acceder a los clientes a sus datos personales.
* RF-2.2: La aplicación debe permitir acceder a la información sobre los pedidos y sobre los clientes de la empresa.

## Considered Options

* 0002-1: Uso de base de datos SQL para datos estructurados.
* 0002-2: Uso de base de datos NoSQL para datos no estructurados.
* 0002-3: Uso de una base de datos híbrida (SQL para clientes y NoSQL para pedidos).

## Decision Outcome

Chosen option: Uso de base de datos SQL para datos estructurados, porque es la opción que mejor satisface los requisitos de consistencia, integridad de los datos y capacidad de manejar relaciones complejas entre los datos de clientes y pedidos.

### Consequences

* Good, because mejora la consistencia de los datos al aprovechar las relaciones entre tablas en una base de datos SQL.
* Good, because simplifica la gestión de la infraestructura al utilizar una sola tecnología para todos los datos estructurados.
* Bad, because puede no ser tan flexible para manejar grandes volúmenes de datos no estructurados o semi-estructurados.

## Pros and Cons of the Options

### Uso de Base de Datos SQL para Datos Estructurados

Este enfoque utiliza las capacidades de bases de datos SQL para gestionar datos que tienen una estructura clara, como los datos de clientes y pedidos.

* Good, because asegura la integridad referencial y facilita la gestión de relaciones entre tablas.
* Good, because las bases de datos SQL son bien conocidas, ampliamente soportadas y fáciles de administrar.
* Bad, because las bases de datos SQL pueden volverse más lentas al manejar grandes volúmenes de datos no estructurados.

### Uso de Base de Datos NoSQL para Datos No Estructurados

Este enfoque utiliza bases de datos NoSQL para manejar datos no estructurados, como registros de actividad o datos de clientes sin una estructura fija.

* Good, because las bases de datos NoSQL pueden manejar grandes volúmenes de datos de manera eficiente y escalar horizontalmente.
* Bad, because no son tan adecuadas para gestionar relaciones complejas entre datos estructurados, como los datos de clientes y pedidos.
* Bad, because puede ser más difícil garantizar la consistencia de los datos debido a la naturaleza eventual de la consistencia en muchas bases de datos NoSQL.
