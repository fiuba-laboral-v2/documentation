# Tablas de log de acciones del administrador

Existe una tabla para registrar el historial de las acciones de moderación 
(aprobación y rechazo) por cada tipo de entidad, es decir, una tabla para 
`Companies`, otra para `Applicants`, otra para `Offers` y otra para `JobApplications`.  

Cada vez que un administrador modera una de estas entidades ya sea rechazándolas, 
aprobándolas o moviéndolas a pendiente, se loguea en la tabla correspondiente 
el estado al cual la entidad fue actualizada, una referencia al admin que 
realizó la acción, una referencia a la entidad moderada, el mensaje de rechazo 
en caso de haber rechazado la entidad y la fecha de creación del evento.

Estas tablas se llaman:
 * ApplicantApprovalEvents
 * CompanyApprovalEvents
 * OfferApprovalEvents
 * JobApplicationApprovalEvents

Estas tablas actualmente no se muestran a ningún usuario pero tienen el
potencial de ser utilizadas para saber qué acciones realizó un administrador mostrando 
los datos que estas tablas contienen, explicados anteriormente.  

En el futuro podría usarse para mostrar a todos los administradores concentrando 
la información de las cuatro tablas en una sola sección de manera tal de poder ver 
las acciones de moderación ya que podría ser muy útil consultar esta
información donde se conoce quién realizó la moderación, cuando, y en caso de 
rechazo, el motivo.
