
---

# Ejercicio Práctico: Dashboard de Inventario "Sustantiva Tech" con Vue

## Objetivo

Construir una interfaz interactiva para la gestión de productos tecnológicos. Deberás aplicar de forma práctica la sintaxis de templates basada en HTML para vincular el DOM a los datos de la aplicación. El ejercicio integra interpolación, directivas, modificadores y renderizado dinámico sobre un **DOM Virtual**.

## Requisitos Técnicos

1. **Entorno**: Crear un proyecto base utilizando la **Vue CLI** (Vue 3 + JavaScript).
2. **Estilos**: Utilizar **Bootstrap 5** agregando el enlace CDN directamente en el archivo `public/index.html`.



---

## Instrucciones del Desafío

### 1. Configuración del Proyecto

* Inicializa un nuevo proyecto desde la terminal utilizando el comando `vue create nombre-del-proyecto`.
* Selecciona **Vue 3** y asegúrate de trabajar con **JavaScript**.
* En el archivo `public/index.html`, añade el CSS de Bootstrap en el `<head>`.
* Limpia el componente principal (`App.vue`) para comenzar tu desarrollo desde cero.

### 2. Identidad Visual (v-bind e Interpolación)

* Muestra un título para la aplicación utilizando **interpolación** (sintaxis de mustaches `{{ }}`).


* Añade un subtítulo que muestre el nombre del "Encargado de Inventario". El nombre debe transformarse a **mayúsculas** mediante una expresión de JavaScript directamente en el enlace de datos.


* Inserta una imagen (logo) cuyo atributo `src` esté enlazado dinámicamente utilizando la directiva correspondiente para atributos.



### 3. Registro de Productos (Modelos y Atributos)

* Crea una sección de interfaz (sin etiqueta `<form>`) con campos para: **Nombre del producto**, **Precio** y **Categoría** (select).
* Enlaza estos campos a variables reactivas utilizando enlaces bidireccionales.


* Añade un botón de "Registrar Producto".
* Este botón debe ejecutar una función al detectar el evento de clic.


* El botón debe estar **deshabilitado** (usando binding de atributos booleanos) si el campo del nombre está vacío.




* Aplica un **modificador** al campo de texto para que el valor se limpie automáticamente de espacios en blanco al inicio y al final.



### 4. Visualización Dinámica (v-for y v-if)

* Crea una tabla o una lista de tarjetas de Bootstrap para mostrar los productos.
* Utiliza una directiva para iterar sobre el arreglo de productos registrados.


* Debes definir y usar un **alias para el índice** de la iteración.


* Es obligatorio usar el atributo `:key` con un identificador único para optimizar el rendimiento del DOM.




* Implementa lógica condicional para el stock:


* Si la lista está vacía, muestra un mensaje informativo.


* Si hay elementos, el mensaje debe desaparecer del DOM real.





### 5. Lógica de Control y Rendimiento

* Añade un botón "Eliminar" en cada elemento de la lista que borre ese registro específico.
* Implementa un aviso de "Capacidad Crítica" que solo sea visible cuando la cantidad de productos sea superior a 5 elementos.
* Utiliza una directiva que solo altere la propiedad CSS `display`, manteniendo el elemento siempre en el DOM.




* Utiliza una directiva especial para que el ID de la sesión de inventario se renderice **una sola vez** y no se actualice aunque cambien otros datos de la aplicación.



### 6. Personalización y Sintaxis Abreviada

* Para mejorar la legibilidad del código, utiliza el **modo abreviado** para todos los enlaces de atributos y de eventos.


* 
**Desafío Extra**: Haz que el precio del producto cambie de color dinámicamente (clases de Bootstrap) si el valor ingresado es superior a $100 mediante expresiones de JavaScript en el atributo clase.



---
