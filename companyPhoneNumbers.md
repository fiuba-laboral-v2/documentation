# Números de teléfono de empresa

Existe un modelo que se llama `CompanyPhoneNumber` el cual representa un número 
de teléfono de una empresa. Estos se persisten en la tabla `CompanyPhoneNumbers`.

Actualmente este modelo no se usa pero es útil saber que existen en caso de querer
que una empresa pueda agregar a su perfil diferentes números de contacto.

Para agregarlos se tendría que agregar al formulario de edición del perfil de 
empresa. Hay que tener en cuenta que existe en el repositorio de `validations`, 
un validator llamado `validatePhoneNumber` que se puede usar en el `front-end` de 
manera tal de reutilizar este validador que usa el modelo `CompanyPhoneNumber`.

Finalmente habría que agregar un argumento `phoneNumbers` a la mutation 
`updateCurrentCompany` que sea un array de strings. Y dentro del resolver de la 
mutation se debería usar el repositorio `CompanyPhoneNumberRepository` dentro de
la transacción.
