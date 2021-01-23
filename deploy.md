# Deploy

## Pasos iniciales

En el servidor se asume que están instalados:
* Linux
* Apache ([instrucciones de instalación](https://ubuntu.com/tutorials/install-and-configure-apache#2-installing-apache))
* Docker ([instrucciones de instalación](https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository))
* Docker Compose ([instrucciones de instalación](https://docs.docker.com/compose/install/#install-compose))
* Un server de ssh: `sudo apt install openssh-server openssh-client`

La aplicación a deployar es un html estático compilado de una aplicación React (`front-end`) y un servidor (`back-end`) que persiste en una base de datos PostgreSQL.

Se exponen ambos via Apache, en dos direcciones diferentes (por default, "/" y "/graphql" respectivamente).

## Repositorio de deploy

En el repositorio [deploy](https://github.com/fiuba-laboral-v2/deploy) hay scripts que se pueden correr en cualquier máquina, y se conectan al servidor via ssh:
* `NODE_ENV=production yarn deploy:setup`
* `NODE_ENV=production yarn deploy:backend`
* `NODE_ENV=production yarn deploy:frontend`

En la máquina que vayan a correr los script se asumen instalados:
* Linux
* Node version manager (o nvm, [instrucciones de instalación](https://github.com/nvm-sh/nvm#install--update-script)), e instalado vía nvm, node v14.15.0.
* Yarn: `sudo apt install --no-install-recommends yarn`

Pasos a seguir:

1. Forkear los repositorios a otro usuario u organización de GitHub
2. Nombrar "production" al branch principal de `front-end` y `back-end`
3. Actualizar las variables de configuración (explicadas más abajo) en la sección "production" de los siguientes archivos del repo `deploy`:
   * `src/config/deploy.ts`
   * `src/config/Repository/Frontend.ts`
   * `src/config/Repository/Backend.ts`
4. Pararse sobre la carpeta raíz del repo deploy
5. Instalar las dependencias del repo de deploy: `yarn install`
6. Ejecutar el comando `NODE_ENV=production yarn deploy:setup`
7. Modificar en el server el archivo `~/fiuba-laboral-v2/back-end/.env`, agregar variables tal que quede:
   ```
    NODE_ENV=production
    DATABASE_URL=postgresql://user:password@netlocation:port/dbname
    JWT_SECRET=cualquier string: se utiliza para encriptar las contraseñas
    EMAIL_API_APPLICATION_ID=lo que se pone en <aplic_id xsi:type="xsd:string">
    EMAIL_API_PASSWORD=lo que se pone en <password xsi:type="xsd:string">
    EMAIL_API_URL=<url del servicio de SOAP de Fiuba>/misc.php
    FIUBA_USERS_API_URL=<url del servicio de SOAP de Fiuba>/usuarios.php
   ```
8. Ejecutar el deploy del `front-end` y el `back-end` con los 
comandos (`NODE_ENV=production yarn deploy:frontend` y 
`NODE_ENV=production yarn deploy:backend`, respectivamente). 
Repetir este paso cada vez que se quieran subir los últimos cambios del 
repositorio correspondiente.

Tener en cuenta que el deploy fue preparado para un ambiente de staging que no usa https. Pueden ser necesarias modificaciones para contemplar ese caso.

Después de cualquier modificación en el repo de deploy hay que correr nuevamente `yarn install` ya que así se vuelve a compilar el código typescript.

### Variables de configuración

* `src/config/deploy.ts`
   * `hostname`: desde el que se accede públicamente a lo que sirve apache (ejemplo: "bolsadetrabajo.fi.uba.ar")
   * `frontendPath`: path en la url donde se accede a la aplicación (con "/" al principio y no al final, por ejemplo "/" o "/frontend")
   * `sshAddress`: para conexión ssh (ejemplo: "dylan@bolsadetrabajo.fi.uba.ar")
   * `user`: usuario de la sesión en el server (ejemplo: "dylan")
* `src/config/Repository/Frontend.ts`
   * `publicUrl`: url completa desde donde se va acceder al frontend de la aplicación (ejemplo: https://bolsadetrabajo.fi.uba.ar)
   * `gitRepository.url`: url ".git" del repositorio
   * `gitRepository.location`: carpeta donde se va a clonar el repositorio
   * `gitRepository.branch`: nombre del branch
* `src/config/Repository/Backend.ts`
   * `containerName`: nombre del container de docker que va a ser creado o actualizado al deployar el backend
   * `gitRepository.url`: url ".git" del repositorio
   * `gitRepository.location`: carpeta donde se va a clonar el repositorio
   * `gitRepository.branch`: nombre del branch

### Qué hace `NODE_ENV=production yarn deploy:setup`

En `scripts/setup.js` se ejecuta via ssh el archivo `setup.sh`. Este prepara a Apache para exponer el frontend y el backend. Este usa a `set_default_settings.sh`. En dichos archivos está descrito el propósito de cada paso.

### Qué hace `NODE_ENV=production yarn deploy:frontend`

En `scripts/deploy_frontend.ts` se clona la última versión del repositorio, se compila el html con sus assets, se borra el html preexistente y se lo reemplaza con el recién compilado.

### Qué hace `NODE_ENV=production yarn deploy:backend`

En `scripts/deploy_backend.ts` se clona o actualiza el repositorio en la carpeta especificada, se construye y se ejecuta el contenedor de docker via docker-compose, y se corren las migraciones sobre la base de datos. Finalmente, se corre `docker image prune --force` para eliminar las imágenes sin usar en docker.

En el repositorio `back-end`, el archivo `docker-compose.yml` muestra la configuración para construir y ejecutar los contenedores (el servidor del backend, y adicionalmente, en desarrollo o staging, una base de datos postgres dockerizada). Tienen seteado `restart: always`, es decir que al fallar o tras un corte de luz van a volver a levantarse solos.

En `Dockerfile` se especifica que el contenedor del server corre `yarn pm2:start`. En `package.json`, sección de `scripts` se ve que este comando ejecuta la aplicación node via pm2, que básicamente se encarga de instanciar múltiples procesos y manejar su creación y destrucción según reglas definidas en `config/process.yml`, y documentadas [en el sitio de pm2](https://pm2.keymetrics.io/docs/usage/application-declaration/#advanced-features).

Hoy se levanta en modo cluster ([documentación](https://pm2.keymetrics.io/docs/usage/cluster-mode/)), con `instances: max` (una por núcleo del procesador), y `max_memory_restart: 250M`. Modificar según sea necesario.
