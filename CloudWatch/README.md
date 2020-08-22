# CloudWatch

## ¿Qué es CloudWatch?

Es un servicio de monitoreo del rendimiento de recursos y aplicaciones en AWS.

## ¿Qué monitoréa?

- Compute

  - Instancias de EC2.
  - Grupos de autoescalamiento.
  - Balanceadores de carga elástica.
  - Chequeo de salud de Route53

- Almacenamiento y Content Delivery
  - Volumenes EBS
  - Storage Gateways
  - CloudFront

## CloudWatch y EC2

### Métricas a nivel de Host

- CPU
- Network
- Disk
- Status Check

### AWS CloudTrail

Es un servicio que aumenta la visibilidad de la actividad del Usuario y recursos grabando las acciones y los llamados al API desde el `AWS Management Console`.

Puedes identificar cuales usuarios y cuentas llamaron AWS, la IP de origen desde donde se hicieron los llamados y cuando se hicieron.

### Diferencias entre CloudWatch y ClouedTrail

- CloudWatch monitorea rendimiento.
- CloudTrail monitorea llamadas al API en la plataforma de AWS.

### Carácteristicas de CloudWatch

- CloudWatch es usado para el monitore del desempeño
- CloudWatch monitoreo standard 5 minutos
- CloudWatch monitoreo detallado 1 mninuto
- CloudWatch monitorea eventos en instancias de EC2 cada 5 minutos por defecto, pero puede ser configurado para que sea de un minuto.
- Se pueden crear alarmas de CloudWatch que disparen notificaciones.
- Se puede crear dashboards para visualizar lo que ocurre en el ambiente de AWS.
- Se puede crear alarmas que notifique cuando se supere algún umbral en particular.
- Se puede crear eventos (**CloudWatch Events**) que responden a cambios de estados en recursos de AWS.
- Se puede crear logs (**CloudWatch Logs**) que pueden conglomerar, monitorear y almacenar logs.
