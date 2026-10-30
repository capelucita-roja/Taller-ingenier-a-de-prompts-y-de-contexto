# Reto 4: explicación

## Parte A: cadena de pensamiento (phi-demo)
- En una línea: 0 de 5 errores. El modelo inventó un problema inexistente y devolvió el mismo código.
- Paso a paso con datos concretos: 0 de 5 como conclusión, pero la traza mostró evidencia de 3 errores (> 6, < -1000, <= 18): los cálculos eran correctos, la interpretación final no.
- Conclusión: pedir el razonamiento por escrito hace visible dónde falla el modelo y deja verificar cada paso, pero un modelo pequeño puede calcular bien y concluir mal.

## Parte B: la instrucción que se olvida (qwen-demo, num_ctx 512)
- Regla en el chat: se cumplió en las respuestas 1 y 2 y se perdió en la 3.
- Regla en /set system: se cumplió en las 3 respuestas.

### Qué pasó
La ventana de contexto (512 tokens) es la memoria de trabajo del modelo. Las respuestas largas (400+ palabras) la llenaron y, para seguir, se descartó lo más antiguo: el primer mensaje del chat, que contenía la regla. Sin ella en el contexto, el modelo ya no sabía que debía empezar con VEREDICTO.
El system prompt se conserva al inicio del contexto aunque el historial se recorte, por eso la regla sobrevivió.

### Lección práctica
Las reglas importantes (formato, restricciones, reglas del negocio) deben ir en el system prompt, no en un mensaje suelto de una conversación larga, y las conversaciones largas deben reiniciarse o resumirse. (Referencia: prácticas 9 y 14B de GUIA_PRACTICAS.md.)