
## Tipos de kernel
> #### Kernel monolitico: 
> Es el responsable de la gestion de memoria y procesos asi como de la comunicacion o enlace de procesos y permite la integracion con driver y hardware, este es el tipo de kernel que se manifiesta comunmente en los sistemas operativos que hoy en dia se utilizan (OS X, Linux, Windows).
> #### Microkernel:
> Su diseño fue creado intencionalmente de un tamaño pequeño para que en caso de fallo, no se paralice todo el sistema operativo dejandolo inutilizable por el momento.
> Esta dividido por varios modulos para que pueda similar el funcionamiento de un kernel comun, de momento solo esta aplicado en el componente llamado Mach de OS X ya que hasta ahora no hay ningun sistema operativo con microkernel.
> #### Kernel hibrido:
> Nace de la combinacion de los tipos de kernel anteriormente expuestos (Monolitico y microkernel), en este caso el kernel grande se hace mas compacto y modulable mientras las otras partes del kernel se cargan dinamicamente, esto fue aplicado en cierta medida en los sistemas Linux y OS X.
> #### Exonucleos:
> Son aquellos que si bien no cuentan con ningun tipo de abstraccion, son aquellos que permiten el uso de bibliotecas.
> Funcionan adecuadamente proporcionando mucha funcionalidad en muchos aspectos debido a que cuentan con un acceso directo al hardware y gracias a esto, un desarrollador podria ser capaz de permitir todas esas decisiones importantes en cuanto al rendimiento del sistema se refiere.

## Diferencias entre kernels

| KERNEL MONOLITICO | MICROKERNEL | KERNEL HIBRIDO | EXONUCLEO |
|------|------|------|------|
| Es un kernel rapido pero menos seguro. | Es el mas pequeño de todos y es mas seguro que el kernel combencional monolitico. | Es un kernel compacto y dinamico. | Cuenta con una comunicacion directa con el hardware |
| Se encentra en los sistemas operativos mas comunes. | Es un kernel un poco lento. | Dinamicamente cargan modulos despues del arranque. | Posee acceso de bajo nivel para que el programador pueda implementar abstracciones personalizadas y omitir las innecesarias. |

## User vs Kernel Mode

> ### Descripcion general:
> El código en modo kernel tiene acceso ilimitado al hardware, mientras que el código en modo usuario tiene acceso restringido al SCI. Cuando se produce un error en el modo de usuario, no ocurre mucho: de hecho, en ese momento el kernel interviene y repara los posibles daños. Por otro lado, un fallo del kernel puede hacer caer todo el sistema. No obstante, existen precauciones de seguridad para evitarlo.
> ### Modo usuario:
> Se crea un proceso para la aplicación, el proceso proporciona a la aplicación un espacio de direcciones virtuales privado y una tabla de identificadores privados. Dado que el espacio de direcciones virtuales de una aplicación es privado, una aplicación no puede modificar los datos que pertenecen a otra aplicación.
>
> Un proceso que se ejecuta en modo de usuario no puede acceder a direcciones virtuales reservadas para el sistema operativo. Limitar el espacio de direcciones virtuales de una aplicación en modo de usuario impide que la aplicación modifique los datos críticos del sistema operativo, y posiblemente perjudiciales.
> ### Modo Kernel:
> Todo el código que se ejecuta en modo kernel comparte un único espacio de direcciones virtuales. Por lo tanto, un controlador en modo kernel no está aislado de otros controladores y del propio sistema operativo. Si un controlador en modo kernel escribe accidentalmente en la dirección virtual incorrecta, los datos que pertenecen al sistema operativo u otro controlador podrían verse comprometidos.