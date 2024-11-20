---  
status: "accepted"  
date: 2024-11-19  
decision-makers: Adrián Muñoz y Delia Martínez  
consulted: ASC  
informed: ASJ y ASC  
---  

# Estadísticas de Pedidos y Clientes  

## Context and Problem Statement  

La aplicación debe proporcionar estadísticas centralizadas sobre los pedidos (peso promedio, volumen promedio, cantidad de pedidos enviados por remitente y destinos frecuentes) y sobre los clientes (número de pedidos realizados, gasto total acumulado, y fecha del primer pedido realizado).  

## Decision Drivers  

* RF-4.1: Proporcionar estadísticas del pedido.  
* RF-4.2: Proporcionar estadísticas de los clientes.  

## Considered Options  

* 0011-1: Crear una única clase que gestione todas las estadísticas requeridas sobre los pedidos y clientes.  
* 0011-2: Dividir la funcionalidad en varias clases, separando las estadísticas de los pedidos y las de los clientes.  

## Decision Outcome  

Chosen option: 0011-1: Crear una única clase que gestione todas las estadísticas requeridas sobre los pedidos y clientes. Esto simplifica el diseño y facilita la implementación inicial, siendo suficiente para cumplir con los requisitos RF-4.1 y RF-4.2.  

## Pros and Cons of the Options  

### Crear una única clase para gestionar estadísticas de pedidos y clientes  

* Good, because centraliza todas las estadísticas relevantes en un solo lugar, simplificando el diseño.  
* Good, because es eficiente al minimizar dependencias y reducir la complejidad inicial.  
* Good, because facilita el mantenimiento básico, ya que toda la lógica de estadísticas está en un único componente.  
* Bad, because tiene escalabilidad limitada. En el futuro, la clase podría requerir una refactorización si se amplían las funcionalidades estadísticas.  
* Bad, because aumenta el acoplamiento, combinando estadísticas de naturaleza distinta (pedidos y clientes) en una sola entidad.  

### Dividir la funcionalidad en varias clases  

* Good, because mejora la modularidad al asignar responsabilidades específicas a cada clase, facilitando la extensión futura.  
* Good, because ofrece mayor flexibilidad para introducir nuevas estadísticas o adaptar los cálculos existentes.  
* Bad, because incrementa la complejidad inicial con más clases y relaciones entre ellas.  
* Bad, because requiere más tiempo y esfuerzo de desarrollo, lo cual no es necesario para cumplir los requerimientos actuales.  
