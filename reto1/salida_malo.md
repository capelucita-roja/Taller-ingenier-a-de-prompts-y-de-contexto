Aquí tienes un ejemplo completo y funcional de cómo crear una función para gestionar pedidos. He utilizado **JavaScript** (que es el estándar más común) pero he estructurado el código de manera que puedas adaptarlo fácilmente a tu lenguaje o framework favorito (como Python, PHP, etc.).

Este ejemplo incluye:
1.  Validación básica de datos.
2.  Cálculo automático del total.
3.  Generación de un ID único para el pedido.
4.  Simulación de almacenamiento en una base de datos local (`localStorage`) para que los pedidos persistan al recargar la página.

### Código Ejemplo (JavaScript)

```javascript
class GestorPedidos {
    constructor() {
        this.pedidos = []; // Array vacío para almacenar pedidos
        this.siguienteId = 1; // Contador para IDs únicos
    }

    /**
     * Función principal para crear un nuevo pedido
     * @param {Object} datos - Objeto con la información del pedido
     * @returns {Object} El objeto creado o null si hay error
     */
    crearPedido(datos) {
        // 1. Validación de entrada
        if (!datos || !datos.cliente || !datos.items) {
            console.error("Error: Faltan datos obligatorios (cliente o items).");
            return null;
        }

        // 2. Calcular el total del pedido
        const total = this.calcularTotal(datos.items);

        // 3. Construir el objeto pedido
        const nuevoPedido = {
            id: `PED-${this.siguienteId.toString().padStart(4, '0')}`, // Formato de ID (ej: PED-0001)
            fecha: new Date().toISOString(), // Fecha y hora actual
            cliente: datos.cliente,
            items: datos.items,
            total: total,
            estado: "Pendiente" // Estado inicial
        };

        // 4. Guardar en la base de datos simulada (LocalStorage)
        this.guardarPedido(nuevoPedido);

        // 5. Actualizar el contador de IDs
        this.siguienteId++;

        console.log(`✅ Pedido creado exitosamente: ${nuevoPedido.id}`);
        return nuevoPedido;
    }

    /**
     * Calcula la suma total de los items del pedido
     * @param {Array} items - Array de objetos con precio y cantidad
     * @returns {number} Total numérico
     */
    calcularTotal(items) {
        let subtotal = 0;
        for (let item of items) {
            // Asegurarse de que precio y cantidad sean números
            const precio = parseFloat(item.precio) || 0;
            const cantidad = parseInt(item.cantidad) || 0;
            subtotal += (precio * cantidad);
        }
        return subtotal.toFixed(2); // Formatear a 2 decimales
    }

    /**
     * Guarda el pedido en LocalStorage para persistencia básica
     */
    guardarPedido(pedido) {
        const pedidosExistentes = JSON.parse(localStorage.getItem('misPedidos')) || [];
        pedidosExistentes.push(pedido);
        localStorage.setItem('

