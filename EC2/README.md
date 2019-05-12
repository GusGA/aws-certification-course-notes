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

