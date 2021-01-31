# Servicio de Email

En el `back-end` existe un servicio de email (`EmailService`) que utiliza la 
API `Soap` que provee la Facultad. Este servicio tiene una política de reintentos
en caso de que el envío falle.

Existe un archivo de configuración `EmailServiceConfig` el cual tiene definido 
una serie de números que representa el intervalo en segundos para volver a 
realizar un intento cada vez que el envío del email falle hasta que el intervalo 
se termine. 

Se loguea el resultado de todos los requests de envío de email a la 
tabla `NotificationEmailLogs`.

La tabla `NotificationEmailLogs` contiene:

* `notificationUuid`: Referencia a la notificación enviada (No tiene una ForeignKey a nivel base de datos)
* `notificationTable`: Nombre de la tabla a la cual pertenece la notificación
* `success`: Booleano que indica si el mail se envió exitosamente
* `message`: Mensaje sobre la operación. En caso de error especifica el error que el servicio devuelve. En caso contrario muestra un mensaje de éxito
* `createdAt`: Fecha de creación del registro

###### [Eliminación periódica de registros](PeriodicRemoval.md)
