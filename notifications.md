# Notificaciones

Las notificaciones se guardan en las tablas `ApplicantNotifications`, 
`CompanyNotifications` y `AdminNotifications` y los tipos de notificación 
(en la columna `type` de cada tabla) son:

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
    
###### [Eliminación periódica de registros](PeriodicRemoval.md)
