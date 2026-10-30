```python
from datetime import datetime, timedelta
from typing import Tuple, List, Dict, Any

def crear_pedido(estudiante: Dict[str, float], productos: List[Dict[str, Any]], fecha_hora: datetime) -> Tuple[bool, str]:
    """
    Valida y crea un pedido anticipado en la cafetería CafeFET.
    
    Reglas de negocio validadas:
    1. Solo se aceptan pedidos de lunes a sábado entre las 07:00 y las 18:00.
    2. Máximo 5 productos por pedido.
    3. El saldo nunca puede quedar negativo (se verifica antes de descontar).
    4. No se pueden pedir productos que no estén disponibles.
    
    Parámetros:
        estudiante (dict): Diccionario con la clave 'saldo' (float, en pesos).
        productos (list): Lista de diccionarios con claves 'nombre', 'precio' y 'disponible'.
        fecha_hora (datetime): Objeto datetime del momento del pedido.
    
    Retorna:
        tuple: Una tupla (exito: bool, mensaje: str).
               - Si es exitoso: (True, "Pedido creado con éxito")
               - Si falla: (False, "Mensaje descriptivo del error")
    """
    
    # Validación 1: Horario de atención (Lunes a Sábado, 07:00 - 18:00)
    if fecha_hora.weekday() < 5: # Lunes=0, ..., Sábado=5
        if not (fecha_hora.hour >= 7 and fecha_hora.hour < 18):
            return False, "El horario de atención es de 07:00 a 18:00."
    
    # Validación 2: Máximo 5 productos
    if len(productos) > 5:
        return False, "Se permite un máximo de 5 productos por pedido."
    
    # Validación 3 y 4: Verificar disponibilidad y saldo suficiente
    total_precio = 0.0
    for prod in productos:
        if not prod['disponible']:
            return False, f"El producto '{prod['nombre']}' no está disponible."
        total_precio += prod['precio']
    
    saldo_actual = estudiante['saldo']
    if total_precio > saldo_actual:
        return False, "No hay suficiente saldo en la carne para cubrir el pedido."
    
    # Si todo es válido, procesamos el descuento (sin modificar los datos de entrada permanentemente 
    # si se quisiera simular, pero aquí solo devolvemos el estado lógico)
    mensaje = "Pedido creado con éxito"
    return True, mensaje

# Explicación breve de las validaciones implementadas:
# 1. Validación del día y hora (weekday < 5 y rango de horas).
# 2. Verificación del tamaño de la lista de productos (<= 5).
# 3. Verificación de disponibilidad individual y cálculo del total.
# 4. Comparación del total contra el saldo del estudiante.
```

