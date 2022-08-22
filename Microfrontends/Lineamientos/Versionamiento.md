## Versionado del Paquete

### Pruebas locales
Dada una versión establecida para la feature a desarrollar, podrás publicar pruebas de tu desarrollo en local con cambios parciales. Aquí iterarás la el útlimo número de la versión.
```js
"version": "0.0.1-dev.1"
...
"version": "0.0.1-dev.2"
```
### Integraciones a develop
Una vez este listo tu feature para integrarse a la rama de develop es que debes cambiar el sufijo a rc. Esto indicará que es el paquete oficial para el uso de desarrollo.
```js
"version": "0.0.1-rc"
```
### Integraciones a release
Una vez tu paquete ya haya pasado por pruebas en certificación, es que es que genera el paquete estable el cual irá a producción y será integrado en la rama main.
```js
"version": "0.0.1"
```