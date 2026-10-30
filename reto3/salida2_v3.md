1. Dado que el estudiante tiene el carne con saldo $15.000,
   Cuando realiza un pedido válido de lunes a sábado entre las 7:00 y las 18:00,
   Entonces se crea el pedido y se descuenta el saldo correspondiente.

2. Dado que el estudiante intenta pedir productos con saldo $10.000,
   Cuando el costo total supera su saldo disponible en la cuenta,
   Entonces el sistema rechaza el pedido para evitar un saldo negativo.

3. Dado que el estudiante selecciona productos del inventario,
   Cuando intenta añadir un producto que está agotado al carrito,
   Entonces el sistema impide agregar ese producto específico al pedido.

4. Dado que el estudiante realiza un pedido fuera de horario o en domingo,
   Cuando intenta crear un pedido antes de las 7:00 o después de las 18:00,
   Entonces el sistema bloquea la creación del pedido por estar fuera de servicio.

5. Dado que el estudiante tiene un pedido creado hace 29 minutos,
   Cuando pasa exactamente 30 minutos sin recoger su comida,
   Entonces el sistema cancela el pedido y devuelve el saldo original.

