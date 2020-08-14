# CloudFront

## ¿Qué es CloudFront?

Es un servicio **CDN** (`Content Delivery Network`), una red de distribución de contenido que consta de servidores distribuidos globalmente que sirven contenido estático (imágenes, páginas web) a usuarios basados en su ubicación geográfica, origen del sitio web y el servidor del contenido.

`CloudFront` puede ser usado para servir un sitio web entero, incluyendo contenido dinámico, estático, streaming e interactivo usando una red global de `Edge Locations`.

Las peticiones por el contenido son automáticamente enrutadas hacia la `Edge Location` más cercana, así el contenido es servido con el mejor `performance` posible.

## Terminología

- **Edge Location**: Esta es la ubicación donde se encuenta el contenido cacheado, esta separado de una región AWS o Zona de disponibilidad.
- **Origin**: Este es el origen de los archivos que el servicio CDN va a distribuir, esto puede ser un bucket de S3, una instancia de EC2, un Balanceador de carga de Elastic o Route53.
- **Distribution**: Este es el nombre dado al CDN que consiste en un conjunto de `Edge Location`

## Tipos de Distribución

- **Web Distribution**: Típicamente usado para sitios web.
- **RTPM**: Usado para streaming de contendido. (Descontinuado a partir del 31/12/2020)

## Carácteristicas

- Los `Edge Locations` no son de solo lectura, puede escribirse contenido allí.
- Los objetos cacheados por el tiempo de vida configurado (TTL).
- Se puede eliminar contenido cacheado pero tiene un costo extra.

## Cloudfront signed url and cookies

Cuando se crean signed urls o signed cookies, se adjunta una politica y esta puede incluir: expiración del URL, rangos de IP, `Trusted signers` (cuentas de AWS que puedan crear **Signed URLs**)

- Usa signed URL/Cookies cuando necesites asegurar contenido que solo personas autorizadas esten habilitadas para acceder.
- Si el origen es `EC2` puedes usar Cloudfront.

### ¿Cuando usar **Signed URLs** o **Signed Cookies**?

- Las **Signed URL** se usan para identificar archivos individuales. Ejemplo: 1 archivo = 1URL
- Las **Signed Cookies** se usan para multiples archivos. Ejemplo 1 cookie = Multiples archivos

#### Caracteristicas de Cloudfront Signed URL

- Pueden tener diferentes origenes, (No necesita ser un `EC2`).
- Puede utulizar funcionalidades de caching
- La generación de la par de llaves, abarca toda la cuenta manejada por el usuario root de AWS.
- Puede filtra por fecha, path, IP, direccion, expiración, etc.

#### Diferencias de S3 Signed URL

- No se usa cloudfront para acceder al recurso
- Crea una petición como el usuario IAM que creó la signed URL
- Tienen una vida limitada
