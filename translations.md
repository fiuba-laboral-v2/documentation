# Traducciones

Es importante tener en cuenta que los textos que se ven en la aplicación están 
escritos en un archivo del backend llamado `src/models/Translation/defaultTranslations.ts.`
Este archivo tiene un objeto de Typescript donde cada key lo denominamos 
`translationGroup` y dentro del grupo están las traducciones correspondientes. Esto
se hizo así de manera tal de hacer una sola request desde el `front-end` 
para obtener las traducciones de cierto componente solicitando su grupo 
correspondiente.

Existe una query de GraphQL en el `back-end` llamada `getTranslations` la cual 
recibe un `translationGroup` y devuelve el conjunto de traducciones. 

Y en el `front-end` existe un hook llamado `useTranslations` el cual recibe un
`translationGroup` y un tipo de Typescript para determinar la interfaz de 
traducciones a retornar como se ve a continuación:

```Typescript
const translations = useTranslations<{ title: sting }>("applicantList");
```

## Nombre de las secretarías

En caso de que una secretaría cambie de nombre hay que modificar el nombre 
correspondiente en el `translationGroup` de `institutions` en el archivo
`src/models/Translation/defaultTranslations.ts.` que tiene este formato:

```
institutions: {
    extension: string;
    graduados: string;
}
```
