# Decisiones que el modelo tuvo que adivinar (prompt malo)

1. Lenguaje: eligió JavaScript. yo no le pedi nada; yo nesesite que fuera Python.
2. Estructura: creó una clase GestorPedidos en vez de una función simple.
3. Datos de entrada: se inventó un objeto para los "cliente" e "items" (precio y cantidad).
4. Qué retorna: devuelve el objeto del pedido o no retorna nada si hay error, ni un True/False ni un mensaje.
5. Dónde guarda: usa el  localStorage del navegador "como si fuera una página web", no el saldo del carné.
6. Reglas ignoradas: no valida el horario (lunes a sábado, 7:00-18:00), ni máximo 5 productos, ni saldo, ni productos agotados, ni la cancelación a los 30 minutos.
7. La respuesta se quedó ca la mitad corto su respuesta por error en el codigo  incompleto.