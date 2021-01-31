# Convenciones generales

* Las carpetas y archivos que refieren a entidades (en singular) como `Database`, `Environment`, `Admin`, `Logger` van en mayúscula.

* Las carpetas y archivos que actúan como contenedores (en general, en plural) 
como `graphql`, `config`, `models`, `migrations`, `defaultTranslations`, 
`queries`, `fieldTypes` van en minúscula. También los "sustantivos comunes", 
como `compontent` y `container` dentro de `NavBar`.

* No utilizar default export. Es preferible nombrar los exports (ejemplo: `export Database` en `Database.ts`)

* La estructura de carpetas de `/test` tiene que imitar la estructura de `/src`.

* Archivos y carpetas:
    * Para componentes react y types de graphql usar CamelCase.

* Las carpetas de los modelos en singular (`Company`). Dentro de la carpeta se pueden guardar los 
archivos `Model.ts`, `Repository.ts`, `Interface.ts`, etc.

* Los modelos se llaman sin ningún sufijo ni prefijo.

* Los tipos de `GraphQL` se guardan en una carpeta `Types` dentro de la carpeta de la entidad correspondiente
    * Esta tiene un index con un array y todos los types

* Los tipos de `GraphQL` se nombran como: **GraphQL&lt;TypeName&gt;**. Ejemplo: `GraphQLCompany`

* El ancho mínimo de viewport que soportamos es de 210px inclusive

* Todas las Queries y Mutations de Graphql deben ser guardadas en constantes en mayúsculas al momento de ser usadas.

## Convenciones del [Front End](Frontend.md)
