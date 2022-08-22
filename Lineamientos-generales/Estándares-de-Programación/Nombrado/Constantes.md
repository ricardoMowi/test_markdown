Es importante poder declara variables constantes. Estos nos permitirán poder setear valores que puede ser configurables posteriormente por lo que es importante conocer donde colocarlas y que sean fáciles de identificar.

#Nomenclatura
Todas las variables deben ser declaradas con UPPER_SNAKE_CASE con un nombre claro y sin abreviaciones. Evitar nombres genéricos.

```
// good

const SESSION_COOKIE_NAME = 'cookie';
...
const APPROVED_CODE = 1;

```

```
// bad

const COOKIE = 'cookie';
const approvedCode = 1;

```

#Ubicación
Las estas variables puede ir:
- Dentro de un archivo de componente. Si el uso es exclusivo de ese componente.
- En un archivo dentro de "constants": Si esa variable puede ser usada por mas de un componente.


