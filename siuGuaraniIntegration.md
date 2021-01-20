# Integración de la aplicación con los datos del SIU Guaraní

La integración consiste en actualizar qué carreras los postulantes están cursando o 
finalizaron y su progreso. También implica actualizar qué carreras ofrece la facultad
con las carreras que existen en la aplicación.

Las carreras de un postulante están persistidas en la tabla ApplicantCareers, la cual es
una tabla de join entre las tablas Applicants y Careers, Y hay que tener en cuenta que
un Applicant pertenece a un User. Entonces la integración consiste en usar un 
servicio externo donde usando el dni del usuario asociado al applicant, 
obtener qué carreras tiene el mismo.

La tabla ApplicantCareers contiene la siguiente información:
    * careerCode: una referencia al código de carrera en la tabla Careers
    * currentCareerYear: El año de cursada en la facultad si no se graduó de la carrera
    * approvedSubjectCount: La cantidad de materias aprobadas si no se graduó de la carrera
    * isGraduate: Un booleano para saber si se graduó de la carrera
    * applicantUuid: Una referencia a la clave primaria de la tabla Applicants


Finalmente tenemos la tabla Careers la cual tiene los siguientes datos:
    * code: Código de la carrera
    * description: Nombre de la carrera

La idea de la integración sería que a través de un servicio, obtener las carreras
que la facultad ofrece y actualizar esta tabla.
