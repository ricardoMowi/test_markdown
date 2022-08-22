# Guía de pruebas unitarias

[[_TOC_]]


## Requerimientos previos

* Jest (viene instalado con create react app)
* Enzyme
* Enzyme adapter react 16
* Enzyme to JSON
* Redux mock store

## Proceso de instalación

### NPM

```
npm i --save-dev enzyme enzyme-adapter-react-16 
npm i --save-dev redux-mock-store
```

### Yarn

```
yarn add --dev enzyme enzyme-adapter-react-16 
yarn add --dev redux-mock-store
```


### Estructura de creación de pruebas
La creación de pruebas se realizará a la altura del componente con la extensión .test.jsx 
La creación de los snapshots se realizará dentro de una carpeta llamada __snapshots__ a la altura de del componente, dichos snapshots se harán con la extensión .test.jsx.snap
 
### Ejemplo de integración


```
import React from 'react';
import { shallow } from 'enzyme';
import Button from './Button';

describe('Test Button component', () => {
  it('Test click event', () => {
    const mockCallBack = jest.fn();

    const button = shallow((<Button onClick={mockCallBack}>Ok!</Button>));
    button.find('button').simulate('click');
    expect(mockCallBack.mock.calls.length).toEqual(1);
  });
});
```

**Nota:** Se debe debe tener como mínimo un 80% de cobertura de código.

