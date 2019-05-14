# EBS

## ¿Qué es EBS?

Amazon Elastic Block Storage (`EBS`) provee almacenamiento de volumenes por bloques para ser usado con instancias de Amazon EC2 en la nube de AWS.

Cada volumnes de EBS es replicada autimáticamente dentro de su zona de disponibilidad para protegerse de una falla de componentes, ofreciendo alta disponibilidad y durabilidad.

## Tipos de almacenamiento EBS

* De proposito general(SSD). 
* Provisioned IOPS(SSD).
* HDD de rendimiento optimizado (Throughput Optimised HDD).
* Cold HDD
* Magnético

### Caso de uso.

#### SSD
* Proposito General: Mayoria carga de trabajo
* Provisioned IOPS: Bases de datos

#### HDD
* Throughput Optimised: Big Data & Data Warehouses
* Cold HDD: File Servers
* EBS Magnetics: Cargas de trabajo donde los datos que no son accesados frecuentemente

### API Names

* De proposito general(SSD) -> `gp2`
* Provisioned IOPS(SSD) -> `io1`
* HDD de rendimiento optimizado (Throughput Optimised HDD) -> `st1`
* Cold HDD -> `sc1`
* Magnético ->  `Standard`