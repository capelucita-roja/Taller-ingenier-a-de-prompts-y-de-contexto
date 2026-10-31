# Taller: ingeniería de prompts y de contexto

Diplomado en Ingeniería de Software con IA y Sistemas Agénticos · Sesión 03 · Módulo 1

## Integrantes
- Grupo G7
- Diego Fernando Ibañez
- Jean Carlos Godoy Escobar
- Elkin Daniel Villaneda

## Caso
**Caso 2 · CafeFET** (pedidos anticipados a la cafetería de la FET).

## Modelos y equipo usados
- Ollama 0.40.12 en local, sin conexión a servicios externos.
- `qwen-demo` (qwen3.5:4b, temperatura 0, semilla 42) con `--think=false` en los retos 1, 3 y parte B del reto 4.
- `revisor-cafefet-v1` y `revisor-cafefet-v2` (base qwen3.5:4b, temperatura 0) en el reto 2.
- `phi-demo` (phi4-mini) en la parte A del reto 4.
- Equipo: Windows 11, Intel Core i5-11400H, 8 GB de RAM, NVIDIA GeForce GTX 1650.

## Contenido
| Carpeta | Qué contiene |
|---|---|
| `reto1/` | Prompt malo, prompt con la fórmula base y delimitadores, variante sin restricciones, las tres salidas, decisiones adivinadas y comparación. |
| `reto2/` | Modelfile v1 y v2 del revisor, revisiones comparadas, tres ataques de inyección antes y después, y tabla de ataques. |
| `reto3/` | Cadena de tres prompts (historia, criterios, casos de prueba), sus versiones corregidas, salidas y nota del paso corregido. |
| `reto4/` | Cadena de pensamiento con phi-demo, prueba de la ventana de contexto con `num_ctx 512`, salidas y explicación. |

## Resultados principales
- **Reto 1:** con la fórmula base la función pasó de JavaScript con `localStorage` a Python con validaciones de máximo 5 productos, agotados y saldo. Seguía fallando el horario y no descontaba el saldo. Quitar las restricciones introdujo código inválido y una respuesta cortada.
- **Reto 2:** el revisor encontró 3 de 5 errores y respetó el formato; el modelo sin system prompt encontró 1. v1 resistió los tres ataques por la fuerza de su rol, y v2 respondió con frases controladas en dos de ellos. En el ataque del comentario oculto no lo reportó como sospechoso.
- **Reto 3:** el primer error apareció en el prompt 2 (regla inventada de días festivos y formato roto). Al corregirlo, el ejemplo del formato se copió en el contenido, y hubo que cambiarlo en una segunda corrección.
- **Reto 4:** `phi-demo` encontró 0 de 5 errores en una línea y en paso a paso; en este último sus cálculos fueron correctos, pero concluyó al revés. Con `num_ctx 512` la regla dada en el chat se perdió en la tercera respuesta; en `/set system` se mantuvo.

## Reflexión del grupo
La técnica con más efecto en CafeFET fue darle al modelo las reglas del negocio dentro de etiquetas `<reglas>`, junto con un formato de salida exacto. Sin ellas el modelo adivinó todo, desde el lenguaje hasta qué hacer con el saldo. También vimos que los ejemplos *few-shot* pesan más de lo esperado: el modelo copió los números del ejemplo en todos los criterios, y solo cambió cuando usamos un ejemplo de otro tema.

Otra conclusión es que el modelo pequeño nunca cumplió todas las reglas, ni siquiera con el mejor prompt: fallaba el horario, ignoraba el domingo o inventaba comportamientos. Lo que sí mejoró fue la posibilidad de detectar esos fallos, porque con prompts claros las salidas se podían comparar contra una lista de reglas. Además aprendimos que las instrucciones importantes deben ir en el system prompt y no en un mensaje suelto, porque la ventana de contexto descarta lo más antiguo.

Si mañana tuviéramos que pedirle a una herramienta de IA que programe una funcionalidad de nuestro sistema, escribiríamos primero las reglas de negocio y los datos de entrada y salida, prohibiríamos explícitamente inventar reglas, pediríamos casos límite, dividiríamos la tarea en pasos pequeños, y revisaríamos cada salida contra las reglas antes de usar el código.
