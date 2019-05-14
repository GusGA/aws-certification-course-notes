# EC2

## ¿Qué es EC2?

Es un servicio que provee capacidad de computo redimensionable en la nube.
Amazon EC2 reduce los tiempos en obtener y bootear nuevas instancia de servidores a minutos, permitiendo una rápida capacidad de escalamiento, tanto para arriba y para abajo como lo requiera la necesidad del computo.

## Modelos de Cobro

### On Demand
Permite pagar un monto fijo por hora o por segundo, sin ningún tipo de compromiso.

### Reserved 
Provee una capacidad de reserva y un descuento por la carga en las horas de una instancia, contratos de 1 a 3 años.

- Tipos de cobro por reserva
  - **Standard reserved instances**: Ofrecen hasta 75% de descuento en instancias `on demand`, Mientras mayor sea el pago adelantado y el contrato por más tiempo, mayor el descuento.
  - **Convertible reserved instances**: Ofrece hasta 54% de descuento en capacidad `on demand` para cambiar los atributos de la instancia reservada siempre que el intercambio resulte en una instancia reservada de igual o mayor valor. 
  - **Schedule reserved instances**: Instancias habilitadas para ser iniciadas dentro de una ventana de tiempo definida. Esta opción permite que coincida la capacidad reservada con un cronograma recurrente y predecible que solo requiera la fracción de un día, una semana o un mes.  

### Spot 
Le permite pujar, independientemente del precio que desee por la capacidad de la instancia, proporcionando un ahorro cada vez mayor si la aplicación tiene tiempos de inicio y finalización flexibles. 

### Dadicated Host
Servidores EC2 dedicados, estos pueden ayudar a reducir costos permitiendo utilizar licencias de software existente enlazada al servidor.

### Carácteristicas

* Por defecto la proteción de terminación de las instancias esta en `off`, debe ser ajustada a `on`.
* En una Instancia de EBS, la acción por defecto es para el volumen root EBS es ser eliminado cuando la instancia es finalizada, se puede cambiar esta acción y terminar la instancia sin eliminar el volumen root.
* Los volúmenes root EBS del AMI por defecto no puede ser cifrada, pero se puede hacer via aplicaciones de terceros para cifrar el volumen o crear un AMI desde la consola o vía API.
* Volumenes adicionales pueden ser cifrados.

### Grupos de seguridad

* Los cambios efectuados en los grupos de seguridad tienen efectos inmediatos en las instancias involucradas.
* Todo el tráfico de entrada por defecto esta bloqueado.
* Todo el tráfico de salida esta permitido.
* Puede tener cualquier numero de instancias de EC2 bajo el mismo grupo de seguridad.
* Puede tener multiples grupos de seguridad bajo la misma instancia de EC2.
* Los grupos de seguridad son `STATEFULL`.
* Si crea una regla de tráfico de entrada, automaticamente esta permitido el tráfico de salida por el mismo puerto.
* `NO` se puede bloquear una IP específica usando grupos de seguridad, a cambio se usan las Lista de control de acceso de red (`Network Access Control List`).
* Puedes espeficiar reglas que permitan acceso pero no para negarlo.