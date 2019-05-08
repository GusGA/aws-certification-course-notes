# S3

## ¿Qué es S3?

S3 (Simple Storage Service) es un servicio de almacenamientos de archivos en internet, basado en Objetos.

## Carácteristicas y funcionalidades de S3

* S3 usa un `namespace` universal y debe ser único de manera global.
* La url tiene formato `https://<aws-region>.amazonaws.com/<global-unique-name>`
* Cuando cargas un archivo a S3, obtienes un status HTTP 200 si la carga fue exitosa.
* Almacenamiento casí infinito.
* Los archivos son almacenados en `buckets` que son una especie de directorios
* Soporta MFA para la eliminación de archivos 
* Consistencia de lectura despues de escritura para `PUTS` de nuevos objetos.
* Consistencia eventual para sobre escritura `PUTS`y eliminación de objetos `DELETE` (Toma tiempo en propagar los cambios). 
* Cifrado.
* Versionamiento.
* Gestión del ciclo de vida.
* Listas de control de acceso y políticas en `Buckets`.

## Garantías de S3 ofrecidas por Amazon

* La plataforma de S3 esta diseñada para entrgar un **99.99%** de disponibilidad.
* Amazon garantiza un **99.9%** de disponibilidad.
* Amazon garantiza un **99.999999999%** (11x9) de duración de la información de S3.

## Tipos de almacenamiento

### S3 Standard

Disponibilidad de **99.99%** y Durabilidad de **99.999999999%**, alamacenados redundantemente en distintos a tráves de distintas instalaciones y diseñado para soportar la caida de 2 instalaciones concurrentemente.

### S3 IA (Infrequently Accessed)

Para datos que son accesados de manera poco frecuente pero require acceso rápido cuando es necesitado.

Los cargos son menores que los de `S3 Standard` pero tiene un cargo extra por acceso a los datos.

### S3 One Zone - IA 

Cuando se desea una opción de bajo costo para datos de acceso poco frecuente  pero no requiere resilencia en multiples zonas de disponibilidad.

### S3 Intelligent Tiering

Diseñado para optimizar costos automatizando el movimiento de los datos al `tier` con mejor relación costo-efectividad sin impactar en el `performance` o el sobreexigimiento operacional.

### S3 Glacier

Es una opción segura, durable y de bajo costo para almacenar datos.

Puedes almacenar con confianza cualquier cantidad de datos a un costo muy competitivo y superando a soluciones `on-premise`.

Los tiempos de recuperación pueden ser configurables entre minutos y horas.

### S3 Glacier Deep Archive

Es la opción más económica para almacenar datos en S3, los tiempos de recuperación son de 12 horas.


## Vías por las cuales S3 genera cobros

* Almacenamiento.
* Peticiones.
* Gestión de almacenamiento.
* Transferencia de datos.
* Aceleración de transferencia.
* Replicación entre regiones.


## Composión de un objeto de S3

- `Key` Nombre del objeto.
- `Value` Datos del objeto, secuencia de bytes.
- `Version Id` Información para el versionamiento.
- `Metadata` Datos sobre los datos que se estan almacenando.
- `Subresources` 
  - Listas de control de acceso.
  - Torrent

## Cifrado 

Por defecto los `buckets` recién creados son privados, además puedes configurar el control de acceso a través de Políticas de Buckets (`Bucket policies`) y de listas de control de acceso (`Access Control List`).

Los buckets de S3 pueden configurarse para crear `logs` de accesos los cuales registran cualquier petición hecha al bucket, esto puede ser enviado a otro bucket inclusive a otro bucket en otra cuenta.

### Cifrado en tránsito.

El cifrado en tránsito se realiza cuando la comunicación entre el cliente y el servidor esta bajo el protocolo `HTTPS`, ya que el mismo cifra el contenido de las peticiones y si estas son interceptadas no pueden descifradas.

### Cifrado del lado del servidor (Encryption at rest)

`Encryption at rest` es el cifrado que se realiza sobre los datos al momento de guardarlos, puede ser realizada desde el cliente o desde el servidor.

Desde el cliente se cifra el objeto y se lo envia a S3.

Desde el servidor, AWS gestiona las llaves de cifrado y puede ser obtenido de las siguientes maneras:
  * S3 Managed Keys - SSE-S3 (`Server Side Encryption S3`) (Gestión de llaves por parte de aws).
  * AWS Key Management Service - SSE-KMS (`Server Side Encryption Key Management Service`) (Gestión compartida en entre el usuario y AWS en el manejo de las llaves).
  * Server Side Encryption With Customer Provided Keys - SSE-C (El usuario le provee a AWS las llaves para el cifrado de los objetos en S3).

### Versionamiento de los objetos de S3

* Almacena todas las versiones de un objeto, incluido todas las escrituras hasta las eliminaciones.
* Gran herramienta de respaldo.
* Una vez activado, el versionamiento no puede ser deshabilitado, solo suspendido.
* Integra reglas para el ciclo de vida.
* El versionamiento incluye la funcionalidad de `MFA DELETE`, donde se usa el multi-factor de autenticación y puede ser provisto como otra capa de seguridad.

### Gestión del ciclo de vida en S3

* Automatiza el movimiento de objetos entre diferentes [`tiers`](#Tipos-de-almacenamiento) de almacenamientos.
* Puede ser usado en combinación con el versionamiento.
* Puede ser aplicados a versiones actuales y previas.

### Replicación entre regiones.

* El versionamiento debe esta activo en ambos `buckets`, tanto en el origen como en el destino.
* Las regiones deben ser únicas.
* Los archivos en un `bucket` existente no son replicados automáticamente.
* Las siguientes cargas de archivos serán replicadas automáticamente.
* Las marcas de eliminación no son replicadas.
* Eliminar versiones individualmente o eliminaciones de las marcas de borrado no serán replicadas.

### Acelaración de transferencia.

La aceleración de transferencia de S3 es un servicio que utiliza la `Cloudfront Edge Network` para acelerar las cargas hacia S3.

En vez de cargar directamente hacia el `bucket` se utiliza una `URL` distinto para cargar el archivo directo a la `Edge Location` más cercana al usuario y posteriormente hacia el `bucket` de S3.

### SnowBall

![snowball](snowball_box.jpeg)
