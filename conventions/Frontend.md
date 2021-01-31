# Convenciones del Front End

* Todas las páginas deben estar bajo la carpeta `src/pages`.

* Todas las páginas deben estar a su vez dentro de las carpetas, `Applicant`, 
`Company` o `Admin`.

* Las carpetas `Applicant`, `Company` o `Admin` van a tener su conjunto de 
sub-rutas para acceder a sus respectivas páginas.

* Todas las rutas deben ser incluidas en `RoutesBuilder`.

* Los componentes que son comunes a varias páginas deben ser guardados en la 
carpeta `src/components`.

* Los componentes que se usan solo en una page, deben ser escritos en la 
carpeta de la page.

* Todos los componentes se escriben dentro de una carpeta con el nombre del 
componente con la primer letra en mayúscula.

* En un principio, si una interfaz se usa solo en un archivo, la interfaz se 
declara ahí mismo. Si se necesita en dos archivos distintos, se la declara en 
un archivo `interfaces.ts`, en la carpeta donde se lo considere más apropiado.
