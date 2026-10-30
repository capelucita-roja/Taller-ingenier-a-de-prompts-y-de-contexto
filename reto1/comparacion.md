# Reto 1: comparación

## Qué reglas cumple ahora que antes no cumplía
- Usa Python (antes JavaScript) y una sola función (antes una clase).
- Retorna una tupla (exito, mensaje), como se pidió.
- Valida máximo 5 productos, productos agotados y saldo suficiente (saldo nunca negativo).
- No usa base de datos ni localStorage; respeta que la cancelación a los 30 minutos no va en la función.
- El código sale completo, sin cortarse.

## Qué sigue fallando (prompt con fórmula completa)
- Bug en el horario: weekday() < 5 excluye el sábado y deja pasar sábado/domingo sin validar la hora.
- No descuenta el saldo cuando el pedido es válido.
- Usó diccionarios en vez de objetos con atributos.
- No valida pedido vacío (0 productos).
- La explicación quedó como comentarios, no como lista aparte.

## Variante (sin el bloque de restricciones)
- Mejoró: usó objetos con atributos y aceptó lunes a sábado correctamente (weekday() < 6).
- Empeoró: escribió "para cada producto en productos:" (no es Python válido), rechaza cualquier hora con minutos (minute > 0) y la respuesta quedó cortada.
- Inventó clases Estudiante y Producto que no se pidieron.
- Siguió sin descontar el saldo ni validar el pedido vacío.

## Conclusión
Los bloques de contexto y formato corrigieron lo más grande (lenguaje, retorno, reglas principales). El bloque de restricciones aportó estabilidad: sin él aparecieron errores de sintaxis, de lógica y salidas incompletas. Aun así, el modelo pequeño no cumple todas las reglas, por lo que su código siempre hay que revisarlo.