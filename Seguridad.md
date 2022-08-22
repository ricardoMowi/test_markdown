[[_TOC_]]

#Hacer uso de librerías y frameworks
Se deben seleccionar librerías y framework de fuentes confiables, con desarrollo y mantención activa, y que tenga una amplia comunidad (y por ende, validadas). 
Es importante inventariar y catalogar dichas librerías y frameworks para mantenerlas actualizadas y prevenir vulnerabilidades en ellas. Todas las librerías internas y externas a utilizar deben estar subidas en el Artifactory.

#Validación de datos
Ésta es una técnica para asegurar que sólo los datos con el formato correcto podrán ingresar al sistema a desarrollar. Esta validación debe ser correcta, tanto sintáctica como semánticamente. Por ejemplo, si esperamos que en un campo se puedan ingresar sólo dígitos, no debemos aceptar otro tipo de caracteres (validación sintáctica). La validación semántica es un poco más compleja y consiste en validar que los datos tengan sentido en el contexto de la aplicación, por ejemplo, una fecha de inicio no podría estar después de una fecha de fin.
La validación de datos, al igual que la codificación y escape, deben ser siempre realizados en el servidor y nunca del lado del cliente (por ejemplo, no se debe realizar en el navegador del usuario). No se debe confundir un aviso al usuario (por ejemplo, para alertar de un campo mal ingresado) con la validación de datos.
La validación de datos no convierte automáticamente a los datos en seguros, por lo que se debe utilizar en conjunto con otras defensas, tales como la parametrización de consultas y escapado de datos, mencionados anteriormente.

#Datos sensibles
Se debe evitar, cuando sea posible, el almacenamiento de datos sensibles por parte de la aplicación. En caso que no se pueda evitar almacenar datos sensibles, éstos deben ser protegidos mediante encriptación, para prevenir la modificación o acceso no autorizado. 
