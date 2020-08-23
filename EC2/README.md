# EC2

## ¿Qué es EC2?

Es un servicio que provee capacidad de computo redimensionable en la nube.
Amazon EC2 reduce los tiempos en obtener y bootear nuevas instancia de servidores a minutos, permitiendo una rápida capacidad de escalamiento, tanto para arriba y para abajo como lo requiera la necesidad del computo.

## Modelos de Cobro

### On Demand

Permite pagar un monto fijo por hora o por segundo, sin ningún tipo de compromiso.

#### Util para:

- Usuarios que quieran bajo costo y flexibilidad de amazon ec2 sin pago por adelantado o largos contratos.
- Aplicaciones de corta duración, que tengas saltos o cargas de trabajo impredecibles que no puedan ser interrumpidos.
- aplicaciones que sean desarrolladas o probadas en Amazon EC2 por primera vez.

### Reserved Pricing

Provee una capacidad de reserva y un descuento por la carga en las horas de una instancia, contratos de 1 a 3 años.

#### Util para:

- Aplicaciones que tengan un estado estable o uso predecible.
- Aplicaciones que requiren capacidad reservada
- Usarios que puedan hacer pagos por adelantado para reducir el total de sus costos de computo aún más.

#### Tipos de cobro por reserva

- **Standard reserved instances**: Ofrecen hasta 75% de descuento en instancias `on demand`, Mientras mayor sea el pago adelantado y el contrato por más tiempo, mayor el descuento.
- **Convertible reserved instances**: Ofrece hasta 54% de descuento en capacidad `on demand` para cambiar los atributos de la instancia reservada siempre que el intercambio resulte en una instancia reservada de igual o mayor valor.
- **Schedule reserved instances**: Instancias habilitadas para ser iniciadas dentro de una ventana de tiempo definida. Esta opción permite que coincida la capacidad reservada con un cronograma recurrente y predecible que solo requiera la fracción de un día, una semana o un mes.

### Spot

Le permite pujar, independientemente del precio que desee por la capacidad de la instancia, proporcionando un ahorro cada vez mayor si la aplicación tiene tiempos de inicio y finalización flexibles.

Si es finalizada la instancia por AWS EC2 no tendrá ningún costo el uso parcial por hora. En cambio si la instancia es finalizada por el usuario tendrá un cobro por cualquier hora en la cual la instancia haya corrido.

#### Util para:

- Aplicaciones que tienen tiempos de inicio y fin flexibles.
- Aplicaciones que solo son factibles a precios de computo muy bajos.
- Usuarios con necesidades urgentes de computo para grandes montos de capacidad adicional

### Dadicated Host

Servidores EC2 dedicados, estos pueden ayudar a reducir costos permitiendo utilizar licencias de software existente enlazada al servidor.

#### Util para:

- Utíl para requerimientos regulatorios que no soporten virtualización multi-tenant.
- Excelentes para licenciamientos, donde no haya soportye multi-tenant o despliegues en la nube.
- Puede ser adquirido `on-demand`
- Puede ser adquirido via reserva con hasta 70% de descuento en el precio `on-demand`.

## Carácteristicas de EC2

- Por defecto la proteción de eliminación de las instancias esta en `off`, debe ser ajustada a `on`.
- En una Instancia de EBS, la acción por defecto es para el volumen root EBS es ser eliminado cuando la instancia es finalizada, se puede cambiar esta acción y terminar la instancia sin eliminar el volumen root.
- Los volúmenes root EBS del AMI por defecto pueden ser cifrada, tambien se puede hacer via aplicaciones de terceros para cifrar el volumen o crear un AMI desde la consola o vía API.
- Volumenes adicionales pueden ser cifrados.

## Grupos de seguridad en EC2

- Los cambios efectuados en los grupos de seguridad tienen efectos inmediatos en las instancias involucradas.
- Todo el tráfico de entrada por defecto esta bloqueado.
- Todo el tráfico de salida esta permitido.
- Puede tener cualquier numero de instancias de EC2 bajo el mismo grupo de seguridad.
- Puede tener multiples grupos de seguridad bajo la misma instancia de EC2.
- Los grupos de seguridad son **STATEFUL**.
- Si crea una regla de tráfico de entrada, automaticamente esta permitido el tráfico de salida por el mismo puerto.
- **NO** se puede bloquear una IP específica usando grupos de seguridad, a cambio se usan las Lista de control de acceso de red (`Network Access Control List`).
- Puedes espeficiar reglas que permitan acceso pero no para negarlo.

## Spot Instances & Spot Fleets

**Amazon EC2 Spot Instances** permite aprovechar capacidad de EC2 sin uso en la nubes de AWS. los Spot Instances estan disponibles con descuento de hasta 90% comparado con los precios `on-demand`.

Se pueden usar **Spot Instances** para aplicaciones **sin estado** o que **no necesiten persistencia**, tolerante a fallas y flexibles como big-data, cargas de trabajo contenerizada, CI/CD, web servers, computación de alto desempeño y cargas de trabajo de desarrollo y pruebas

Puedes bloquear instancias de ser eliminen usando **Spot Block**.

Y **Spot Fleet** es una colección de **Spot Instances** y adicionamente pero opcional instancias `On-Demand`.

## Hibernación en EC2

Con **EC2 Hibernate**, las instancias cargan mucho más rápido, el sistema operativo no necesita ser reiniciado debido a que el estado (RAM) es preservado y guardado en el `root device`. Y es util para Procesos largos y servicios que toman mucho tiempo en iniciar.

### Resumen

- **EC2 Hibernate** preserva el contenido de la RAM en almacenamiento persistente (**EBS**)
- Mucho más rapido su inicio ya que no requiere que el sistema operativo sea reiniciado.
- El tamaño de la RAM debe ser menor a 150 GB
- Esta incluido en la familia de las instancia C3, C4, C5, M3, M4, M5, R3, R4, y R5
- Disponible para Windows, Amazon Linux 2 AMI y Ubuntu
- Las instancias no pueden estar hibernando por mas de 60 dias

## AWS Cli

### Caracteristicas

- Se puede interactuar con AWS desde cualquier parte del mundo usando el CLI
- Hay que habilitar los accesos vía IAM

## Instance Metadata

- Se usa para obtener información de la instancia
- Se obtiene la metadata accediendo via `cURL` a `http://169.254.169.254/latest/meta-data/`
- Se obtiene el user-data accediendo via `cURL` a `http://169.254.169.254/latest/user-data/`

## Amazon Elastic File System (Amazon EFS)

Amazon Elastic File System (Amazon EFS) es un servicio de almacenamiento de archivos para las instancias de Amazon Elasctic Compute (`AWS EC2`). Amazon EFS es sencillo de usar y provee una interfaz simple que permite crear y configurar sistema de archivos rápida y facilmente.

Con Amazon EFS, la capacidad de almacenamiento es elastica, crece y se encoge automaticamente a menidad que se agregan y se remueven archivos, por ende las aplicaciones tienen el almacenamiento que necesitan cuando lo necesitan.

- Suporta el protocolo **Network File System** (`Version 4`).
- Solo se paga por el almacenamiento usado (no se require pre-aprovisionamiento).
- Se puede escalar hasta petabytes.
- Los datos son almacenados a traves de multiples zonas de disponibilidad dentro de una región.
- Consistencia "Lectura después de escritura" (`Read after Write`).

## Amazon FSx for Lustre

`Amazon FSx for Lustre` es un sistema de archivos complemente gestionado que esta optimizado para cargas de trabajo de compunto intensivo, tales como computación de alto desemepeño, machine learning, flujos de procesamiento de `media data` y diseño de autimatización electronica (EDA).

## Amazon FSx para Windows File Server

### Diferencias entre Windows FSx, Lustre FSx y EFS

#### Windows FSx

- Un servidor de Windows gestionado que corre un servicio de archivos basado en `Windows Server Message Block (SMB)`
- Deseñado para Windows y aplicaciones de Windows
- Soporta usuarios, listad de control de acceso y politicas de seguridad de Active Directory along with nombre de espacio (`namespaces`) y replicación DFS `Distributed File System`

#### Lustre FSx

- DDiseñado especificamente para el procesamiento rápido de cargas de trabajo como machine learning, computación de alto desempeño, procesamiento de video y modelamiento finaciero entre otros.
- Permite desplegar y correr un sistema de archivos que provee acceso por de bajo de los milisegundos a los datos y permite escribir y leer los datos hasta velocidades de cientos de gigabytes por segundo de desempeño y millones de IOPS.

#### EFS

- Un archivador NAS administrado para instancias EC2 basado en Network File System (**NFS**) v4
- Uno de los primeros protocolos nativos de Unix y Linux para compartir archivos a traves de la red.

### Escenarios para EFS, Lustre FSx y Windows FSx

#### EFS

Cuando se necesite almacenamiento distribuido y altamente resilente para instancia de linux o aplicaciones basadas en linux.

#### Windows FSx

Cuando se necesite centralizar el almacenamieto de aplicaciones basadas en windows, tales como Sharepoint, Microsoft SQL Server, Workspaces, ISS Web Server o cualquier otra aplicación nativa de Microsoft.

#### Lustre FSx

Cuando se necesite almacenamiento distribuido de alta velocidad y capacidad. Esto sería para aplicaciones que necesitan computo de alto desempeño, modelamiento financiero etc. `FSx for Lustre` puede almacenar datos directamente en **S3**

## EC2 Placement Groups

- Un `clustered placement group` no pueden abarcar multiples zonas de disponibilidad (`AZ`)
- `Spread` y `Partitioned` si pueden abarcar multiples `AZ`
- El nombre que se especifique para un `placement group` debe ser unico dentro de la cuenta de `AWS`
- Solo ciertos tipos de instancias puede ser desplegadas en un `placement group` (Compute Optimized, GPU, Memory Optimized, Storage Optimized).
- AWS recomienda instancias homogeneas dentro de un `clustered placement group`.
- No se pueden unir `plpacement groups`
- Se puede mover una instancia existente dentro de un `placement group`. Antes de mover la instancia, esta debe estar en estado detenido. Se pueden remover instancias usando el CLI o el AWS SDK, no se puede hacer con web console todavía.

#### Clustered Placement Group

Grupos de instancias dentro de una misma zona de disponibilidad.

##### Escenario

- Baja latencia de red y alto rendimiento de red

#### Spread Placement Group

Grupo de instancias separadas bajo distinto hardware (distintos racks)

##### Escenario

- Instancias Criticas de EC2

#### Partitioned Placement

Multiples instancias instancias divididas en grupos colocadas en hardware separado.

##### Escenario

- Multiples Instancias de EC2 HDFS, HBase y Cassandra.

## HPC - High Performnace Compute

Se puede alcanzar HPC en AWS a traves de:

- Data transfer:
  - [Snowball o Snowmobile](../S3#snowball)
  - [AWS DataSync](../S3#aws-data-sync) para lamacenar en S3, EFS, FSx para Windows.
  - Direct Connect.
- Compute and Networking:
  - Instancias de EC2 con optimización de GPU o CPU.
  - [**EC2 Fleets**](#spot-instances--spot-fleets).
  - [Placement groups](#ec2-placement-groups).
  - [Enhanced Networkong Single Root I/O virtualization (**SR-IOV**)](/Networking#en).
  - [Elastic Network Adapters o **Inter 85229 Virtual Functions**](/Networking#en).
  - [Elastic Fabric Adapters](/Networking#elastic-fabric-adapter)
- Storage:
  - Instace attached storage:
    - [**EBS**](/EBS#ebs): Escala hasta 64000 IOPS
    - [**Instance Storage**](/EBS#ebs-vs-instance-store-volumes): Escala hasta millones de IOPS, baja latencia
  - Network Storage:
    - [Amazon S3](../S3)
    - [Amazon EFS](#amazon-elastic-file-system-amazon-efs)
    - [Amazon FSx for Lustre](#lustre-fsx-1).
- Orchestration y Automation
  - AWS Batch
  - AWS ParallelCluster
