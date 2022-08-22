

[[_TOC_]]
#Flujo de trabajo en paralelo gitflow

https://miro.com/welcomeonboard/V2RDWHV1dmd2ZUZtajh0QU9vYkxFSFFMTWVuemlKZDFsOUNiaEo2eUlFWU9qdmJMTzZGSU5PTkJxSkhlb0xRYXwzMDc0NDU3MzU2MDE1MDU3NDA1?invite_link_id=303839999903

![](../../../images/git_flow.jpg)

#Integración de nueva features
##Branches

Se trabajará con 3 ramas principales para el desarrollo de las nuevas features.

**main** Se almacenarán las versiones estables del proyecto
**release** Se almacenará las versiones previa al estable, siendo lo más semegante al contenido de producción.
**develop** Se almacenará las features que estén desarrollándose durante cada sprint.

### Nuevas Features (branches)
El desarrollo de cada nueva feature deberá ser versionada en un branch del proyecto, la cual deberá llevar dentro del título el número de historia de usuario a la cual hacer referencia.
Ejem.

`US-3217-integracion-con-el-servicio-de-afiliado`

En caso de que la feature necesita de más de un branch de trabajo, estas deberá cumplir las mismas características. Pero sólo el branch principal formará parte del brach de desarrollado.

## Nuevas Features (commits)
Cada uno de los commits usados para poder desarrollar una nueva característica debe tener las siguiente estructura.
Ejemplo

`[US-0000][commit-type] committing something`

`[US-0000]` El identificador de la historia de usuario.
`[commit-type]` El tipo de cambio realizado, puede ser feat, refactor, fix.
`comminting somthing` La descripción del commit

Importante!! **Los commits deben ser en inglés**

##Aprobaciones
### Revisión de pares

Revisión de pares
Cada desarrollador debe revisar el código desarrollado por su par en busca de código sospechoso (en caso no se tenga un par lo debe realizar el líder técnico); contemplar los siguientes escenarios:

No se encuentra código sospechoso: El desarrollador aprueba el pull request con el siguiente mensaje: **_"Se concluyó con la revisión del código en la búsqueda de alguna implementación que estuviera fuera de las funcionalidades definidas en las historias de usuario y que podría ser aprovechada con otros fines. No encontrándose ninguna irregularidad."_**
Se encuentra código sospechoso: avisar al líder técnico para que inicie la revisión. En caso se encuentre código mal intencionado el líder técnico debe avisar a los equipos de seguridad y riesgos.

[Procedimiento de desarrollo ágil V1.2](/Magna/Development-Guidelines/Procedimiento-de-desarrollo-ágil-V1.3.0)

### Revisión de líder técnico

Cada Lider Técnico debe revisar el código basandose en el chekList.
Comentario: 

**_Capa front_**
Cobertura Sonar. No aplica.
Incluye url’s absolutas. No aplica
Nuevas librerías provenientes de un repositorio confiable. No aplica
Scripts no autorizados. No aplica.
Variables de entorno no permitidas. No aplica
Inyección de código dinámico. No aplica
Hay código JavaScript dentro de index.html. No aplica
No sintaxis eval. No aplica
**_React_**
dangerouslySetInnerHTML sanitizado. No aplica
Url’s peligrosas validadas. No aplica
### Revisión de líder de chapter
El chapter lead frontend, se encargará de revisar el código y de cada Pull Request tenga el comentario de pares y del Líder Técnico para poder aprobar y mergear el PR.
