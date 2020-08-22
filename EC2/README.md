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
