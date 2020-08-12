# IAM

## ¿Qué es IAM?

**IAM** (`Identity Access Management`) es una funcionalidad que permite la gestión de usuarios y sus niveles de acceso de la cónsola de AWS.

### Caractéristicas claves de IAM

- Centraliza el control de la cuenta de AWS.
- Acceso compartido a las cuentas de AWS.
- Permisos granulares.
- Federación de indentidad (Linkedin, Facebook, Active Directory, etc).
- Autenticación Multifactor.
- Provee acceso temporal para usuarios y dispositivos a servicios donde sea necesario.
- Permite crear una política de rotación de contraseñas.
- Soporta el cumplimiento PCI DSS. (Ejemplo debes cumplir con este marco si manejas tarjetas de crédito)
- Es universal y no aplica solo a una región de AWS.

### Terminología para IAM

- **Users**: Usuarios finales como personas, empleados de una organización.
- **Groups**: Una colección de usuarios, donde cada usuario de un grupo hereda los permisos del miso.
- **Role**: Se puede crear roles y asignarselos a los recursos de AWS.
- **Políticas**: Las políticas estan hechas de documentos llamados documentos de política (`policy documents`). Estos documentos estan hechos bajo el formato `JSON` y dan permiso a lo que puede hacer un Usuario/Grupo/Role.

### Root Account

Es la cuenta creada en la cinfiguración incial de la cuenta AWS y tiene completo acceso `admin`.

### Acceso WEB

- Tiene acceso a la consola de AWS

### Acceso Programático

- Tiene acceso via SDK y CLI

### Otras carácteristicas

- Los usuarios recien creados no tienen permisos.
- No se pueden usar las llaves de acceso y secreta para hacer login en la consola de AWS, solo se puede acceder vía API y CLI.
- Las llaves solo pueden ser vistas una vez, si son perdidas deben ser regenaradas de nuevo.
- Es universal, hasta la fecha no aplica solo a regiones.
- El Access Key ID y el secret access key no puede sen usadas para acceder a la consola de aws, no funcionan como el password.
