# Tablas de log de acciones del administrador

Existe una tabla para registrar el historial de las acciones de moderación 
(aprobación y rechazo) por cada tipo de entidad, es decir, una tabla para 
`Companies`, otra para `Applicants`, otra para `Offers` y otra para `JobApplications`.  

Cada vez que un administrador aprueba o rechaza una de estas entidades, se 
loguea en la tabla correspondiente el nuevo estado de la entidad 
(aprobado, rechazado, pendiente de aprobación), una referencia al admin que 
realizó la acción (`userUuid`), una referencia a la entidad moderada, el motivo 
de rechazo en caso de haber rechazado la entidad y la fecha en que sucedió el 
evento (`createdAt`).

Estas tablas se llaman:
 * `ApplicantApprovalEvents`
 * `CompanyApprovalEvents`
 * `OfferApprovalEvents`
 * `JobApplicationApprovalEvents`

No hay frontend para estas tablas, pero es útil saber que existen para 
responder consultas de las secretarías. También, podría agregarse una 
sección para admins que junte estas cuatro tablas y las presente en orden 
cronológico.
