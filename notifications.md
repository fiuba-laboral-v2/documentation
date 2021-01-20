# Notificaciones

Las Notificaciones son entidades que los administradores, usuarios de empresa y 
postulantes pueden ver según distintos tipo de eventos, por lo tanto existen tres tablas
para cada uno de estos tres de manera de distribuir las mismas.  

Las tablas son ApplicantNotifications, CompanyNotifications y AdminNotifications y 
los tipos de notificaciones que pueden ver cada uno de ellos son los siguientes:

* ApplicantNotifications:
    * Postulación a oferta de trabajo aprobada
    * Postulación a oferta de trabajo rechazada
    * Perfil aprobado
    * Perfil rechazado
* CompanyNotifications:
    * Postulación a oferta de trabajo aprobada
    * Oferta de trabajo rechazada
    * Oferta de trabajo aprobada
    * Perfil de empresa aprobado
    * Perfil de empresa rechazado
* AdminNotifications
    * Perfil de empresa actualizado
    
###### Eliminación periódica

Por lo tanto puede ser necesario eliminar las notificaciones periódicamente
en las tres tablas de manera tal de evitar tener acumulado muchas notificaciones
viejas en las tablas
