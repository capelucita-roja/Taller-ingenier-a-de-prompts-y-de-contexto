1. Dado que el usuario repite su último pedido, Cuando se realiza la acción de repetición, Entonces se cargan automáticamente los productos del pedido anterior.
2. Dado que el usuario intenta repetir un pedido, Cuando se detecten productos agotados en el historial, Entonces se excluyen esos productos y se muestra una alerta de disponibilidad.
3. Dado que el usuario repite su último pedido, Cuando se sumen los productos repetidos al saldo actual, Entonces se verifica que el saldo nunca quede negativo antes de confirmar.
4. Dado que el usuario repite un pedido con más de 5 productos, Cuando se intenten añadir artículos adicionales, Entonces se bloquea la acción y se indica el límite máximo permitido.
5. Dado que el usuario repite su último pedido, Cuando se solicite la repetición fuera del horario de 7:00 a 18:00 o en días festivos, Entonces se deniega la operación indicando que no es posible realizar pedidos.

