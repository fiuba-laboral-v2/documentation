# Servicio de Email

En el `back-end` existe un servicio de email (`EmailService`) que utiliza la 
API `Soap` que provee la Facultad. Este servicio tiene una política de reintentos
en caso de que el envío falle.

En el archivo de configuración `EmailServiceConfig` se define un array de 
números que representa cuánto tiempo se espera en segundos antes del siguiente 
re-intento.

Por ejemplo, dado el valor [1, 2, 3]:

* Se envía el mail y falla: se espera 1 segundo
* Se envía el mail y falla: se espera 2 segundos
* Se envía el mail y falla: se espera 3 segundos
* Se envía el mail y falla: no se vuelve a re-intentar

O por ejemplo:

* Se envía el mail y falla: se espera 1 segundo
* Se envía el mail y falla: se espera 2 segundos
* Se envía el mail correctamente

Se loguea el resultado de todos los requests de envío de email a la 
tabla `NotificationEmailLogs`.

La tabla `NotificationEmailLogs` contiene:

* `notificationUuid`: Referencia a la notificación enviada (No tiene una ForeignKey a nivel base de datos)
* `notificationTable`: Nombre de la tabla a la cual pertenece la notificación
* `success`: Booleano que indica si el mail se envió exitosamente
* `message`: Mensaje sobre la operación. En caso de error especifica el error que el servicio devuelve. En caso contrario muestra un mensaje de éxito
* `createdAt`: Fecha de creación del registro

###### [Eliminación periódica de registros](PeriodicRemoval.md)
