[[_TOC_]]


#Estructura de proyecto

Los proyectos frontend deberán estar alineados con a una arquitectura basada en módulos, esto para poder fomentar el reuso y la escalabilidad del proyecto.

La estructura de proyecto es la siguiente.


```js
- modules
  - sharedModule
    - ...
  - functionalityModule
    - assets
      -  images
    - models // bussiness logic
    - components
      - domain component folder
      - domain component folder
    - pages
    - context
    - hooks
    - services / api
    - helpers
    - router
    - constants
    - index.js
  - functionality
       - ...
- router
- hooks
```

Cada módulo deberá representar una funcionabilidad de la aplicación y deberá ser totalmente independiente.

## Assets
...
## Components
...

## Módulos
El módulo debe representar una la abstracción de una funcionalidad o la definición de un dominio el cual puede actuar de manera independiente dentro de la implementación.

### Index.js
Cada módulo debe tener un archivo "index.js" el cual exportará por defecto la estructura genérica de integración junto a algunos elementos que puedan ser reusables.

Esta deberá ser una función que devuelva un objeto. La función recibirá como parámetro la configuración de tu módulo. Esta configuración será útil para establecer comportamientos específicos, deshabilitar funcionalidades o parametrizar elementos dentro de tu módulo.
```js
// ./src/modules/example/index.js

const ExampleModule = (moduleProps) => ({
  pathBase: '/example',
  componentRouter: () => {
    return (
       <ExampleModuleConfigProvider config={moduleProps} >
         <ExampleModuleRouter />
       </ExampleModuleConfigProvider>
    );
  },
  navigationItems: [...]
});

export default ExampleModule;
```
#### Detalle de campos
- **pathBase** (string): Es será el path base de todas las rutas del módulo.
```js
'/example'
'/example/sub-route-one',
'/example/sub-route-two'
```
- **componentRouter** (compenent): Aquí irá tu componente router, es decir el componente que gestione todas las rutas del módulo. En esta parte puede ser envuelta con un provider de configuración el cual se encargará de disponibilizar todas la configuración através de todo el módulo.
```js
       <ExampleModuleConfigProvider config={moduleProps} >
         <ExampleModuleRouter />
       </ExampleModuleConfigProvider>
```
- **navigationItems** (Array<object>): Aquí irá el listado de de items de navegación para la barra lateral izquierda la cual serán cargadas cuando se este navegando dentro del pathBase ingresado anteriormente.
- **includeGlobalNavigation** (boolean): Si es _true_ se incluirá de manera automática los items de navegación global (inicio..);

## Pages
...

## Context
...
## Models
...

## Router
...

## Constants