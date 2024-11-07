---
status: "proposed"
date: 2024-11-07
decision-makers: Adrián Muñoz y Delia Martínez
consulted: ASC
informed: ASJ y ASC
---

# Arquitectura de Microservicios para la Gestión de Pedidos

## Context and Problem Statement

El sistema actual de gestión de pedidos es monolítico, lo que dificulta su escalabilidad y mantenimiento. Se requiere una arquitectura más flexible y modular que permita gestionar de forma eficiente las solicitudes de pedidos de los clientes, el procesamiento de pedidos y la gestión de incidencias en las entregas. La migración hacia una arquitectura de microservicios mejorará la eficiencia, la escalabilidad y la mantenibilidad del sistema.


## Decision Drivers

* **RF-3:** Gestionar pedidos: La aplicación debe proporcionar una manera de gestionar todas las peticiones de los pedidos de clientes.
* **RF-3.1:** Realizar pedido: La aplicación debe permitir al cliente realizar un pedido de los productos a la empresa. Cuando un pedido se realice correctamente, el sistema de pedidos preprocesa el pedido, lo autoriza y lo acepta.
* **RF-5.1:** Reportar incidencias: La aplicación tiene que permitir que se reporten las incidencias y les lleguen a los gestores de las rutas.
* **RF-5.2:** Gestionar incidencias: La aplicación debe permitir gestionar las incidencias en el reparto.
* **RF-6:** Pasarela de pago: La aplicación debe poder redirigirnos a la pasarela de pago STRIPE para realizar un pago.


## Considered Options

* 0004-1: Utilizar una malla de servicios o una cola de mensajes para manejar el servicio de gestión de pedidos y mejorar la escalabilidad del sistema.
* 0004-2: Implementar mecanismos adicionales como caché o balanceo de carga para mitigar la latencia y mejorar el rendimiento del sistema.


## Decision Outcome

Se ha decidido optar por la **Arquitectura de Microservicios**, utilizando el **Patrón API Gateway** para gestionar las solicitudes de los clientes. A pesar de que el **Patrón API Gateway** puede introducir latencia y sobrecarga, se considera adecuado para proporcionar una interfaz unificada para acceder a los microservicios de forma escalable, centralizando la autenticación, el enrutamiento y la gestión de llamadas a APIs externas.

* Good, because simplifica el código del cliente y reduce el número de interacciones entre el cliente y el servidor.
* Good, because facilita el manejo de la autenticación, la autorización y las APIs externas mediante el uso de un API Gateway.
* Bad, because existe pérdida de la posibilidad de atención preferente de incidencias prioritarias.


## Pros and Cons of the Options

### **Main Decision: Arquitectura de Microservicios con Patrón API Gateway**

#### Pros
* **Simplificación del Código del Cliente**: El uso de un API Gateway reduce el número de interacciones directas entre el cliente y los servicios, simplificando el código del cliente y mejorando su mantenibilidad.
* **Reducción de los Viajes de Red**: Al consolidar varios microservicios en un solo punto de entrada, el API Gateway reduce la cantidad de viajes de red entre el cliente y la aplicación, mejorando la eficiencia.
* **Interfaz Unificada para los Clientes**: El API Gateway proporciona una única interfaz unificada para que los clientes accedan a todos los microservicios, mejorando la consistencia del sistema y simplificando la lógica del lado del cliente.
* **Gestión de Límites de Tasa y APIs Externas**: El API Gateway se puede utilizar para gestionar los límites de tasa y las llamadas a APIs externas, asegurando que el sistema no se vea abrumado y pueda manejar el tráfico externo de manera eficiente.

#### Cons

* **Complejidad Aumentada del Sistema**: La introducción de un API Gateway añade una capa adicional al sistema que debe ser gestionada y mantenida. Esto puede aumentar la complejidad de la arquitectura, especialmente al tratar con un gran número de servicios.
* **Impacto Potencial en el Rendimiento**: La capa adicional del API Gateway podría afectar negativamente el rendimiento del sistema, especialmente cuando se maneja un volumen alto de tráfico. Esto puede generar tiempos de respuesta más lentos y cuellos de botella.
* **Costos de Desarrollo, Implementación y Gestión**: Implementar y mantener un API Gateway requiere esfuerzos de desarrollo adicionales y recursos. La complejidad añadida también genera mayores costos asociados con la implementación, monitoreo y mantenimiento.
* **Punto Único de Falla**: El API Gateway representa un punto único de falla en el sistema. Si el gateway experimenta problemas, podría interrumpir toda la comunicación entre los clientes y los microservicios.

#### Decisión Alternativa 1: Usar una Malla de Servicios o una Cola de Mensajes

* **Good**, because una malla de servicios o una cola de mensajes mejoraría la escalabilidad y el rendimiento del sistema al desacoplar los servicios y permitir una comunicación más flexible entre microservicios.
* **Bad**, because implementar una malla de servicios o una cola de mensajes podría agregar complejidad adicional y requerir más recursos para gestionar y monitorear el sistema distribuido de manera efectiva.


#### Decisión Alternativa 2: Implementar Caching o Balanceo de Carga

* **Good**, because los mecanismos de caching y balanceo de carga pueden mejorar el rendimiento al reducir la carga en los microservicios y distribuir el tráfico de manera más eficiente.
* **Bad**, because implementar estos mecanismos introduce más complejidad operativa y podría requerir cambios significativos en la infraestructura existente.
