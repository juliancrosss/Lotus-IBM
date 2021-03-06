# Lotus-IBM
Manego de Lotus software 


Formulas de Lotus Script
En un formulario 
El formulario tiene muchos eventos, en los que se puede incluir código,
pero para nuestra aplicación de momento sólo vamos a ver el evento Windows Title.
Este evento sirve para ponerle un título a la ventana, que se mostrará al crear o visualizar un documento,
una fórmula posible para este evento sería: 
* @If(@IsNewDoc;"Noticia Nueva";Ttitulo).
Con esta fórmula, si se creara un nuevo documento nos aparecería “Noticia Nueva” y si visualizáramos un documento ya creado nos mostraría
el contenido del campo Ttitulo.

* En los eventos del formulario/ Window Title/Fórmula escribimos: 
@If(@IsNewDoc;"Nueva Lista de Distribución";tNombre)


*Campos compartidos

A la derecha pulsamos en el botón, .
Las propiedades de estos campos son iguales que los no compartidos.
Para nuestra aplicación vamos a crear los siguientes dos campos compartidos:

Nombre Campo	Tipo	Valor por Defecto/Fórmula
tModificador	Texto-Calculado	@Name([CN];@UserName)
fModificacion	Fecha/hora-Calculado	@Modified


*Acciones
Las acciones se pueden incluir en formularios, vistas, subformularios y páginas y en todos estos elementos de diseño se crean de la misma manera.
Abrimos nuestro formulario de Noticias, abrimos el panel de acciones, (Ver Figura 5.6.0), nos situamos en el y pulsamos en el Menú Create /Action / Action
*Al insertar una acción nos muestra directamente sus propiedades.
En el cuadro de texto Name, le ponemos un nombre, identificativo con la acción que se vaya a ejecutar.
Por ejemplo, vamos a crear una acción que edite el documento, para poder introducir valores en los campos de un documento,
La fórmula para esta acción sería @Command([Editdocument]).


*Acciones compartidas:
Las acciones compartidas al igual que los campos compartidos se crean una sola vez y pueden ser usadas en varios formularios, vistas o páginas.
Casi todos los formularios tienen las acciones, Guardar, Modificar, Imprimir y Salir y casi todas las vistas incluyen una acción para crear nuevos documentos.
Para crear una acción compartida, pulsamos en la lista de elementos de diseño en Shared Code / Actions
*Las propiedades de estas acciones son iguales que las que no son compartidas.
Para nuestra aplicación vamos a crear estas cinco acciones compartidas cada una con un icono diferente y con las siguientes fórmulas:
Acción	Fórmula	Descripción	Ocultar
Guardar	@Command([filesave])	Guarda el documento.	En lectura
Modificar	@Command([Editdocument])	Pasa el documento a modo Edición.	En edición
Imprimir	@Command([fileprint])	Imprime el documento.	No
Salir	@Command([fileclosewindow])	Sale del documento.	No
Crear noticia	@Command([Compose];”FNoticia”)	Crea un nuevo documento de noticia.	No


*Subformularios
En los subformularios se pueden insertar los mismos elementos de diseño que en un formulario, aunque la diferencia es que por si solos no tienen ninguna funcionalidad, deben estar insertados en un formulario para que pueda verse su contenido.
Para crear un nuevo Subformulario, pulsamos en la lista de elementos de diseño en Shared Code / Subforms


*(Propiedades de un subformulario)
En el cuadro de texto Name, le ponemos un nombre: 1.0.-Acciones Lotus Notes e incluimos un Alias: SFAcciones.
Entre el nombre y el alias hay que poner el carácter “|” que se consigue con la combinación de teclas Alt. Gr. + 1. 
Include in Insert Subform…dialog, seleccionamos esta propiedad, para que podamos seleccionarlo desde cualquier formulario.
*Este subformulario lo vamos a usar para insertar en el las acciones compartidas que hemos creado anteriormente.
Para insertar estas acciones, nos situamos en el subformulario, abrimos el panel de acciones, y pulsamos en el menú Create / Action /Insert Shared Action.
En la pantalla que nos sale, seleccionamos todas las acciones que queremos insertar, en nuestro caso Editar, Guardar, Salir e imprimir y pulsamos en el botón Insert

*Agregando campos compartidos 
Seleccionamos Include in Insert Subform…dialog, para que podamos seleccionarlo desde cualquier formulario.
Antes de insertar los campos compartidos, creamos una tabla de 2 filas y 2 columnas, el la columna de la izquierda vamos a incluir los textos o literales que describen el contenido que va a tener el campo, (Ver Figura 5.8.4).
En la columna de la derecha vamos a insertar los campos compartidos.
Nos situamos en la columna derecha, primera fila y pulsamos en el menú Create / Resource / Insert Shared Field, nos aparecerá la siguiente pantalla:

Seleccionamos el campo tModificador y pulsamos en el botón OK, hacemos lo mismo con el campo fModificador.



*Insertar subformularios
Vamos a insertar los dos subformularios que hemos creado en todos nuestros formularios, ya que queremos, que todos tengan acciones y los campos compartidos de quién a modificado el documento y qué día.
Para insertar estos subformularios nos vamos a la lista de elementos de diseño formularios, 
A la derecha nos queda el listado de los formularios que hemos creado, hacemos doble clic sobre el formulario 2.0.-Lista de Distribución para abrirlo.
Nos situamos en la primera línea del formulario que hemos abierto y pulsamos en el menú Create / Resource /Insert Subform,
En la siguiente pantalla, seleccionamos el subformulario 1.0.-Acciones Lotus Notes y pulsamos sobre el botón OK.


*Personalización de la barra de acciones:
Nos situamos en la vista de formulario y hacemos doble click sobre nuestro formulario principal, 1.0.- Formulario Noticia.
Dentro del formulario abrimos el panel de acciones con el menú, View / Action Pane, nos situamos en el y pulsamos sobre el con el botón derecho del ratón, nos saldrá el siguiente menú,
Pulsamos sobre Action Bar Properties y nos mostrará las propiedades de la barra de acciones
El menú de las barras de acciones tiene muchas posibilidades de personalización, nosotros vamos a ponerle un fondo diferente acorde con los colores de nuestra aplicación en la tercera pestañaColor
Vamos a cambiar también el estilo y el color de fondo de los botones, en la quinta pestaña
Button OptionsDisplay borderElegimos Notes Style y en Button Background Color Elegimos el color Blanco


*Vistas

Una vista sirve para mostrar y organizar los datos de los formularios. Las vistas pueden mostrar datos de documentos creado con un formulario o de varios.
Vamos a Crear las vistas Necesarias para nuestra aplicación, unas nos mostrarán los documentos creados con el formulario de noticia y otras los de listas de distribución.
Vamos a crear esta vista para que muestre los documentos de noticia categorizados (agrupados) por el campo Autor, es decir todos los documentos creados por el mismo autor formarán una categoría y de esta, colgaran todos sus documentos.
Al abrir la vista nos aparecen sus propiedades, en el caso de que no aparezcan, nos situaríamos en la vista y pulsamos sobre el SmartIcon .
Le ponemos un nombre y un alias, fijándonos en la peculiaridad de las vistas, tienen una casilla especial para el Alias, no es necesario utilizar el carácter “|” para separar el nombre del Alias como pasaba en los formularios y subformularios,
Hacemos doble click en la segunda pestaña y nos aparecen las siguientes opciones:

Default when databases in first oponed, poner esta vista como predeterminada.
Una vista predeterminada es la vista que ven los usuarios cuando abren la base de datos por primera vez. Cada base de datos debe tener una vista predeterminada, que aparece marcada con un * (asterisco) en la lista de vistas.
Default design for new folders and views, seleccionando esta opción, todas las vistas que se creen nuevas cogen el diseño de esta, aunque al crear una vista nueva se puede indicar otra vista para heredar su diseño. 
En el resto de pestañas, podemos cambiar los colores de la vista y otras propiedades relacionadas con el diseño, además de restringir el acceso de usuarios a la misma en la sexta pestaña.
Ahora lo que nos interesa es como indicarle a esta vista que sólo nos muestre los documentos creados con el formulario noticia, para ello nos situamos en la fórmula de selección de la vista, en Ejecuta seleccionamos: Fórmula y en el panel de fórmula ponemos la siguiente: Select Form=”FNoticia”.
Select Form=”FNoticia
En Object /View Section/ Formula  Select Form=”FNoticia


*Crear y personalizar columnas de la vista:
Pinchamos sobre el triangulo blanco que aparece al lado de la palabra View, (Ver Figura 5.11.2) y nos sale una lista de elementos de los cuales podemos modificar sus propiedades, este triangulo es igual en todos los elementos de diseño, pero no las opciones que se despliegan.
Seleccionamos de la lista Column.

*Cambiando de elemento de diseño)
Nos tiene que mostrar las propiedades de la columna.
A esta columna le ponemos un título, en este caso Autor, y marcamos la opción Show twistie when row is expandable (Mostrar imagen si la fila puede desplegarse), al ser una columna categorizada, nos tiene que mostrar el triangulito para poder desplegar o plegar esta categoría.
Si pusiéramos Display values as icons, y en la fórmula un número, dependiendo del número nos mostraría un icono de los siguientes:
En la siguiente pestaña seleccionamos Sort: Ascending (Ordena Ascendente) y Type: Categorized (Por Categorías),

*(Configurando la ordenación de los datos)

Totals: Como su nombre indica esta opción sirve para configurar totales en las vistas.
Si desplegamos esta opción podemos elegir entre:
Total: calcula el total global para todos los documentos principales y muestra ese total en la parte inferior.
Media por documento: calcula la media global hallando el total de los documentos principales y dividiendo ese valor por el número de documentos principales. Por ejemplo, si hay cuatro documentos y su total es 10, la media por documento será 2,5.
Media por subcategoría: calcula la media para cada categoría. Dentro de cada subcategoría se suman los documentos y el valor resultante se divide por el número de documentos.
% de la categoría superior: calcula el total para todos los documentos principales. Para cada categoría, Notes muestra el porcentaje de ésta en relación con el total global de la vista.
% de todos los documentos: calcula el total para todos los documentos principales. Para cada categoría, Notes muestra el porcentaje de ésta en relación con el total global de la vista.
Hide detail rows: se eliminan los subtotales de cada categoría y subcategoría y se muestran los totales sin sobrecargar la vista con un exceso de números. 


*En el resto de pestañas de las propiedades de las columnas podemos configurar el formato y el color del texto, del título y el formato numérico en el caso de que el campo que asignamos a esta columna sea de este tipo.
Ahora vamos a asignarle a esta columna el valor del campo Autor que es el que queremos que nos muestre, en la fórmula de la columna, seleccionamos Field y elegimos el campo tAutor.


*( Poniendo fórmula a una columna)

Por tanto la primera columna de esta vista nos mostrará el contenido del campo Autor de los documentos creados con el formulario de noticias.
Agregar Columnas:
Vamos a Agregar más columnas a esta vista, hacemos Doble Click a la derecha de la primera columna que hemos creado.


*En las propiedades de la columna no marcamos Mostrar triángulo si la fila puede desplegarse, la ordenación sería Order: ascendente y en Type marcamos Standard.
Le ponemos como Title de la columna: Noticia y en la fórmula de columna seleccionamos el campo tTitulo.
Ahora vamos a insertar la acción compartida “Crear noticia”, nos situamos en el panel de acciones de la vista, y pulsamos en el menú Create / Action / Insert Shared Actio






*Creacion de tres vistas 


*Pulsamos en nueva vista,.
Para nuestra aplicación vamos a crear 3 vistas más:
Vista por Fecha:
Con nombre: 1.1.-Noticias por Fecha
Alias: VNoticiasxFecha
Fórmula de selección: Select Form=”FNoticia”
Esta vista tendrá 3 columnas: 
En Fórmula de columna, seleccionamos Field y elegimos el campo fFecha. En la ordenación seleccionamos: Order: descendente y en Type marcamos Categorized.
En Fórmula de columna, seleccionamos Field y elegimos el campo tTitulo. En la ordenación seleccionamos: Order: ascendente y en Type marcamos Standard.
Fórmula de columna, seleccionamos Field y elegimos el campo, tAutor. En la ordenación seleccionamos: Order: ascendente y en Type marcamos Standard.




*Vista por Categoría de la noticia:
Con nombre: 1.2.-Noticias por Categoría
Alias: VNoticiasxcategoria
Fórmula de selección: Select Form=”FNoticia”
Esta vista tendrá 3 columnas: 
En Fórmula de columna, seleccionamos Field y elegimos el campo, dlgCategoria. En la ordenación seleccionamos: Order: ascendente y en Type marcamos Categorized.
En Fórmula de columna, seleccionamos Field y elegimos el campo, tTitulo. En la ordenación seleccionamos: Order: ascendente y en Type marcamos Standard.
Fórmula de columna, seleccionamos Field y elegimos el campo, tAutor. En la ordenación seleccionamos: Order: ascendente y en Type marcamos Standard.
Guardamos la vista pulsando sobre el SmartIcon,  y la cerramos.


*Vista para ver todos los documentos:
Con nombre: Todos
Alias: VTodos
Fórmula de selección: Select @All
Esta vista tendrá 1 columna, ordenada Ascendente-Standard y con la fórmula: @Text(@DocumentUniqueId).
Guardamos la vista pulsando sobre el SmartIcon,  y la cerramos.



*Vista para la lista de distribución:
Esta vista va a ser diferente a las anteriores, ya que los documentos que nos va a mostrar serán los creados con el formulario 2.0.-Lista de distribución.
Con nombre: VListaDistribucion
Alias: VListaDistribucion
Fórmula de selección: SELECT form="FLista"
Esta vista tendrá 2 columnas:
En Fórmula de columna, seleccionamos Field y elegimos el campo, tNombre. En la ordenación seleccionamos Order: ascendente y en Type marcamos Standard.
Fórmula de columna, seleccionamos Fórmula y ponemos: @name([CN];tMiembros), esta función elimina la jerarquía del nombre de usuario, dando como resultado el nombre común (Nombre y apellidos).
En la ordenación seleccionamos Order: ascendente y en Type marcamos Standard.

La segunda columna va a tener una particularidad, en la primera pestaña de sus propiedades, vamos a elegir en el separador de múltiples valores; New Line, ya que el campo tMiembros del formulario “FLista”, tenía la propiedad de poder incluir valores múltiples,
queremos que cada uno de estos valores se muestre en una línea de la columna.


*(Cambiando el separador de múltiples valores)
En esta vista vamos a crear una acción que se llame “Crear Lista”, nos situamos en el panel de acciones y pulsamos sobre ella con el botón derecha del ratón,
en el menú que se despliega seleccionamos, Create Action.


Nombre de la acción: Crear lista de distribución.
Elegimos un icono para esta acción.
En el panel de fórmulas escribimos: @Command([Compose];”FLista”).



*Creando documentos
Nos situamos en una de las vistas de noticias y pulsamos sobre la acción que hemos llamado “Crear Noticia”, vamos a crear algunos documentos nuevos, rellenando todos los datos posibles, para visualizarlos en las vistas y luego poder trabajar con ellos.
Hacemos lo mismo en la vista “Lista de distribución”, creamos algunos documentos nuevos pulsando en la acción que hemos llamado “Crear Lista”.

*Vistas ocultas
Las vistas que se definan como ocultas sólo se podrán ver en modo diseño, de tal manera que el usuario desde el cliente lotus notes no podrá verlas, se suelen utilizar para recuperar valores en campos, para los agentes y también para que los programadores lleven un control de todos los documentos creados en la base de datos.
Para nuestra aplicación vamos a crear dos vistas ocultas que nos servirán para recuperar los valores de los campos Categoría de la noticia, Lista de distribución y SendTo de los formularios.
Volvemos a modo diseño pulsando en el icono  , que nos aparece en la barra de la izquierda en Lotus notes.
Pulsamos en la lista de elementos de diseño Views:
Creamos una nueva vista pulsando en el botón, .
Vista para la categoría de la noticia:
Con nombre: Entre paréntesis (VCategorias), los paréntesis indican que se trata de una vista oculta y no se verá desde el cliente notes.
Al crear la vista vemos que por defecto tiene el mismo diseño que la vista “Por Autor” que es la que hemos señalado como predeterminada en la base de datos.
Para eliminar estas columnas, nos situamos encima y pulsamos la tecla Supr.
Fórmula de selección: SELECT form="FNoticia", ya que lo que queremos es que nos muestre todas las categorías de los documentos creados con el formulario “FNoticia”.
Esta vista va a tener 1 columna:
En la ordenación de la columna, seleccionamos Order: ascendente y en Type marcamos Standard.
En Fórmula de columna, seleccionamos Field y elegimos el campo dlgCategoria.
Como fórmula de columna le ponemos el campo.
Guardamos la vista pulsando sobre el SmartIcon  y la cerramos.






*Vista Oculta para la lista de distribución:

Con nombre: Entre paréntesis (VLista).
Alias: VLista.
Fórmula de selección: SELECT form="FLista".
Esta vista va a tener 2 columnas:
Nos quedamos con dos columnas, de tipo Standard y ordenadas de forma ascendente.
En Fórmula de columna, seleccionamos Field y elegimos el campo, tNombre. En la ordenación seleccionamos Order: ascendente y en Type marcamos Standard.
En Fórmula de columna, seleccionamos Field y elegimos el campo, tMiembros. En la ordenación seleccionamos Order: ascendente y en Type marcamos Standard.
De esta vista vamos a recuperar los valores de los campos “Lista de distribución” y “Enviar a:” en los documentos creados con el formulario FNoticia.


*Recuperar valores de una vista en un campo de un formulario.
Para recuperar los valores de las vistas ocultas que hemos creado en los campos de los formularios, hacemos doble click sobre el formulario, 1.0.- Formulario Noticia, para abrirlo.


Campo dlgCategoria:
Nos situamos en el campo dlgCategoria, hacemos doble click sobre él para que nos aparezcan sus propiedades, nos aseguramos que es un campo de tipo Dialog List y Editable,
Abrimos la segunda pestaña de propiedades del campo, vamos a cambiar las opciones, en vez de escribir uno a uno los valores de este campo, como se ve en la Figura 5.14.1, los vamos a calcular en base a una fórmula.


*(Calcular los valores en base a una fórmula)
Desplegamos la lista de opciones, y seleccionamos, Use formula for choices, y en el cuadro de texto Choices escribimos
la siguiente fórmula: @Unique(@DbColumn("";"";"(VCategorias)";1)).
Con esta fórmula recogemos los valores que haya en la primera columna de la vista privada “(VCategorias)”.
La función @Unique nos sirve para que no se repitan valores, en el caso de que haya más de un documento con la misma categoría. 
Allow values not in list (Permitir valores que no estén en la lista), nos permitirá seleccionar un valor de los ya existentes en la lista o incluir uno nuevo.



*(Seleccionando el tipo de campo)

Guardamos el Formulario pulsando sobre el SmartIcon  y vamos a comprobar como en este campo se muestran los valores que tengamos en el campo categoría del resto de documentos.
Pulsamos en el Menú Design / Preview in Note

Abrimos de nuevo Lotus Designer y el formulario 1.0.- Formulario Noticia.
El Campo dlgLista:
Ahora vamos a cambiar la fórmula del campo dlgLista, nos situamos en el y hacemos doble Click para ver sus propiedades, nos aseguramos de que es un campo de tipo Dialog List y Editable.
Hacemos Click en la segunda pestaña de propiedades del campo, vamos a cambiar las opciones, igual que en el campo categoría de la noticia, vamos a calcular los valores en base a una fórmula.
Desplegamos la lista de opciones, y seleccionamos, Use formula for choices, y en el cuadro de texto Choices escribimos 
la siguiente fórmula: @Unique(@DbColumn("";"";"(VLista)";1)).



El Campo SendTo:
En este campo se va a calcular la lista de personas que se hayan incluido en la opción seleccionada en el campo, dlgLista.
Hacemos doble click en el campo, cambiamos en la primera pestaña el tipo de campo y lo ponemos de Texto – Computed (calculado) y señalamos la opción, Allow multiple values(Permitir varios valores), en el panel de 
fórmula ponemos la siguiente: @Unique(@DbLookup("";"";"(vListaDistribucion)";dlglista;2)), nos quedará de la siguiente forma:

Guardamos el Formulario pulsando sobre el SmartIcon  y vamos a probar como en el campo Lista de distribución nos sale la lista de valores que tengamos en los documentos creados con el formulario 2.0.- Lista de Distribución y que al seleccionar uno de estos valores nos calcula automáticamente el campo SendTo, con las personas que hayamos incluido en esa lista de distribución.
Pulsamos en el Menú Design / Preview in Notes.


*Función @Prompt
Esta función sirve para mostrar un cuadro de diálogo al usuario y da como resultado un valor de texto basándose en las acciones que el usuario realiza en dicho cuadro de diálogo.
@Prompt, resulta útil cuando se necesita pedir información al usuario y determinar las acciones a tomar basándose en los datos recogidos.


Para probar todas las opciones de esta función, vamos a crear un formulario nuevo con el nombre y el Alias Prompt y que tenga los siguientes campos:
Nombre Campo	Tipo	Valor por Defecto
Titulo	Texto-Editable	@Name([CN];@UserName)
Mensaje	Texto-Editable	“Mensaje”
Lista	Texto-Editable- Allow multiple values	"rojo;azul;blanco"
tResultado	Texto-Editable	“”


Vamos a crear unos botones para mostrar los diferentes cuadros de diálogo existentes:
Para crear un botón, pulsamos en el menú Create / Hotspot / Button,

Creamos 9 botones con los siguientes nombres y las siguientes fórmulas:
Nombre del botón	Fórmula
YesNo	FIELD tResultado:=@Prompt([YesNo];Ttitulo;Mensaje);@True
YesNoCancel	FIELD tResultado:=@Prompt([YesNoCancel];ttitulo; Mensaje);@True
OkCancelEdit	FIELD tResultado:=@Prompt([OkCancelEdit];ttitulo; Mensaje;"");@True
OkCancelList	FIELD tResultado:=@Prompt([OkCancelList];ttitulo;Mensaje;"color";tlista);@True
OkCancelCombo	FIELD tResultado:=@Prompt([OkCancelCombo];ttitulo;Mensaje;"color";tlista);@True
OkCancelListMult	FIELD tResultado:=@Prompt([OkCancelListMult];ttitulo;Mensaje;"color";tlista);@True
Password	FIELD tResultado:=@Prompt([Password];ttitulo;Mensaje);@True
Choosedatabase	FIELD tResultado:=@Prompt([ChooseDatabase];"";"");@True
Localbrowse	FIELD tResultado:=@Prompt([LocalBrowse];ttitulo;"1");@True



*Recursos compartidos / Imágenes

La creación de recursos de imágenes resulta especialmente útil para almacenar las imágenes que se usan en la base de datos. Aunque existen otros métodos para utilizar imágenes, de esta forma se mantiene la imagen en una única ubicación. De forma que si se
realiza cualquier tipo de modificación en una imagen, los cambios se aplican en todos los sitios donde se encuentre.

Para crear un recurso de imagen, nos situamos en la lista de elementos de diseño, Shared Resources /Images y pulsamos en el botón,
Se abre el cuadro de diálogo con el explorador de Windows, seleccionamos una o varias imágenes gif, bmp o jpeg de la lista y pulsamos en Abrir.
Se creará una entrada para cada uno de los archivos que se hayan seleccionado y ya podremos insertarlos en formularios, páginas, etc.
Para insertar una imagen en el resto de elementos de diseño seleccionamos en el menú Create / Image Resource.


*Navegadores
Vamos a crear un navegador para que al abrir la base de datos nos aparezca en la parte izquierda y no se vea el panel de vistas.
Nos situamos en la lista de elementos de diseño, Other / Navigators y pulsamos en el botón, 
Le ponemos el Nombre: 1.0.-Principal
Indicamos una vista predeterminada, en la opción Inicial view or fólder, seleccionamos la vista llamada 1.0.-Noticias Por Autor.
Vamos a personalizar el navegador poniéndole una imagen de fondo, antes tenemos que abrir con cualquier programa de tratamiento de imágenes como el Paint una imagen, seleccionarla y copiarla en el portapapeles, 
después volveremos a nuestro nuevo navegador y pulsamos en el menú Create / Graphic Background,


*(Insertando una imagen de fondo)
Create / Text 
Creamos una tabla con 1 columna y 5 filas, en cada fila insertaremos un enlace de texto.
Creamos 5 textos (Ver Figura 5.17.1) 
Por Autor
Por Fecha
Por Categoría
Lista de distribución
SALIR, acción que al pulsar nos cierre la base de datos

Al crear cada uno de los textos nos muestra las propiedades del mismo 


*(Propiedades del texto en un navegador)
En el cuadro de texto Caption, escribimos el título del enlace de texto.
En las propiedades, personalizamos el tipo de letra, el color por defecto, el color al pasar con el ratón por encima y el color al quedar seleccionado el enlace de texto.
En el panel de programación le indicaremos a cada uno de los enlaces, la vista que tiene que abrirnos de la siguiente forma:
Para los 4 primeros enlaces, seleccionamos Simple action(s)Open a View or FólderSeleccionamos la vista que queremos abrir de las que tenemos creadas.

Simple action(s) /Open a View or Fólder/ Vista a selecionar 


*(Asignando acciones a los enlaces de texto)
En el caso del enlace SALIR, seleccionamos en RunFórmula y en el panel de programación escribimos, @command([fileCloseWindow])
Guardamos el navegador pulsando sobre el SmartIcon .



*Frameset para el Cliente Notes
El Frameset estará compuesto por 2 marcos:
El Izquierdo contendrá el nuevo navegador que hemos creado y en el derecho se visualizará la vista que seleccionemos desde los enlaces de texto del navegador
Para crear un Frameset nuevo, nos situamos en la vista de elementos de diseño, Frameset, y pulsamos sobre el botón, .
La pantalla que nos aparece es la siguiente:
En esta pantalla podemos seleccionar el número y el orden de los marcos que tendrá el Frameset, aunque lo que se elija aquí no será definitivo, ya que, dentro del Frameset también podremos configurar estas opciones.
Para nuestra aplicación seleccionaremos la primera opción en Arrangement y el Number of frames será 2.
Al pulsar en el Botón OK, nos aparecerá la siguiente pantalla:En Name pondremos: 1.0.-Principal
En Alias: Principal
En Title:”Gestor de Noticias”, este es el título que mostrará en la ventana al abrir el FrameSet en Lotus Notes.
Ya hemos configurado las propiedades del FrameSet, ahora vamos a configurar las propiedades de cada uno de los marcos.
Nos situamos en uno de los marcos y pulsamos sobre el con el botón derecho del ratón.

*(Seleccionando las propiedades de un marco)
Las propiedades del marco Izquierdo son, (Ver Figura 5.17.3)
Name: Izquierdo
Type: Name Element-Navigator
Value: 1.0.-Principal, lo seleccionamos pulsando sobre la imagen, .
Default target for links in frame: Derecho, queremos que el contenido de los enlaces de texto de nuestro navegador nos los muestre en el marco derecho.


*(Propiedades del marco Derecho)
Las propiedades del marco Derecho son,
Name: Izquierdo
Type: Name Element-View
Value: 1.0.-Noticias por Autor, seleccionamos esta vista pulsando en la imagen, .
*(Cambiar a las propiedades de la base de datos)

*Cambiar la opción Al abrir la base de datos para el cliente Notes
Ya hemos creado el FrameSet, ahora vamos a configurar la base de datos para que al abrirla nos lo muestre.
Nos situamos en cualquier parte del conjunto de marcos que tenemos abierto y pulsamos sobre el SmartIcon , nos muestra las propiedades del FrameSet, elegimos que nos muestre las propiedades de la Database, en el desplegable que muestra el triangulo blanco




*(Cambiando las Propiedades de la base de datos)
En las propiedades de la base de datos, en la quinta pestaña, cambiamos las siguientes opciones, (Ver Figura 5.19.1).
When Opened in the Notes Client, seleccionamos, Open designated FrameSet
Name: Seleccionamos nuestro Frameset: 1.0.-Principal
Abrimos la base de datos en Lotus Notes para probar como nos muestra el FrameSet seleccionado.
Nos debe aparecer el conjunto de marcos:



*Esquemas
Vamos a preparar nuestra aplicación para que se pueda ver en cualquier navegador Web, para ello crearemos algunos elementos de diseño entre los que se encuentran los OutLines.
Para crear un OutLine, nos situamos en la lista de elementos de diseño y seleccionamos Asare Code / Out linees y pulsamos en el botón,.
Los Out linees están compuestos por entradas, las cuales actúan como los enlaces de texto de los navegadores

*Podemos incluir las entradas del OutLine una a una o pulsar en este botón, para generar un Outline con todas las vistas que tenemos en la base de datos. El resultado lo podemos ver en la siguiente Figura:



Eliminamos las entradas que no nos interese Mostar, situándonos encima y pulsando la tecla Supr. y nos quedamos únicamente con las de las vistas de por autor, por fecha, por categoría y lista de distribución.

*(Cambiando las Propiedades de una entrada de Outline)
El título de cada una de las entradas por defecto es el nombre de la vista, vamos a cambiarle el título para mejorar el aspecto, hacemos doble click sobre cada una de ellas y nos aparecerán sus propiedades.

En todas cambiaremos en el cuadro de texto Label el nombre, poniéndole uno identificativo, por ejemplo, en la primera entrada le pondremos, Por Autor.

En Content/ Type, elegimos Named ElementView, y pulsando sobre el icono, , seleccionamos la vista que queremos abrir.
Y así con todas las entradas de este nuevo OutLine.


Una vez que tengamos personalizadas todas las entradas del OutLine, vamos a configurar el propio OutLine, para ver las propiedades del mismo, nos situamos en cualquier parte del OutLine y pulsamos en el SmartIcon , que nos mostrará la siguiente pantalla:
En Name le ponemos: 1.0.-Principal.
En Alias: Principal.
Guardamos el Outline pulsando sobre el SmartIcon .


*Páginas

Un OutLine no se puede incluir en un conjunto de marcos por si sólo, para poder visualizarlos es necesario incluirlo en una página o en un formulario, nosotros lo incluiremos en una página.
Para crear una nueva página, nos situamos en la lista de elementos de diseño, seleccionamos Pages y pulsamos en el botón, .
Pulsamos en el SmartIcon , para ver sus propiedades 


*(Accediendo a las Propiedades de una Página)
En Name ponemos: 1.0.-Principal | Principal
Separando el nombre y el alias por el carácter “|”.
Si nuestra página tuvieses código HTML seleccionaríamos Web access/ Content type / HTML, esta página va a contener un OutLine con lo cuál no es necesario seleccionar esta propiedad.

Nos situamos en cualquier parte de la página donde queramos situar el OutLine y pulsamos sobre el Menú Create / Embedded Element / Outline, 

Nos aparece la siguiente pantalla, en ella elegimos el Outline que hemos creado y pulsamos en el botón OK:
Nos situamos encima del Outline que hemos insertado y pulsamos sobre el SmartIcon , , para ver sus propiedades, (Embedded Outlet)

(Propiedades del OutLine insertado)
Ajustamos en OutLine size, Width (anchura) y Height (altura).
En Web Access seleccionamos Using HTML, otra opción es elegir Using Java applet, podéis probarlo con esta opción, pero la página tardará mucho más en cargarse.
En el resto de pestañas se puede configurar el tipo de letra, ponerle una imagen de fondo a cada entrada, establecer los márgenes, el estilo de los bordes y establecer fórmulas de ocultación como en el resto de elementos de diseño, una cosa a tener en cuenta, es que existen diferentes niveles en el esquema, cada uno de los cuales se puede personalizar.
Una vez se acabemos la personalización del Outline y de la página, guardamos la página pulsando sobre el SmartIcon .



*Hojas de estilo
Hojas de estilo
Las hojas de estilo para las aplicaciones Web en Lotus se suelen crear en una página y así lo vamos a hacer, 
Creamos una página nueva, que tenga el Nombre y el Alias: estilos.css | estilos.css.
Vamos a copiar este código HTML y a pegarlo en nuestra nueva página:
Una vez tengamos el código pegado en la página, lo seleccionamos todo, pulsando en el menú, Edit /Select All o en la combinación de teclas ctrl.+A y lo convertimos en código HTML pulsando en el menú, Text / Pass-Thru HTML.

Por supuesto, este código HTML, es un ejemplo, se pueden crear todas las etiquetas nuevas que queramos.
Guardamos la página pulsando sobre el SmartIcon .
En los siguientes capítulos veremos como incluir esta página de estilos y sus etiquetas en los restantes elementos de diseño.


*Agentes
Necesitamos dos agentes, que se ejecutarán desde dos acciones de las vistas, con los cuales cambiaremos el valor del campo rdWeb del formulario noticias.
Los nombres de estos agentes serán: Subir a Web y Dar de baja en Web
Para crear un Agente nuevo, nos situamos en la vista de elementos de diseño, Shared / Agent, y pulsamos en el botón, .
Nos aparecen automáticamente las propiedades del agente, vamos a configurarlo como en la siguiente pantalla:


Abajo del panel de programación, nos aparece el botón,"Add Action" , lo pulsamos y accedemos a la programación del agente.
Seleccionamos Modify Field como aparece en esta pantalla:


En Modify by, seleccionamos Replacing, en The value in field, seleccionamos el campo rdWeb y como nuevo valor le ponemos “Si”, como aparece en la siguiente pantalla:
Pulsamos el botón Replace y ya tenemos creado nuestro agente de Subir a Web.
Creamos el agente Dar de baja en Web de la misma manera, pero en vez de poner el valor “Si” en el campo rdWeb, ponemos el valor “No”.


*Los siguientes puntos nos indican la forma de acceder y ejecutar estos agentes.
Cómo ejecutar los agentes:
*Creamos dos acciones compartidas, con los nombres, Subir a Web y Dar de baja en Web.

En Run, seleccionamos Simple action(s), pulsamos en el botón,"Edit action" , que aparece en la parte inferior de la pantalla y en las opciones que se muestran, elegimos Run Agent y el agente que corresponda ejecutar a cada acción,


Guardamos las acciones compartidas pulsando sobre el SmartIcon

Insertamos las acciones compartidas en las vistas de noticias que tenemos creadas.
Abrimos la base de datos en Lotus notes y probamos que realmente, seleccionando varios documentos, se cambia el campo rdWeb en todos ellos a “Si” o “No”, dependiendo de la acción que hayamos seleccionado.


*Formulario para visualizar las noticias en Web
Creamos un nuevo formulario con un nombre diferente, por ejemplo:” 1.1.-FormularioNoticiasWeb”, pero con el mismo Alias que el formulario noticias: “FNoticias”.
*Incluimos los mismos campos que en el formulario principal de noticias y le vamos a añadir algunas fórmulas para los navegadores como la validación de campos.
$$Return: Creamos un campo de tipo texto y calculado al visualizar con la siguiente fórmula:"[/"+@WebDbName+"/todos/"+@Text(@DocumentUniqueID)+"?opendocument]", cuando guardemos un documento en Web, nos mostrará el mismo documento en modo lectura, lo normal es ocultar este campo en todos los navegadores.
*Evento JS Header:
En este evento del formulario, vamos a añadir un código JavaScript que nos compruebe que en el campo Título de la noticia se ha incluido algún valor antes de guardar el documento
En el panel de fórmulas del JS Header le ponemos el siguiente código:
function validar(){
var f = document.forms[0] 
if (f.Titulo.value == "") {
alert ("Por favor, introduzca el título");
f.Titulo.focus();
return false;
}
;f.submit()}



*(Ocultando una acción compartida para Web Browsers)
*Cómo hacer una llamada a la función validar del evento JS Header:
Vamos a llamar a la función Validar desde una acción Guardar nueva, pero antes tenemos que ocultar sólo para Web la que ya teníamos.
Nos situamos en la lista de elementos de diseño, Shared Code / Actions
Hacemos doble click sobre la acción Guardar y la ocultamos para Web 

*(Navegando por las pestañas superiores)
Volvemos al formulario de noticias para Web que estábamos personalizando, navegando a través de las pestañas superiores,


Al haber ocultado la acción Guardar para Web browser, necesitamos una nueva para el formulario de noticias que se va a visualizar en Web.
Creamos una acción nueva en el panel de acciones de este formulario que se va a llamar Guardar, le ponemos un icono identificativo y en el panel de fórmulas vamos a elegir Run JavaScript y como código: validar().



De esta forma cuando creemos un nuevo documento noticia en Web y pulsemos en la acción Guardar, antes de guardar el documento comprobará que el campo se cumplen todas las condiciones que se indican el la función validar que hemos incluido en el evento JS Header.


Objects / Evento HTML Body Attributes:
Con el siguiente Código HTML: "bgcolor=#FFFFFF text=#000000 leftmargin=3 topmargin=3 marginwidth=3 marginheight=3", establecemos un color de fondo y de texto predeterminado para los documentos creados con este formulario.
Los márgenes a los que queremos ajustar los documentos en la ventana del navegador, se definen en Internet Explorer con leftmargin y topmargin y con marginwidth y marginHeight en Netscape navigator
Guardamos el formulario pulsando sobre el SmartIcon  y nos situamos en la vista de elementos de diseño Forms.

Situándonos sobre el formulario 1.1.-Formulario NoticiasW y pulsando con el botón derecho del ratón podemos acceder a las propiedades de este elemento de diseño, pulsando en el menú que aparece Design Properties

*La pantalla que nos aparece es como la siguiente:
Lo ocultamos para Notes y Mobile clients.
Hacemos los mismo con el formulario 1.0.-Formulario Noticia, pero este lo ocultamos para Web browsers y para Mobile clients
Con estas ocultaciones conseguimos que cuando se abra un documento en el cliente Lotus notes utilice el formulario 1.0.-Formulario Noticia y que cuando se abra un documento en el cliente Web utilice el formulario 1.1.-Formulario NoticiaW.
De esta forma podemos tener un diseño diferente, dependiendo del entorno en el que utilice la aplicación.


* Formulario para visualizar las vistas
* Creamos un nuevo formulario cuyo Nombre y Alias sea 3.0.- Formulario Vista | $$ViewTemplateDefault.
* Este formulario será el formulario por defecto en el que se muestren todas las vistas en Web.




* Authors	Los campos de lectores y autores permiten controlar quién puede leer y crear los documentos que se generan a partir de un formulario.
Checkbox	Cada opción aparece junto a una casilla de verificación.
Color	Muestra la paleta de colores donde se puede seleccionar uno.
Combobox	Las opciones aparecen dentro de un cuadro de lista desplegable.
Date/Time	Para introducir fechas y las horas.
Dialog List	Para ver todas las opciones a la vez sin tener que desplegar la lista de valores.
Formula	Los campos de fórmulas se utilizan para rellenar listas de suscripción.
Listbox	Se muestra una lista de opciones para que los usuarios puedan seleccionar la que más les interesa.
Names	Cree un campo de nombres para mostrar los nombres de usuarios. Un campo de este tipo puede ser calculado o editable y se le suele asociar la fórmula: @UserName, el nombre se mostrará tal y como aparece en los ID de Notes: por ejemplo, Juan Sánchez/Brossoft.
Para mostrar únicamente el "nombre común", sin el “/Brossoft “ se le asigna la siguiente fórmula: @Name([CN];@UserName)
Number	Para introducir datos numéricos o monetarios.
Password	Campos de texto que al escribir la contraseña cada carácter que introduce el usuario se muestra como un asterisco en la pantalla.
Radio button	Cada opción aparece junto a un botón, el usuario sólo puede seleccionar uno.
Readers	Los campos de lectores y autores le permiten controlar quién puede leer y crear los documentos que se generan a partir de un formulario
Rich text	Para introducir imágenes, anexos y objetos.
Text	Para introducir, almacenar y visualizar texto.
Rich text lite	Campo de texto enriquecido pero con una lista de elementos enumerados en un menú desplegable que son los únicos elementos que se permite al usuario insertar en este tipo de campo.
Time Zone	Muestra una lista con todas las zonas horarias del mundo.

