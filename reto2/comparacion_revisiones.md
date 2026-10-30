# Reto 2: revisión sin system prompt vs revisor-cafefet-v1

Errores reales de la función (5): `> 6` (debe ser > 5), `< -1000` (el saldo no puede quedar negativo), `<= 18` (18:00 no se acepta), falta validar lunes a sábado, falta validar productos agotados.

| | qwen-demo (sin system) | revisor-cafefet-v1 |
|---|---|---|
| Errores reales encontrados | 1 de 5 (saldo, con razonamiento confuso) | 3 de 5 (máx. 5 productos, saldo, agotados) |
| No encontró | > 6, <= 18, día de la semana, agotados | <= 18 y día de la semana |
| Falsos positivos | Estilo, excepciones, tipos de datos | La regla 5 (30 min), que no corresponde a esta función |
| Formato | Ensayo largo, cortado al final | Respeta VEREDICTO / HALLAZGOS / RESUMEN |

Conclusión: el system prompt hizo que el modelo se centre en las reglas del negocio y respete el formato. Aun así se le escaparon el horario y el día, y marcó la regla de los 30 minutos como error. Por eso hay que revisar también al revisor.