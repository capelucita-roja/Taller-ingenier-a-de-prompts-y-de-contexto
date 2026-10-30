1. Dado que el estudiante tiene saldo $5.000 y su pedido anterior cuesta $4.000,
   Cuando presiona "Repetir pedido" un martes a las 10:00,
   Entonces el sistema crea el nuevo pedido y el saldo queda en $1.000.

2. Dado que el estudiante tiene saldo $5.000 y su pedido anterior cuesta $4.000,
   Cuando presiona "Repetir pedido" un domingo a las 10:00,
   Entonces el sistema muestra un mensaje indicando que no se aceptan pedidos en domingos.

3. Dado que el estudiante tiene saldo $5.000 y su pedido anterior cuesta $4.000,
   Cuando presiona "Repetir pedido" a las 18:00 exactas de cualquier día,
   Entonces el sistema muestra un mensaje indicando que no se aceptan pedidos a partir de esa hora.

4. Dado que el estudiante tiene saldo $5.000 y su pedido anterior cuesta $4.000,
   Cuando presiona "Repetir pedido" un martes a las 10:00 sin especificar cantidad,
   Entonces el sistema crea el pedido con la misma cantidad de productos del pedido anterior.

5. Dado que el estudiante tiene saldo $5.000 y su pedido anterior cuesta $4.000,
   Cuando presiona "Repetir pedido" un martes a las 10:30 (más de 30 minutos después),
   Entonces el sistema cancela el pedido y devuelve el saldo completo al usuario.

