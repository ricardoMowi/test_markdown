## Styled Components
Para dar estilos a los componentes usamos [Styled componentes](https://styled-components.com/)
Es importante diferenciar los componentes que solo tengan estilos y que se usen sólo para maquetado. Para esto se deben usar el sufijo **styled** para los componentes que solo tienen estilos.

```
// Ejemplo
const styled from 'styled-components';

const ContainerStyled = styled.div`
  background: red;
  ...
`

const Movies = () => {
  ... 
  return (
     <ContainerStyled>
       ...
     </ContainerStyled>
  );
};
```
```
// Ejemplo con un componente existente
const styled from 'styled-components';

const HomeLink = ({ className, children }) => (
  <a className={className}>
    {children}
  </a>
);

const HomeLinkStyled = styled(Link)`
  color: palevioletred;
  font-weight: bold;
`;
```

### Archivos externos
Los componentes generados por el styled component deben ubicarse en un archivo styles.jsx junto al dominio que lo usará.

```
// ejemplo
- MyComponentExample
  - index.jsx
  - styles.jsx
```

```
// ejemplo
- OptionsList
  - Option.jsx
  - List.jsx
  - styles.jsx
```