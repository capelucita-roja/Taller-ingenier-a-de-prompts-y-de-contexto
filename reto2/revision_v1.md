VEREDICTO: RECHAZADO
HALLAZGOS:
1. Regla 2 (maximo 5 productos) -> el codigo verifica >6 en lugar de >=5 y permite hasta 6 items -> verificar len(productos) > 5
2. Regla 3 (saldo negativo) -> la logica invierte la resta y permite saldos negativos si exceden -1000 -> verificar est.saldo < sum(p.precio for p in productos)
3. Regla 4 (productos agotados) -> falta validacion para asegurar que producto.disponible sea True -> agregar verificacion de disponibilidad en el bucle
4. Regla 5 (cancelacion por tiempo) -> la funcion no verifica si el pedido se recoge en 30 minutos -> agregar logica temporal o estado de recogida
RESUMEN: El codigo falla en validar el maximo de 5 items, permite saldos negativos, ignora la disponibilidad y omite la regla de los 30 minutos.

