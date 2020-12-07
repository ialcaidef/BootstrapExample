# Cómo trabajar con Bootstrap 

Lo primero que tenemos que hacer es desde una ventana de MS-DOS situarnos en la carpeta del proyecto y ejecutar el siguiente comando

		npm install

para crear la carpeta node_modules e integrar el framework Bootstrap en el proyecto

Por defecto al crear un proyecto MVC nos crea en la carpeta Views. En ella creamos la subcarpeta Shared y el fichero _Layout.cshtml. Esta página es la plantilla que usará el asistente de las vistas cuando no seleccionamos ninguna.
Es el equivalente a las MasterPages en WebPages, es decir la plantilla común para todas las páginas de nuestro sitio. 
El contenido por defecto de la plantilla será

~~~
    <div class="view-container">
        @RenderBody()
    </div>
~~~

**@RenderBody()**
Se utiliza en _layout.cshtml para indicar que en ese punto se incluirá el código generado por la vista.

Todos los layouts deben incluirla. En caso de no hacerlo obtendremos el siguiente mensaje de error.

Error de servidor en la aplicación '/'.

No se ha llamado al método "RenderBody" para la página de diseño "~/Views/Shared/_layout.cshtml".

### Uso de vistas con nuestro controlador

Ahora creamos la vista a partir del controlador. En la ventana del código **LibraryController.cs**, hacemos clic con el botón derecho del ratón 
en el siguiente código y luego haga clic en **Add View**.

    public IActionResult Index()

Si bien es posible escribir código dentro de nuestros métodos de acción para ensamblar HTML y luego usar el método auxiliar Response.Write() 
para enviarlo de vuelta al cliente, ese enfoque se vuelve bastante difícil de controlar rápidamente. Un enfoque mucho mejor es que solo realicemos 
la lógica de aplicaciones y datos dentro de nuestros métodos de acción y, a continuación, pasemos los datos necesarios para representar una respuesta 
HTML a una plantilla de "vista" independiente que sea responsable de generar la representación HTML de la misma. 
Como veremos en un momento, una plantilla de "vista" es un archivo de texto que normalmente contiene una combinación de marcado HTML y código 
de representación incrustado.

Separar nuestra lógica de controlador de nuestra representación de vista trae varios grandes beneficios. En particular, ayuda a aplicar una clara 
"separación de preocupaciones" entre el código de la aplicación y el formato de la interfaz de usuario/código de representación. Esto hace que sea 
mucho más fácil probar la lógica de la aplicación de prueba unitaria de forma aislada de la lógica de representación de la interfaz de usuario. 
Facilita la modificación posterior de las plantillas de representación de la interfaz de usuario sin tener que realizar cambios en el código de la 
aplicación. Y puede facilitar que los desarrolladores y diseñadores colaboren juntos en proyectos.
