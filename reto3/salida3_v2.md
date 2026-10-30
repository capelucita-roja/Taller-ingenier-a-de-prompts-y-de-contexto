| Caso | Entrada | Resultado esperado | Criterio que cubre |
| :--- | :--- | :--- | :--- |
| 1 | Saldo: $15.000; Día: Lunes; Hora: 10:00; Productos: 3 (activos); Precio total: $8.000 | Se crea el pedido y saldo queda en $7.000 | 1 |
| 2 | Saldo: $10.000; Día: Martes; Hora: 14:00; Productos: 5 (activos); Precio total: $12.000 | Rechazo del pedido, saldo permanece en $10.000 | 2 |
| 3 | Saldo: $20.000; Día: Miércoles; Hora: 16:00; Productos: 4 (activos) + 1 (agotado); Precio total: $15.000 | Se crea el pedido con los 4 activos, saldo queda en $5.000 | 3 |
| 4 | Saldo: $5.000; Día: Sábado; Hora: 17:59; Productos: 2 (activos); Precio total: $3.000 | Se crea el pedido y saldo queda en $2.000 | 1 |
| 5 | Saldo: $5.000; Día: Domingo; Hora: 12:00; Productos: 2 (activos); Precio total: $3.000 | Rechazo del pedido por estar fuera de servicio | 4 |
| 6 | Saldo: $5.000; Día: Lunes; Hora: 18:00; Productos: 2 (activos); Precio total: $3.000 | Rechazo del pedido, ya no se acepta a las 18:00 | 4 |
| 7 | Saldo: $5.000; Día: Lunes; Hora: 06:59; Productos: 2 (activos); Precio total: $3.000 | Rechazo del pedido, fuera de horario | 4 |
| 8 | Saldo: $10.000; Día: Jueves; Hora: 11:00; Productos: 6 (activos); Precio total: $5.000 | Rechazo del pedido por exceder el máximo de 5 productos | 2 |
| 9 | Saldo: $0.00; Día: Viernes; Hora: 15:00; Productos: 1 (activo); Precio total: $0.00 | Se crea el pedido y saldo queda en $0.00 | 3 |
| 10 | Saldo: $10.000; Día: Lunes; Hora: 12:00; Productos: 5 (activos); Precio total: $10.000; Tiempo de espera: 30 min exactos | Cancelación del pedido y devolución del saldo original ($10.000) | 5 |

