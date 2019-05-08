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
