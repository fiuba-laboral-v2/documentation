# Servicio de Email

En el `back-end` existe un servicio de email (`EmailService`) que utiliza la 
API `Soap` que provee la Facultad. Este servicio tiene una política de reintentos
en caso de que el envío falle.

Existe un archivo de configuración `EmailServiceConfig` el cual tiene definido 
una serie de números que representa el intervalo en segundos para volver a 
realizar un intento caa vez que el envío del email falle hasta que el intervalo 
se termine. 

En caso de que en algún re-intento se envíe el email exitosamente, se loguea 
un registro de éxito en la  tabla `NotificationEmailLogs`.
En caso de que se venza dicho intervalo, se loguea un registro de error en la 
tabla `NotificationEmailLogs`:

La tabla `NotificationEmailLogs` contiene:

* `notificationUuid`: Referencia a la notificación enviada (No tiene una ForeignKey a nivel base de datos)
* `notificationTable`: Nombre de la tabla a la cual pertenece la notificación
* `success`: Booleano que indica si el mail se envió exitosamente
* `message`: Mensaje sobre la operación. En caso de error especifica el error que el servicio devuelve. En caso contrario muestra un mensaje de éxito
* `createdAt`: Fecha de creación del registro
