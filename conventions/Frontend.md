# Convenciones del Front End

* La aplicación está dividida en páginas, cada una con su ruta. Las rutas 
se declaran en `RoutesBuilder` y cada una corresponde a un componente 
"page", en la carpeta `src/pages`.

* Las páginas son o para postulante, para company, para admin, o públicas. 
Esa división corresponde a las carpetas `Applicant`, `Company`,  `Admin` o `Public`.

* Las carpetas `Applicant`, `Company` o `Admin` van a tener su conjunto de 
sub-rutas para acceder a sus respectivas páginas.

* Los componentes que son comunes a varias páginas deben ser guardados en la 
carpeta `src/components`.

* Los componentes que se usan solo en una page, deben ser escritos en la 
carpeta de la page.

* Todos los componentes se escriben dentro de una carpeta con el nombre del 
componente con la primer letra en mayúscula.

* En un principio, si una interfaz se usa solo en un archivo, la interfaz se 
declara ahí mismo. Si se necesita en dos archivos distintos, se la declara en 
un archivo `interfaces.ts`, en la carpeta donde se lo considere más apropiado.
