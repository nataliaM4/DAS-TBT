---
parent: Decisions
nav_order: 100
title: 0001-Gestión Segura de Datos Personales de Clientes
status: Proposed
date: 2024-10-31
decision-makers: ["Arquitectos Senior de Software (ASS)"]
consulted: ["Arquitectos de Software Certificados (ASC)"]
informed: ["Equipo de Desarrollo", "Departamento de Seguridad", "Administración de Datos"]

---

# Gestión Segura de Datos Personales de Clientes

## Contexto y Declaración del Problema

La empresa planea migrar su arquitectura monolítica a una basada en microservicios para mejorar la flexibilidad y escalabilidad. Como parte de esta migración, es fundamental gestionar de forma segura los datos personales de los clientes. El módulo de Clientes debe realizar operaciones CRUD de los datos de los clientes y permitir acceso al historial de pagos de cada cliente. Adicionalmente, se requiere implementar medidas de seguridad y control de acceso para proteger estos datos.

Actualmente, el sistema utiliza dos bases de datos SQL: una para almacenar la información y pagos de clientes (Customers) y otra para los datos de pedidos (Orders). Para cumplir con los requisitos de seguridad, se decidió implementar el Patrón de Cifrado de Datos y el Patrón de Control de Acceso.

---

## Impulsores de la Decisión

* RF01-Operaciones CRUD: El módulo de Clientes debe manejar las operaciones de creación, lectura, actualización y eliminación de datos de clientes.
* RF02-Historial de Pagos: El módulo debe proporcionar acceso seguro al historial de pagos.

---

## Opciones Consideradas

* **0001-1: Patrón de Cifrado de Datos y Control de Acceso**: Implementación de cifrado para datos sensibles y control de acceso basado en roles.
* **0001-2: Módulo de Autenticación Separado**: Creación de un módulo de autenticación separado en lugar de utilizar control de acceso dentro del módulo de Clientes.
* **0001-3: Uso de Algoritmo Alternativo AES-256**: Implementación de un cifrado alternativo con AES-256 en lugar del Patrón de Cifrado de Datos estándar.

---

## Resultado de la Decisión

Opción seleccionada: **0001-1: Patrón de Cifrado de Datos y Control de Acceso**, ya que esta opción cumple con los requisitos de seguridad y eficiencia en la gestión de datos personales y permite un control de acceso seguro al historial de pagos de cada cliente.

---

## Pros y Contras de las Opciones

### 0001-1: Patrón de Cifrado de Datos y Control de Acceso

* **Bueno**: Asegura la protección de los datos personales mediante cifrado.
* **Bueno**: Facilita un control de acceso basado en roles, restringiendo el acceso a personal autorizado.
* **Bueno**: Escalable y flexible, permitiendo una fácil integración con otros microservicios.
* **Malo**: Requiere esfuerzos adicionales de desarrollo y pruebas.
* **Malo**: Puede introducir sobrecarga en el rendimiento debido a las operaciones de cifrado y control de acceso.

### 0001-2: Módulo de Autenticación Separado

* **Bueno**: Aumenta la flexibilidad al permitir autenticación centralizada.
* **Malo**: Incrementa los esfuerzos de desarrollo y mantenimiento al requerir un módulo adicional.

### 0001-3: Uso de Algoritmo Alternativo AES-256

* **Bueno**: AES-256 es ampliamente conocido por su seguridad y confiabilidad.
* **Malo**: Requiere pruebas y validaciones adicionales para asegurar su integración con la arquitectura actual.

---

## Información Adicional

Se realizarán revisiones de diseño y pruebas de seguridad para validar la implementación del Patrón de Cifrado de Datos y Control de Acceso en otros microservicios. Este ADR será revisado y actualizado una vez completada la implementación para asegurar que la decisión sigue siendo válida y eficaz.
