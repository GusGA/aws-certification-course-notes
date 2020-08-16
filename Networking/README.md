# Networking

## ENI vs. ENA vs. EFA

### ENI

Elastic Network Interface, esencialmente una interfaz de red virtual.

#### Carácteristicas

- Permite tener una dirección primaria privada IPv4 de una rango de direcciones IPv4 del VPC
- Una o mas direcciones scundarias privadas de un rango de direciones IPv4 del VPC
- Una dirección IPv4 elastica (**Elastic IP**) por cada direción privada.
- Una dirección publica IPv4
- Una o mas dirección IPv6
- Uno o mas grupos de seguridad
- Una dirección Mac
- Un check flag de origen/destino
- Una descripción

#### Escenarios para un dispositivo de red

- Crear una red de gestión. (management network)
- Usar aparatos de redes y seguridad en una VPC
- Crear instancias [`dual-homed`](https://en.wikipedia.org/wiki/Dual-homed) con cargas de trabajop y roles en distintas sub redes.
- Crear una solución de alto desempeño de bajo costo.

### EN

Enhanced Networking, Usa **Single Root IO Vitualization** (`SR-IOV`) para proveer capacidades de networking de alto desempeño en instancias que lo soporten. SR-IOV es un metodo de vistualización de dispositivos que proveen I/O de alto desempeño y baja utilización de CPU comparado con los dispositivos virtualizados tradicionales.

Enhanced Networking provee alto ancho de banda, alto desempeño en paquetes por segundo (PPS) y bajas latencias entre instancias consistentemente. No hay cargos adicionales por usar `Enhanced Networking`. Se puede usar cuando se desea un buen desempeño de la red.

Dependiendo del tipo de instancia, `Enhanced Networking` puede ser habilitado usando:

- **ENA** (`Elastic Network Adapter`), el cual soporta velocidades de red de hasta 100 Gbps para instancias que lo soporten
- Interfaz **Intel 82599 Virtual Function** (`VF`), la cual soporta velocidades de red de hasta 10 Gbps para instancias que lo soporten. (Tipicamente usados en viejas instancias).

**NOTA** En cualquier pregunsta de escenario, probablemente seleccionar ENA sobre VF si está entre las opciones.

### Elastic Fabric Adapter

Un dispositivo de red que se puede adjuntar a una inatancia EC2 de Amazon para acelerar el computo de alto desempeño (`High Performance Computer`) y aplicaciones de Machine Learning.

**EFA** provee bajas y mas consistentes latencias y el rendimiento es mayor que Transporte TCP tradicional usado en sistemas en la nube basados en sistemas HPC.

**EFA** puede usar `OS-bypass`. El `OS-bypass` habilita a HPC y a las aplicaciones de machine learning a saltarse el kernel del sistema operativo y comunicarse directamente con el dispositivo **EFA**. Esto hace que sea mucho mas rápido y con mucha menos latencia. (No es soportado por Windows, solo con Linux)

### Escenarios para ENA/EFA/ENI

- **ENI**: Para networking básico, Quizás cuando se necesita separar la gestion de las redes de las aplicaciones o un logging de la red separados y se necesita hacer esto a un bajo costo. Este escenario usa multiple ENI para cada red.

- **Enhanced Network**: Caundo se necesiten velocidades entre 10Gbps y 100 Gbps. Donde se necesite que sea confiable, y de alto rendimiento.

- **Elastic Fabric Adapter**: Cuando se necesite acelerar el computo de alto desempeño (HPC) y aplicaciones de machine learning o si necesita hacer `OS-bypass`. Si hay un escenario mencionando HPC o ML y preguntan cual adaptador de red usar, escoja EFA.
