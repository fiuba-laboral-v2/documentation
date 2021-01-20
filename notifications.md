# Notificaciones

Las notificaciones se guardan en las tablas:

* `ApplicantNotifications`:
    * Postulación a oferta de trabajo aprobada (`approvedJobApplication`)
    * Postulación a oferta de trabajo rechazada (`rejectedJobApplication`)
    * Postulación a oferta de trabajo pendiente de aprobación (`pendingJobApplication`)
    * Perfil aprobado (`approvedProfile`)
    * Perfil rechazado (`rejectedProfile`)
* `CompanyNotifications`:
    * Postulación a oferta de trabajo aprobada (`newJobApplication`)
    * Oferta de trabajo rechazada (`rejectedOffer`)
    * Oferta de trabajo aprobada (`approvedOffer`)
    * Perfil de empresa aprobado (`approvedProfile`)
    * Perfil de empresa rechazado (`rejectedProfile`)
* `AdminNotifications`
    * Perfil de empresa actualizado (`updatedCompanyProfile`)
    
###### Eliminación periódica

Finalmente, hay que tener en cuenta que puede ser necesario eliminar las 
notificaciones periódicamente en las tres tablas de manera tal de evitar 
tener acumulado muchas notificaciones viejas en las tablas.
