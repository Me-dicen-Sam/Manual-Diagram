---
titulo: "Manual de Usuario U-Library"
autor: "Samuel Baquero"
fecha: "2025-11-20"
salida:
  documento_md:
    variante: preservar_yaml
    markdown: verdadero
---

# U-Library — Manual de Usuario

## 1. Introducción
U-Library es un sistema web para la gestión de bibliotecas universitarias. Permite administrar libros, autores, estudiantes, préstamos, reservas y reportes. Esta guía explica cómo usar la aplicación desde la perspectiva del usuario final.

## 2. Primeros Pasos

### 2.1 Acceso e Inicio de Sesión
- Abra su navegador y diríjase a la URL de U-Library proporcionada por su institución.
- Ingrese su correo electrónico y contraseña.
- Haga clic en "Iniciar Sesión".

![Pantalla de Login](https://Img/login.png)

### 2.2 Descripción General del Diseño
- **Barra lateral:** navegación entre módulos (Dashboard, Libros, Autores, Editoriales, Estudiantes, Préstamos, Reservas, Categorías, Reportes).
- **Barra superior:** menú de usuario y notificaciones.
- **Área de contenido:** listas, formularios y detalles.

![Dashboard Principal](https://Img/dashboard.png)
![Layout Completo](https://Img/layout.png)

## 3. Gestión de Libros

### 3.1 Listar y Buscar Libros
- Vaya a **Libros** en el menú lateral.
- Use la búsqueda por título, autor o ISBN.
- Aplique filtros por categoría, estado y año de publicación.
- Ordene por columnas haciendo clic en los encabezados.

![Lista de Libros](https://Img/book-list.png)

### 3.2 Crear un Libro
- Haga clic en **"Nuevo Libro"**.
- Complete los campos: ISBN, Título, Año de publicación, Editorial, Categorías, Autores.
- Haga clic en **"Guardar"**.
- Verá una confirmación de éxito.

![Crear Libro](https://Img/book-create.png)

### 3.3 Editar un Libro
- En la lista de libros, abra el menú de la fila y haga clic en **"Editar"**.
- Actualice los campos necesarios.
- Haga clic en **"Guardar Cambios"**.
- Verá una confirmación de éxito.

![Editar Libro](https://Img/book-edit.png)

### 3.4 Eliminar un Libro
- En la lista de libros, abra el menú de la fila y haga clic en **"Eliminar"**.
- Confirme la acción en el diálogo emergente.
- Verá una confirmación de éxito.

![Eliminar Libro](https://Img/book-delete-confirm.png)

## 4. Gestión de Autores

### 4.1 Listar y Buscar Autores
- Vaya a **Autores** en el menú lateral.
- Vea la lista de todos los autores registrados.
- Busque por nombre, apellido o nacionalidad.
- Filtre por nacionalidad si es necesario.

![Lista de Autores](https://Img/author-list.png)

### 4.2 Crear un Autor
- Haga clic en **"Nuevo Autor"**.
- Complete: nombre, apellido, nacionalidad, fecha de nacimiento (opcional), biografía (opcional).
- Haga clic en **"Guardar Autor"**.

![Crear Autor](https://Img/author-create.png)

### 4.3 Editar un Autor
- En la lista de autores, haga clic en **"Editar"**.
- Modifique la información necesaria.
- Guarde los cambios.

![Editar Autor](https://Img/author-edit.png)

### 4.4 Eliminar un Autor
- En la lista de autores, haga clic en **"Eliminar"**.
- Confirme la eliminación.
- **Nota:** No se puede eliminar autores con libros asociados.

![Eliminar Autor](https://Img/author-delete.png)

## 5. Gestión de Editoriales

### 5.1 Listar Editoriales
- Vaya a **Editoriales** en el menú lateral.
- Vea todas las editoriales registradas.
- Busque por nombre o país.

![Lista de Editoriales](https://Img/publisher-list.png)

### 5.2 Crear una Editorial
- Haga clic en **"Nueva Editorial"**.
- Complete: nombre, dirección, teléfono, email, sitio web.
- Haga clic en **"Guardar Editorial"**.

![Crear Editorial](https://Img/publisher-create.png)

### 5.3 Editar una Editorial
- En la lista de editoriales, haga clic en **"Editar"**.
- Actualice la información de contacto.
- Guarde los cambios.

![Editar Editorial](https://Img/publisher-edit.png)

## 6. Gestión de Estudiantes

### 6.1 Listar y Buscar Estudiantes
- Vaya a **Estudiantes**.
- Busque por nombre, código o correo electrónico.
- Aplique filtros por carrera o estado.

![Lista de Estudiantes](https://Img/student-list.png)

### 6.2 Crear un Estudiante
- Haga clic en **"Nuevo Estudiante"**.
- Complete: código de estudiante, nombre, apellido, correo electrónico, teléfono, carrera.
- Haga clic en **"Guardar"**.

![Crear Estudiante](https://Img/student-create.png)

### 6.3 Editar un Estudiante
- En la lista de estudiantes, haga clic en **"Editar"**.
- Actualice la información personal o académica.
- Guarde los cambios.

![Editar Estudiante](https://Img/student-edit.png)

### 6.4 Desactivar un Estudiante
- En la lista de estudiantes, haga clic en **"Desactivar"**.
- Confirme la acción.
- El estudiante no podrá hacer nuevos préstamos pero mantendrá su historial.

![Desactivar Estudiante](https://Img/student-deactivate.png)

## 7. Gestión de Categorías

### 7.1 Listar Categorías
- Vaya a **Categorías** en el menú lateral.
- Vea todas las categorías temáticas disponibles.
- Busque por nombre de categoría.

![Lista de Categorías](https://Img/category-list.png)

### 7.2 Crear una Categoría
- Haga clic en **"Nueva Categoría"**.
- Ingrese: nombre y descripción (opcional).
- Haga clic en **"Guardar Categoría"**.

![Crear Categoría](https://Img/category-create.png)

### 7.3 Editar una Categoría
- En la lista de categorías, haga clic en **"Editar"**.
- Modifique el nombre o descripción.
- Guarde los cambios.

![Editar Categoría](https://Img/category-edit.png)

## 8. Gestión de Préstamos

### 8.1 Crear un Préstamo
- Vaya a **Préstamos**.
- Haga clic en **"Nuevo Préstamo"**.
- Seleccione estudiante y ejemplar del libro.
- El sistema establece automáticamente la fecha de vencimiento (15 días).
- Haga clic en **"Crear Préstamo"**.

![Crear Préstamo](https://Img/loan-create.png)

### 8.2 Préstamos Activos
- Vea todos los préstamos activos en la lista.
- Filtre por estudiante, estado o fecha de vencimiento.
- Identifique préstamos próximos a vencer (resaltados en amarillo).

![Préstamos Activos](https://Img/loan-active-list.png)

### 8.3 Devolver un Libro
- En la lista de préstamos activos, haga clic en **"Devolver"**.
- Confirme la devolución en el diálogo.
- El estado cambiará a **"devuelto"** automáticamente.
- Si hay multas por retraso, el sistema las calculará automáticamente.

![Devolver Libro](https://Img/loan-return.png)

### 8.4 Renovar Préstamo
- En préstamos activos, haga clic en **"Renovar"**.
- El sistema extiende la fecha de vencimiento por 15 días más.
- **Límite:** máximo 2 renovaciones por préstamo.

![Renovar Préstamo](https://Img/loan-renew.png)

## 9. Gestión de Reservas

### 9.1 Listar Reservas
- Vaya a **Reservas**.
- Vea reservas pendientes, confirmadas o vencidas.
- Filtre por estado o estudiante.

![Lista de Reservas](https://Img/reservation-list.png)

### 9.2 Crear una Reserva
- Haga clic en **"Nueva Reserva"**.
- Seleccione estudiante y libro (no ejemplar específico).
- El sistema asigna automáticamente fecha de expiración (3 días).
- Haga clic en **"Confirmar Reserva"**.

![Crear Reserva](https://Img/reservation-create.png)

### 9.3 Cancelar Reserva
- En la lista de reservas, haga clic en **"Cancelar"**.
- Confirme la cancelación.
- El libro quedará disponible para otros estudiantes.

![Cancelar Reserva](https://Img/reservation-cancel.png)

## 10. Ejemplares de Libros

### 10.1 Gestionar Ejemplares
- Desde el detalle de un libro, vaya a la pestaña **"Ejemplares"**.
- Vea todos los ejemplares físicos del libro.
- Cada ejemplar tiene un código único.

![Gestión de Ejemplares](https://Img/book-copies.png)

### 10.2 Agregar Ejemplar
- Haga clic en **"Agregar Ejemplar"**.
- Ingrese el código del ejemplar y ubicación.
- El estado por defecto es **"Disponible"**.

![Agregar Ejemplar](https://Img/add-copy.png)

### 10.3 Cambiar Estado de Ejemplar
- Para cada ejemplar, puede cambiar el estado:
  - **Disponible:** listo para préstamo
  - **Prestado:** actualmente en préstamo
  - **En reparación:** no disponible temporalmente
  - **Extraviado:** dado por perdido

![Cambiar Estado Ejemplar](https://Img/copy-status.png)

## 11. Notificaciones y Errores

### 11.1 Mensajes de Éxito
- Las acciones exitosas muestran un mensaje toast **verde**.
- Ejemplo: "✅ Libro creado exitosamente"
- Desaparecen automáticamente después de 5 segundos.

![Mensaje de Éxito](https://Img/success-message.png)

### 11.2 Mensajes de Error
- Los errores de validación muestran un mensaje toast **rojo**.
- Ejemplo: "❌ El estudiante ya tiene el máximo de préstamos"
- Permanen hasta que se corrijan los errores.

![Mensaje de Error](https://Img/error-validation.png)

### 11.3 Diálogos de Confirmación
- Para acciones importantes (eliminar, desactivar), aparece un diálogo de confirmación.
- Debe hacer clic en **"Confirmar"** para proceder.

![Diálogo de Confirmación](https://Img/confirmation-dialog.png)

## 12. Consejos y Mejores Prácticas

### 12.1 Para Búsquedas Eficientes
- Use los controles de paginación en la parte inferior de las listas.
- Combine búsqueda con filtros para resultados más rápidos.
- Use el autocompletado en campos de búsqueda.

### 12.2 Para Gestión de Datos
- Mantenga el correo electrónico del estudiante único para evitar duplicados.
- Verifique siempre la disponibilidad antes de crear préstamos.
- Actualice regularmente los estados de los ejemplares.

### 12.3 Para Reportes
- Genere reportes mensuales de actividad.
- Revise regularmente los préstamos vencidos.
- Monitoree los libros más solicitados.

## 13. Solución de Problemas Comunes

### 13.1 "No puedo crear un préstamo"
- Verifique que el estudiante esté activo.
- Confirme que el ejemplar esté disponible.
- Revise que el estudiante no tenga préstamos vencidos.

### 13.2 "No aparece un libro en búsqueda"
- Verifique la ortografía del título.
- Intente buscar por ISBN.
- Confirme que el libro no esté marcado como inactivo.

### 13.3 "Error al guardar cambios"
- Revise que todos los campos obligatorios estén completos.
- Verifique que los datos tengan el formato correcto.
- Confirme que no haya duplicados (email, código estudiante, ISBN).

---
