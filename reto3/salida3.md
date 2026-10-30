| Caso | Entrada | Resultado esperado | Criterio que cubre |
| :--- | :--- | :--- | :--- |
| 1 | Usuario selecciona "Repetir pedido" tras un pedido válido de lunes a sábado entre las 07:00 y 18:00. | Se cargan automáticamente los productos del pedido anterior al carrito. | 1 |
| 2 | Usuario selecciona "Repetir pedido" que contiene productos agotados. | Se excluyen los productos agotados del carrito, se muestra una alerta de disponibilidad y se permite completar con los restantes. | 2 |
| 3 | Usuario intenta repetir un pedido; la suma de productos repetidos supera su saldo actual (saldo quedaría negativo). | El sistema deniega la confirmación, indica el saldo insuficiente y no realiza la transacción. | 3 |
| 4 | Usuario intenta añadir un producto al carrito para llegar a más de 5 ítems en total. | Se bloquea la acción de añadir, se muestra una alerta indicando el límite máximo de 5 productos. | 4 |
| 5 | Usuario selecciona "Repetir pedido" fuera del horario de servicio (ej. domingo o antes de las 07:00). | Se deniega la operación con un mensaje indicando que no es posible realizar pedidos en ese momento. | 5 |

**Nota sobre la revisión:**
He revisado los 5 criterios proporcionados y he generado exactamente uno caso de prueba por cada criterio. No se han detectado casos faltantes, por lo que no se han agregado ninguno nuevo.

