# Integración de la aplicación con los datos del SIU Guaraní

Existe la posibilidad de que el sistema se alimente de los datos del 
SIU Guarani. Esto traería la ventaja de la certificación de validez de los 
datos de los estudiantes y graduados a la hora de utilizar la plataforma.
Actualmente se requiere que el usuario complete datos como el nombre, 
el padrón y el avance de sus carreras. Todo esto podría automatizarse 
posiblemente con un sync de datos en el login del usuario.

Una posible integración es periódicamente actualizar las carreras que 
cursa cada `Applicant` y su avance en ellas.

El avance de un `Applicant` en una `Career` está en la tabla `ApplicantCareers`. 
Un `Applicant` "pertenece a" un `User`. En lo concreto, habría que, para todo 
`Applicant`, obtener el dni de su `User` y actualizar sus `ApplicantCareers` 
con la información dada por el SIU.

La tabla `ApplicantCareers` contiene la siguiente información:
    * careerCode: Una referencia al código de carrera en la tabla Careers
    * currentCareerYear: El año de cursada en la facultad si no se graduó de la carrera (Sin CBC)
    * approvedSubjectCount: La cantidad de materias aprobadas si no se graduó de la carrera (Sin CBC)
    * isGraduate: Un booleano para saber si se graduó de la carrera
    * applicantUuid: Una referencia al `Applicant`


> **__NOTA:_**  Si FIUBA ofrece una nueva carrera o renombra una preexistente 
> están en [Carreras](careers.md)
