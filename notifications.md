# Notificaciones

Las Notificaciones son entidades que los administradores, usuarios de empresa y 
postulantes pueden ver a medida que suceden distintos tipos de eventos. 
Para el modelado de las mismas creamos tres tablas de notificaciones, 
una para cada tipo de usuario respectivamente. 

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

Finalmente, hay que tener en cuenta que puede ser necesario eliminar las 
notificaciones periódicamente en las tres tablas de manera tal de evitar 
tener acumulado muchas notificaciones viejas en las tablas.
