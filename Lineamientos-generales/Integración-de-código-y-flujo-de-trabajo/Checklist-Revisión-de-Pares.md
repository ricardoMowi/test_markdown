Para la revisión de pares es importante considerar que cada integración de código cumpla con la siguiente lista propuesta.

## Capa Front

- No se debe incluir url's absolutas que no correspondan al dominio de Prima. Algunas de las url's permitidas por las responsabilidad que desempeñan son:
  - https://policies.google.com/
  - https://www.w3.org/2000/svg
- Las nuevas librerías a usar deben provenir de un repositorio confiable y que no estén apuntando a dominios o repositorios provenientes a usuarios desconocidos.
  - **Es importante validar esta nueva integración con el Chapter Lead**.
  - La dependencia debe tener más de 10k de instalación en npm.
  - El repositorio debe ser mantenido continuamente, es decir que debe tener integrados pull requests en el último año.
- No se deben insertar scripts no autorizados. Se debe verificar que el archivo index.html no contenga script que no se encuentren en el listado de más abajo, salvo que el Product Owner haya especificado la incorporación de nuevos módulos y este haya sido validado con el Chapter Lead. Algunos script permitidos:
**Scripts Permitidos**
  - Google Tag manager
  - Google Analytics
- Las variables de entorno deben ser las permitidas dentro de los únicos archivos de ambiente.
  - env.dev
  - env.qa
  - env.prod
- Verificar que no se inyecte código de manera dinámica.
  - Esto puede ocasionar carga de archivos o consumo de api's desconocidas.
  - En caso sea requerido debe ser validado por el Chapter Lead.
```js
document.createElement(‘script’);
```
- Verificar que no se agregué código javascript dentro del archivo index.html, este debe ser invocado desde un archivo dentro del mismo dominio o proyecto.

```js
// No se debe
// index.html
...
<script>
function miFuncionPrueba() {
...
}
</script>
```
```js
// si se debería hacer
<script src="/js/archivoConMiFuncionPrueba.js" /></script>
```
- Verificar que no se este utilizando la sintaxis _eval_ . [Leer más](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/eval#never_use_eval!)
```js
eval(new String('2 + 2')); // returns a String object containing "2 + 2"
eval('2 + 2');             // returns 4
```



### React

- En el renderizado de html directo mediante _dangerouslySetInnerHTML_ se debe de sanitizar el contenido. Se debe user [dompurify](https://www.npmjs.com/package/dompurify) para llevar a acabo esto.
```js
import purify from "dompurify";

<div dangerouslySetInnerHTML={{ __html:purify.sanitize(data) }} />
```
- Acceso directo al DOM. Se debe realizar de la manera especificada anteriormente.

```js
// Do this
import purify from "dompurify";
<div dangerouslySetInnerHTML={{__html:purify.sanitize(data) }} />

// Don't do this
this.myRef.current.innerHTML = attackerControlledValue;

```
- Url's peligrosas. Se debe validar que lo que se va a renderizar en el href es una url y no un código de ejecución **_javascript:_** para eso se debe validar la inclusión del _https_ o _http_

```js
// Do this
function validateURL(url) {
  const parsed = new URL(url)
  return ['https:', 'http:'].includes(parsed.protocol)
}

<a href={validateURL(url) ? url : ''}>Click here!</a>
```

```js
// Don't do this
<a href={attackerControlled}>Click here!</a>
```

