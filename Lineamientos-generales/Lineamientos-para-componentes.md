[[_TOC_]]


Todos los componentes agregados en la ui elements deben considerar los siguientes puntos para poder asegurar el reuso, escalabilidad y mejor manejo de los componentes.

# Consideraciones en los nuevos componentes.
## Apertura a nuevas props
Es importante cumplir con el "Open-Closed Principle" para los componentes, por eso cada uno de los componentes deberá tener solo los props necesarios para trabajar. 

Un desarrollar deberá estar en la capacidad de usar props no mapeadas y que son naturales de los componentes, para lograr esto el restantes de propiedades enviadas al componentes deben ser aplicadas al componente nativo que estemos usando.

Ejemplo:

```js
import styled from 'styled-components';

const CustomButtonStyled = styled`
   background-color: red;
`:

const MyCustomButton = (props) => {
   return (
      <CustomButtonStyled {...props} >
         { props.children }
      </ CustomButtonStyled >
   );
};
```

De esta manera podría hacer algo como:

```js
<MyCustomButton id="name-button" className={'tw-text-right'}> Content <MyCustomButton />
```

Sin necesidad de modificar el componente.

## Pruebas unitarias
Todos los componentes ingresados en la ui elements deben contar con sus pruebas unitarias respectivas. Esto es importante porque aseguramos el correcto funcionamiento en sus integraciones. [Más información.](/Magna/Frontend/Lineamientos-generales/Estándares-de-Programación/Pruebas-Unitarias)

## Integración con temas
Todos los componentes deben tener soporte a los temas. Por lo que los colores con los que sean desarrollados deben ser sacados de la base de temas y no colocados de manera estática.

Recuerda que el componente debe tener un tema por defecto y estar abierto al uso de otra configuración.

- Usamos el GlobalStyle para generar el tema https://dev.azure.com/PrimaAFPTeam/PrimaFrontend/_git/prima-ui-elements?path=%2Fsrc%2Flib%2Futils%2Ftheme%2FGlobalStyle%2Findex.jsx
- Aquí esta el listeado actual de temas https://dev.azure.com/PrimaAFPTeam/PrimaFrontend/_git/prima-ui-elements?path=%2Fsrc%2Flib%2Futils%2Ftheme%2FGlobalStyle%2Fthemes.js.
- Todos los componentes deberán ser capaces de recibir una prop "theme" en tipo de string que pueden ser "orange", "green", etc.
- Internamente deberás usar la información del tema proporcionado. Es importante dejar un tema por defecto.
Puedes usar el hook "useOrverrideTheme" con el cual podrás evaluar tu props theme y te devolverá la información correspondiente al tema.

```js
import { useOrverrideTheme } from '../../../utils/theme/customization/useTheme';
import styled from 'styled-components';
...

const CustomButtonStyled = styled`
   background-color: ${ props => props.theme?.button?.mainColor }
`; 

const MyComponente = (props) => {
  const { overrideTheme } = useOrverrideTheme(props.theme);

  return (
    <CustomButtonStyled {...props} {...overrideTheme} >
    </ CustomButtonStyled>
  );
};


```


