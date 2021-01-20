# Tablas de log de acciones del administrador

Existe una tabla para loguear las acciones de moderación por cada tipo de entidad,
es decir, una tabla para Companies, Applicants, Offers y JobApplications.  
Cada vez que un administrador modera una de estas entidades ya sea rechazándolas, 
aprobándolas o moviéndolas a pendiente, se loguea en la tabla correspondiente el estado
al cual la entidad fue actualizada, una referencia al admin que realizó la acción,
una referencia a la entidad moderada, el mensaje de rechazo en caso de haber rechazado 
la entidad y la fecha de creación del evento.

Estas tablas se llaman:
 * ApplicantApprovalEvents
 * CompanyApprovalEvents
 * OfferApprovalEvents
 * JobApplicationApprovalEvents
