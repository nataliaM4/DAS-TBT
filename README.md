# DAS-TBT
DAS Proyect

Para migrar el sistema monolítico actual a una arquitectura de microservicios, primero es importante entender los componentes y la lógica de negocio que necesita ser desacoplada para que cada servicio pueda ser gestionado de manera independiente, escalable y eficiente. A continuación, te explico el proceso sin dejar ninguna característica, y aclararé términos cuando sea necesario.

Componentes y Módulos de Negocio:

	1.	Clientes (crítico):
Este componente maneja los datos personales de los clientes. Dado que se considera crítico, debe ser diseñado para que esté altamente disponible y seguro. La información personal debe estar bien protegida y el acceso debe ser eficiente. En la nueva arquitectura, este componente puede ser un microservicio independiente que interactúe con una base de datos dedicada a los clientes.
	2.	Pedidos (semi-crítico):
Este módulo permite a los clientes realizar pedidos de productos. Aquí, se define que un cliente puede intentar realizar un pedido hasta 3 veces antes de que se le bloquee temporalmente. El proceso de pedidos sigue un flujo en tres fases:
	•	Preprocesado del pedido: Validación inicial y verificación.
	•	Autorización: Verifica que el pedido cumpla con todas las reglas de negocio.
	•	Aceptación: Confirmación final y preparación para el reparto.
No es posible avanzar a la siguiente fase si la fase anterior no ha sido completada correctamente (esto es lo que llamamos una dependencia secuencial).
Para escalar este servicio y manejar un alto volumen de pedidos, la arquitectura debe permitir la creación de instancias adicionales de este microservicio cuando haya muchos pedidos en un corto período.
	3.	Reparto y rutas (crítico):
Este es un componente complejo que se encarga de organizar la entrega de los pedidos y optimizar las rutas de los camiones. El sistema debe ser capaz de gestionar flotas de transporte, y cuenta con dos algoritmos de optimización que se seleccionan dependiendo de la situación (por ejemplo, si un camión se está retrasando). Este componente es crucial para garantizar la entrega a tiempo de los productos.
	4.	Estadísticas (no crítico):
Este módulo genera informes y proporciona información en tiempo real sobre los pedidos y el estado de los camiones. Dado que no es crítico, no necesita los mismos niveles de disponibilidad y rendimiento que otros componentes. Sin embargo, ofrece información valiosa para el análisis del rendimiento y la toma de decisiones.
	5.	Incidencias (semi-crítico):
Este módulo informa sobre problemas que puedan surgir durante el reparto, como camiones averiados o entregas fallidas. Dado que impacta directamente en la logística, es importante que funcione correctamente, pero no es tan crítico como los módulos de Clientes o Pagos.
	6.	Pagos (crítico):
La empresa utiliza Stripe, que es una pasarela de pagos externa. Stripe es responsable de garantizar que los pagos se procesen de manera segura y cumplan con los estándares internacionales. Aunque es un sistema externo, debe integrarse sin problemas con los microservicios de la empresa para manejar los pagos de los clientes.

Elementos Clave de la Nueva Arquitectura:

	1.	Microservicios:
Cada uno de estos módulos mencionados se convertirá en un microservicio independiente. Los microservicios son pequeñas aplicaciones que realizan funciones específicas y pueden funcionar de forma independiente. Esto permite que cada servicio sea gestionado, actualizado y escalado sin afectar al resto del sistema.
	2.	Gateway (Puerta de enlace):
Este componente será el encargado de gestionar las solicitudes que provienen de los clientes (PC y móviles) y redirigirlas al microservicio adecuado. Actuará como un punto central de acceso, traduciendo las solicitudes HTTP/REST (un protocolo de comunicación entre aplicaciones) hacia los microservicios correctos.
	3.	Protocolos HTTP/REST:
REST es un estilo de arquitectura que utiliza HTTP para la comunicación entre aplicaciones. Cada microservicio puede exponer una API REST (interfaz de programación de aplicaciones) para permitir que otros servicios o clientes puedan interactuar con él.
	4.	Bases de datos desacopladas:
En la nueva arquitectura, es probable que cada microservicio tenga su propia base de datos (aunque puede que en algunos casos compartan). Esto se conoce como el principio de base de datos por servicio, lo que ayuda a evitar cuellos de botella y permite que cada servicio escale de manera independiente.
	5.	Escalabilidad:
Uno de los beneficios principales de una arquitectura de microservicios es que cada servicio puede ser escalado según sea necesario. Por ejemplo, si el servicio de pedidos experimenta una alta demanda, puedes aumentar su capacidad sin necesidad de tocar los otros servicios.
	6.	Resiliencia:
Dado que cada microservicio funciona de manera independiente, un fallo en un microservicio (por ejemplo, en el servicio de estadísticas) no afectará a los demás, asegurando que los servicios críticos sigan funcionando.
	7.	Mensajería y coordinación:
Servicios como pedidos y reparto, que tienen dependencias entre ellos, pueden usar sistemas de mensajería (como queues o eventos) para coordinarse entre sí de manera eficiente. Estos sistemas permiten que los microservicios se comuniquen sin bloquear el procesamiento de otros.

Beneficios de la Nueva Arquitectura:

	•	Menos rigidez: Los microservicios permiten una mayor flexibilidad y facilitan la adopción de nuevas tecnologías o actualizaciones sin necesidad de tocar todo el sistema.
	•	Escalabilidad: Cada microservicio puede escalarse de manera independiente según la demanda.
	•	Facilidad de mantenimiento: Si hay un error en un microservicio, no es necesario detener el sistema completo para solucionarlo.
	•	Resiliencia: Los fallos en un microservicio no afectan a los otros, manteniendo los servicios críticos activos.

Este enfoque permitirá que la compañía alimenticia tenga un sistema más flexible, escalable y fácil de mantener.