# Integración de la aplicación con los datos del SIU Guaraní

Una posible integración es periódicamente actualizar las carreras que 
cursa cada `Applicant` y su avance en ellas.

El avance de un Applicant en una Career está en la tabla `ApplicantCareers`. 
Un `Applicant` "pertenece a" un `User`. En lo concreto, habría que, para todo 
`Applicant`, obtener el dni de su `User` y actualizar sus `ApplicantCareers` 
con la información dada por el SIU.

La tabla ApplicantCareers contiene la siguiente información:
    * careerCode: una referencia al código de carrera en la tabla Careers
    * currentCareerYear: El año de cursada en la facultad si no se graduó de la carrera (Sin CBC)
    * approvedSubjectCount: La cantidad de materias aprobadas si no se graduó de la carrera (Sin CBC)
    * isGraduate: Un booleano para saber si se graduó de la carrera
    * applicantUuid: Una referencia al Applicant
