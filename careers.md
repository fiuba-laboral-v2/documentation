# Carreras

## Agregar una nueva carrera a la base de datos

Para agregar una nueva carrera a la base de datos productiva se debe agregar 
un nuevo archivo en el directorio de seeders productivos del backend (`src/seeders/production`).
Este archivo debe seguir la convención de nombres del resto de archivos productivos,
es decir, `<timestamp>-add-<nombre de la carrera>-career`.

Y se debe escribir un comando para crear y dar de baja la misma de la base de datos
de la siguiente manera:

> **_NOTE:_**  Los datos a continuación son inventados para mostrar un ejemplo.

```Typescript
import { QueryInterface } from "sequelize";
import { Environment } from "../../config/Environment";

const TABLE_NAME = "Careers";
const careerCode = "900";

export = {
  up: async (queryInterface: QueryInterface) => {
    if (Environment.NODE_ENV() !== Environment.PRODUCTION) return;

    return queryInterface.bulkInsert(TABLE_NAME, [
      {
        code: careerCode,
        description: "Ingeniería en Robótica",
        createdAt: new Date(),
        updatedAt: new Date()
      }
    ]);
  },
  down: async (queryInterface: QueryInterface) => {
    if (Environment.NODE_ENV() !== Environment.PRODUCTION) return;
    return queryInterface.bulkDelete(TABLE_NAME, { code: careerCode }, {});
  }
};

```

Para correr este seeder y agregar la carrera, se debe ejecutar:
```bash
yarn db:seed:up:production <timestamp>-add-<nombre de la carrera>-career.js
```
Y para eliminar la carrera , se debe ejecutar:
```bash
yarn db:seed:down:production~~~~ <timestamp>-add-<nombre de la carrera>-career.js
```
