# ALTTA LAB Inventory

## Qué problema resuelve
Permite registrar, organizar y controlar los recursos físicos de un laboratorio tecnológico, así como los costos asociados a su adquisición.

El sistema contempla dos áreas principales: gestión de inventario y gestión de costos, permitiendo conocer las existencias, su estado, el valor del inventario, la inversión realizada y los pagos pendientes.

## Para quién
Laboratorios, estudiantes, desarrolladores y equipos de prototipado que necesitan administrar sus recursos técnicos y llevar un control económico de los mismos.

## Datos que manejará la herramienta
- **ID del recurso — texto:** identificará de manera única cada recurso y permitirá utilizar códigos alfanuméricos.
- **Nombre — texto:** identificará el componente, material, consumible o equipo.
- **Categoría — texto:** permitirá clasificar recursos como electrónica, mecánica, impresión 3D, actuadores, herramientas, equipos o consumibles.
- **Cantidad — entero:** representa el número de unidades disponibles.
- **Estado — valor categórico:** indicará si el recurso está disponible, en uso, agotado o dañado.
- **Costo unitario — entero en centavos:** permitirá manejar dinero de forma exacta sin utilizar coma flotante.
- **Costo total — valor calculado:** se obtendrá a partir de la cantidad y el costo unitario.
- **Estado de pago — valor categórico:** indicará si una adquisición está pagada o pendiente.
- **Monto pagado — entero en centavos:** representa la cantidad que ya fue cubierta.
- **Deuda pendiente — valor calculado:** se obtendrá a partir del costo total y el monto pagado.

## Datos y estructuras
| Dato | Qué guarda | Tipo elegido | Por qué ese y no otro |
|---|---|---|---|
| ID del recurso | Identificador único de cada recurso | Cadena de caracteres | Puede contener letras y números, por ejemplo `ELEC-001`; un entero limitaría el formato del identificador. |
| Nombre | Nombre del componente, material, consumible o equipo | Cadena de caracteres | Su longitud es variable y puede contener espacios, acentos y otros caracteres. |
| Categoría | Clasificación del recurso | Cadena de caracteres | Permite representar categorías descriptivas como electrónica, mecánica o impresión 3D y agregar nuevas categorías posteriormente. |
| Cantidad | Número de unidades disponibles | Entero | Representa unidades completas; una coma flotante permitiría fracciones que no corresponden a este dato. |
| Estado | Situación actual del recurso | Valor categórico | Debe limitarse a estados definidos como Disponible, En uso, Agotado o Dañado para evitar valores inconsistentes. |
| Costo unitario | Precio de adquisición de una unidad | Entero de centavos | Evita los errores de precisión que puede introducir la coma flotante al representar dinero. |
| Estado de pago | Situación del pago de una adquisición | Valor categórico | Solo necesita admitir estados previamente definidos, como Pagado o Pendiente. |
| Monto pagado | Cantidad de dinero ya cubierta | Entero de centavos | Permite realizar operaciones monetarias exactas sin errores de redondeo de coma flotante. |

## Estructuras de datos previstas
- **Estructura estática — arreglo de estados:** almacenará un conjunto definido de estados del inventario, como Disponible, En uso, Agotado y Dañado.
- **Estructura dinámica — lista de recursos:** almacenará los elementos del inventario y podrá crecer o reducirse conforme se agreguen o eliminen recursos.
- **Ordenamiento de recursos:** permitirá organizar los elementos del inventario por criterios como nombre, categoría, cantidad o costo para facilitar su consulta y análisis.
- **Búsqueda de recursos:** permitirá localizar elementos mediante datos como su ID, nombre o categoría.