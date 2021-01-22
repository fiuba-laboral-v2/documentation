# Números de teléfono de empresa

Existe un modelo que se llama `CompanyPhoneNumber` el cual representa un número 
de teléfono de una empresa. Estos se persisten en la tabla `CompanyPhoneNumbers`.

Este modelo quedo incompleto y no se está usando actualmente en la aplicación. 
Si más adelante deciden agregarlo se podría realizar de la siguiente manera:

Se tendría que agregar al formulario de edición del perfil de 
empresa. Tener en cuenta que en el repositorio `validations` ya hay un 
validator: `validatePhoneNumber`. Se debe colocar en el formulario en 
el frontend de manera de reutilizarlo como se hace en el 
modelo back-end (`src/models/CompanyPhoneNumber/Model.ts`)

Finalmente habría que agregar un argumento `phoneNumbers` a la mutation 
`updateCurrentCompany` que sea un array de strings. Y dentro del resolver de la 
mutation se debería usar el repositorio `CompanyPhoneNumberRepository` dentro de
la transacción.
