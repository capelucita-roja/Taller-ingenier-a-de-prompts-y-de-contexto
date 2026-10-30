# Reto 3: nota sobre la cadena de prompts

Cadena final: prompt1_historia.txt -> prompt2_criterios_v3.txt -> prompt3_tabla_v2.txt

## ¿En qué paso apareció el primer error?
En el Prompt 2 (criterios). El Prompt 1 produjo una historia correcta (solo imprecisa: "preparación de mi comida").
En el Prompt 2 original (salida2.md) aparecieron:
- Regla inventada: "días festivos" (no existe en las reglas de CafeFET) y se olvidó el domingo.
- Formato roto: cada criterio en una sola línea, no en tres.
- Escenario imposible: "repetir un pedido con más de 5 productos".
- Comportamiento inventado: "se excluyen los productos agotados".

## Qué corregimos y por qué
1. prompt2_criterios_v2: prohibimos inventar reglas, pedimos datos concretos y un ejemplo de formato. Resultado: el formato quedó bien y desaparecieron los festivos, pero el modelo copió los números del ejemplo (saldo $5.000 / pedido $4.000) en los 5 criterios y faltaban reglas (saldo insuficiente, agotados, máximo 5).
2. prompt2_criterios_v3: cambiamos el ejemplo por otro tema, definimos 5 situaciones obligatorias (A-E) y aclaramos la regla de los 30 minutos. Resultado: 5 criterios completos, sin reglas inventadas.
3. prompt3_tabla_v2: pedimos datos concretos, casos de frontera y una verificación contra las reglas. Resultado: pasamos de 5 casos vagos a 10 casos ejecutables.

## Qué sigue fallando
- Caso 3 inventa que el pedido se crea con los productos disponibles.
- Caso 9 usa precio $0 en vez de un pedido que consume todo el saldo.
- Falta un caso de 5 productos válidos y uno a las 7:00 exactas.
- La auto-verificación fue superficial o no apareció.

## Lección
Un error en un paso se arrastra a los siguientes, y los ejemplos few-shot influyen tanto en el formato como en el contenido (el modelo copió los números). Corregir un prompt puede resolver un problema y crear otro, así que hay que repetir la cadena desde el paso que falló y revisar cada salida.