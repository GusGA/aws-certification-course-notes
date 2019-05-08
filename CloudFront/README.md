# CloudFront

## ¿Qué es CloudFront?

Es un servicio **CDN** (`Content Delivery Network`), una red de distribución de contenido que consta de servidores distribuidos globalmente que sirven contenido estático (imágenes, páginas web) a usuarios basados en su ubicación geográfica, origen del sitio web y el servidor del contenido.

`CloudFront` puede ser usado para servir un sitio web entero, incluyendo contenido dinámico, estático, streaming e interactivo usando una red global de `Edge Locations`.

Las peticiones por el contenido son automáticamente enrutadas hacia lo `Edge Location` más cercana, así el contenido es servido con el mejor `performance` posible.

## Terminología

* **Edge Location**: Esta es la ubicación donde se encuenta el contenido cacheado, esta separado de una región AWS o Zona de disponibilidad.
* **Origin**: Este es el origen de los archivos que el servicio CDN va a distribuir, esto puede ser un bucket de S3, una instancia de EC2, un Balanceador de carga de Elastic o Route53.
* **Distribution**: Este es el nombre dado al CDN que consiste en un conjunto de `Edge Location`

## Tipos de Distribución

*  Distribución Web: Típicamente usado para sitios web.
* RTPM: Usado para streaming de contendido.

## Carácteristicas

* Los `Edge Locations` no son de solo lectura, puede escribirse contenido allí.
* Los objetos cacheados por el tiempo de vida configurado (TTL).
* Se puede eliminar contenido cacheado pero tiene un costo extra.