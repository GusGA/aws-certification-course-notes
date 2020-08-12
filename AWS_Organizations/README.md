# AWS Organizations

## ¿Que són las AWS Organizations?

Es una servicio de administración de cuentas que permite consolidar multiples cuentas de AWS bajo una organización que es administrada de manera centralizada.

## Facturación Consolidada

- Permite establecer politicas distintras entre diferentes organizaciones, con recursos bloqueados por cuenta.
- Permite consolidar la facturación mensual.
- Una factura por cuenta de AWS
- Facil seguimiento de cargos y asignación de costos.
- Descuentos por volumen

## Mejores Prácticas en AWS Organizations

- Siempre habilite MFA en la cuenta root
- Use siemrpe contraseñas complejas en la cuenta root
- La cuenta de pagos debe ser solo usado para propositos de facturación. no haga despliegues de recursos con esta cuenta.
- Habilite y deshabilite servicios de AWS usando el `Service Control Policies` (`SPC`) en las organizaciones o cuentas individuales.
