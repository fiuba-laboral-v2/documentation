Exclusivo **Front-End**:

1) Todas las páginas deben estar bajo la carpeta `src/pages`.

2) Todas las páginas deben estar a su vez dentro de las carpetas, `Applicant`, `Company` o `Admin`.

3) Las páginas compartidas por las 3 aplicaciones, tales como un 404, deberán estar en `src/pages`.

4) Las carpetas `Applicant`, `Company` o `Admin` van a tener su conjunto de su-brutas para acceder a sus respectivas páginas.

5) Todas las rutas deben ser incluidas en `RoutesBuilder`.

6) Los componentes que son comunes a varias páginas deben ser guardados en la carpeta `src/components`.

7) Los componentes que se usan solo en una page, deben ser escritos en la carpeta de la page.

8) Todos los componentes se escriben dentro de una carpeta con el nombre del componente con la primer letra en mayúscula.

9) En un principio, si una interfaz se usa solo en un archivo, la interfaz se declara ahí mismo. Si se necesita en dos archivos distintos, se la declara en un archivo `interfaces.ts`, en la carpeta donde se lo considere más apropiado.
