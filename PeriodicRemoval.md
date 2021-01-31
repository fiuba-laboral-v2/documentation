# Eliminación periódica de registros

Actualmente las tablas `CompanyNotifications`, `ApplicantNotifications`, 
`AdminNotifications` y `NotificationEmailLogs` tienen una política de 
eliminación periódica de sus filas.

En 1 de cada 1000 inserciones a una de esas tablas se borran los registros de 
más de N meses de antigüedad. N se define en la configuración del 
archivo `CleanupConfig`.
