# Eliminación periódica

Actualmente las tablas `CompanyNotifications`, `ApplicantNotifications`, 
`AdminNotifications` y `NotificationEmailLogs` tienen una política de 
eliminación periódica de sus filas.

Cada vez que se persiste un nuevo registro en alguna de estas tablas, se ejecuta un
random de manera tal que en caso de dar menor a 0.1, se borran los registros 
anteriores a cierta cantidad de meses. La cantidad de meses se lee del archivo 
de configuración `CleanupConfig`.
