[[_TOC_]]

# Implementación de componentes
Todos los componentes usados deben ser funcionales, ya no se dan soporte a **componentes basados en clases** dentro del proyecto.


Ejemplo de definición **correcta** de un componente.

```
function Component (props) {
  return <div />;
}

const Component = function (props) {
  return <div />;
};

const Component = (props) => {
  return <div />;
};

function getComponent () {
  return function (props) {
    return <div />;
  };
}

function getComponent () {
  return (props) => {
    return <div />;
  };
}
```
## Cada componente debe considerar
- Mantén los componentes pequeños y con funciones específicas. (**Los componentes no deben superar las 200 líneas**).
- Reutiliza, Mantén la necesidad de crear nuevos componentes en lo mínimo de la necesidad.
- Consolida el código duplicado ( Don’t Repeat Yourself (DRY) ).
- Comenta sólo si es necesario.
- Nombra al componente, después la función.
- **No console.log() dentro en el código integrado!!.**
- Todos los componentes deben tener la validación de props con [props-types](https://www.npmjs.com/package/prop-types) 
- Usa JSDOC para brindar una descripción de tu componente.

```
// Ejemplo
ProductTable 
Avatar
AuthorAvatar
```
- Capitaliza los nombres de los componentes.

```js
// Ejemplo

// good
SelectButton
Menu

//bad
selectbutton
menu
```
- Tus componentes deben ser testeables.
- Todos los archivos relacionados a un componente deben ubicarse dentro de una misma carpeta.


```
// Ejemplo
AwesomeCard/
├── index.jsx 
└── style.jsx // styled components
```

## Cosas que no debes hacer!
- Incluir un número dentro del nombre de un componente.
```js
// Ejemplo

<Movies1></Movies1> // No!!
<Card1></Card1> // No!!

```
- En los styled-componentes llamar nombrar un componente como una etiqueta nativa, esto porque se supone que cada componente debe tener una razón de ser y debe tener una abstracción previa.
```js
// Ejemplo

// No hacer esto!!!
const styled from 'styled-components';

const SPAN1 = styled.span`
  background: red;
`
const SPAN2 = styled.span`
  background: red;
`
// Si hacer
const styled from 'styled-components';

const MovieTitleStyled = styled.h1`
  background: red;
  span {
    font-size: 30px;
  }
`
```
