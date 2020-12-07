# C�mo trabajar con Bootstrap 

Lo primero que tenemos que hacer es desde una ventana de MS-DOS situarnos en la carpeta del proyecto y ejecutar el siguiente comando

		**npm install**

para crear la carpeta node_modules e integrar el framework Bootstrap en el proyecto

Por defecto al crear un proyecto MVC nos crea en la carpeta Views. En ella creamos la subcarpeta Shared y el fichero _Layout.cshtml. Esta p�gina es la plantilla que usar� el asistente de las vistas cuando no seleccionamos ninguna.
Es el equivalente a las MasterPages en WebPages, es decir la plantilla com�n para todas las p�ginas de nuestro sitio. 
El contenido por defecto de la plantilla ser�

~~~
    <div class="view-container">
        @RenderBody()
    </div>
~~~

**@RenderBody()**
Se utiliza en _layout.cshtml para indicar que en ese punto se incluir� el c�digo generado por la vista.

Todos los layouts deben incluirla. En caso de no hacerlo obtendremos el siguiente mensaje de error.

Error de servidor en la aplicaci�n '/'.

No se ha llamado al m�todo "RenderBody" para la p�gina de dise�o "~/Views/Shared/_layout.cshtml".

### Uso de vistas con nuestro controlador

Ahora creamos la vista a partir del controlador. En la ventana del c�digo **LibraryController.cs**, hacemos clic con el bot�n derecho del rat�n 
en el siguiente c�digo y luego haga clic en **Add View**.

    `public IActionResult Index()`

Si bien es posible escribir c�digo dentro de nuestros m�todos de acci�n para ensamblar HTML y luego usar el m�todo auxiliar Response.Write() 
para enviarlo de vuelta al cliente, ese enfoque se vuelve bastante dif�cil de controlar r�pidamente. Un enfoque mucho mejor es que solo realicemos 
la l�gica de aplicaciones y datos dentro de nuestros m�todos de acci�n y, a continuaci�n, pasemos los datos necesarios para representar una respuesta 
HTML a una plantilla de "vista" independiente que sea responsable de generar la representaci�n HTML de la misma. 
Como veremos en un momento, una plantilla de "vista" es un archivo de texto que normalmente contiene una combinaci�n de marcado HTML y c�digo 
de representaci�n incrustado.

Separar nuestra l�gica de controlador de nuestra representaci�n de vista trae varios grandes beneficios. En particular, ayuda a aplicar una clara 
"separaci�n de preocupaciones" entre el c�digo de la aplicaci�n y el formato de la interfaz de usuario/c�digo de representaci�n. Esto hace que sea 
mucho m�s f�cil probar la l�gica de la aplicaci�n de prueba unitaria de forma aislada de la l�gica de representaci�n de la interfaz de usuario. 
Facilita la modificaci�n posterior de las plantillas de representaci�n de la interfaz de usuario sin tener que realizar cambios en el c�digo de la 
aplicaci�n. Y puede facilitar que los desarrolladores y dise�adores colaboren juntos en proyectos.