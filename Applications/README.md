# Applications

## AWS WAF

AWS WAF es un aplicación web cortafuegos que permite monitorear las peticiones `HTTP` y `HTTPS` que sean redirigidas a Amazon CloudFront, un balanceador de carga o un API gateway.

Al más básico nivel de AWS WAF permite 3 compotamientos distintos:

- Permitir todas las peticiones excepto las que se especifiquen.
- Bloquear todas las peticiones exceptos las que se especifiquen.
- Contar las peticiones que hagan match a las propiedades especificadas.

Protección extra en contras de ataques web usando conficiones especificas. Se pueden definir condiciones usando caracteristicas de las peticiones web tales como:

- Direccion IP de la petición de origen.
- País de la petición de origen.
- Valores en las cabeceras de la petición.
- Cadenas de texto que aparecen en las peticiones, cualquier cadena de texto que haga match contra una expresión regular.
- Largo de la petición
- Presencia de código SQL que podría ser malicioso (SQL Injection)
- Presencia de scripts que podría ser malicioso (CrossSite Scripting)

### Escenarios para AWS WAF

- Bloquear dirección IP "maliciosas"
- Bloquear peticiones de países sancionados por gobiernos.
