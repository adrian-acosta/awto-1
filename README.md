# awto
Awto
* Se realiza script en Selenium WD en lenguaje JAVA.
* El proyecto es creado en un tipo de proyecto Maven
* Se utiliza cucumber como framework de pruebas para la creación de test usando lenguaje Gherkin

## Patron de Diseño Empleado Page Object Model.

Se utilizó un patrón de diseño Page Object Model para estructurar y organizar el sitio

El modelado se hizo externamente en el archivo Excel de nombre PageObject.xlsx

![POM](https://user-images.githubusercontent.com/61878768/76101474-b92c4300-5f8b-11ea-8c99-3c5f2b026c57.png)

el cual se encuentra en la ruta: src/main/java/resources/PageObjectModel/PageObject.xlsx

![excelPage](https://user-images.githubusercontent.com/61878768/76101282-6b173f80-5f8b-11ea-8ee4-d6767d1d57bf.png)

Se aplicó ATLC en todas sus etapas.
Se crearon pasos reutilizables y genericos

El modelado al estar externo al proyecto(PageObject.xlsx) es manejable para poder agregar más páginas dado caso el sitio crezca sin necesidad de crear más código dentro del proyecto en cuanto al modelado, además los objetos igualmente se encuentran en el excel por lo que no es necesario agregar más código para poder interactuar con otros elementos nuevos, en caso de que los existentes cambien, solo se actualiza desde el excel y no hace falta modificar código en cuanto a elementos.

## Reportes.

Se crea un reporte nativo en html para poder visualizar en el navegador los resultados(ademas de la consola de ejecución)
Se crea un log de ejecución que se va visualizando en consola y al final se crea un archivo en: awt/log que se puede visualizar durante la ejecución y en el directorio log.

![log](https://user-images.githubusercontent.com/61878768/76101779-348df480-5f8c-11ea-99ad-47998009cc63.png)

![reportehtml1](https://user-images.githubusercontent.com/61878768/76102651-8a16d100-5f8d-11ea-898e-203ac4751736.png)

![reportehtml](https://user-images.githubusercontent.com/61878768/76102740-b03c7100-5f8d-11ea-963c-c744e3a48ce9.png)


Nota:
Se debe de eliminar el log después de la ejecucón.


## Screenshots

Se crean imagenes de la ejecución en caso de necesitar visualizar y tener evidencia de las pruebas.
Se pueden visualizar en: src/main/resources/screenShots

![screenshot](https://user-images.githubusercontent.com/61878768/76101892-5f784880-5f8c-11ea-9b53-c419053ca945.png)


Se debe de modificar el archivo properpies.info el cual la ruta se debe de actualizar segun el directorio raiz dónde se coloque el proyecto.

![properties](https://user-images.githubusercontent.com/61878768/76102012-92224100-5f8c-11ea-959d-5099e3e166e0.png)

La linea de código es:
SCREENSHOTPAHT=D:\\Proyectos\\awt\\src\\main\\resources\\screenShots

Nota:
Se deben de eliminar después de la ejecucón si no son necesarias.

## Driver para ejecución sobre Chrome.

Se agrega al proyecto el driver de ejecución, el cual la ruta se debe de actualizar segun el directorio raiz dónde se coloque el proyecto.

La clase a modificar es Hooks.java la cual se encuentra en: src/main/java/stepsDefinition/Hooks.java

La linea a modificar es:
        System.setProperty("webdriver.chrome.driver","D:\\Proyectos\\awt\\src\\main\\resources\\driver\\chromedriver.exe");


## Archivos Autoit

Se tuvo la necesidad de utilizar autoit para automatizar el flujo de subir archivos de imagen.
Se creó un script en autoit de nombre UploadFile.au3 el cual contiene el código para detectar la ventana de windows del explorar que se muestra al hacer click sobre el link "subir imagen"(licencias y carnet), luego se paso a compilar y crear el UploadFile.exe que es el que se manda llamar en el paso "Cargar archivo" en el caso de prueba .feature.



![autoitscreen](https://user-images.githubusercontent.com/61878768/76102103-b9790e00-5f8c-11ea-8060-9de8a08b17b1.png)

Código dentro del archivo UploadFile.au3:

ControlFocus("Abrir","","Edit1")
ControlSetText("Abrir","","Edit1","D:\Proyectos\awt\src\test\resources\images\carnetFrontal.png")
ControlClick("Abrir","","Button1")

Por lo que abria que editar el archivo a otra ruta dado caso no se encuentre la unidad D: para tener el mismo path.
Otro punto importante a tener en cuenta es el parámetro "Abrir" ya que se utilizó el google chorome en español, éste parámetro igualmente deberia de cambiar dado caso el navegador este en inglés.

Para esto es necesario tener Autoit instalado.

Nota:
Se tuvo que utilizar Autoit para cargar archivos ya que la clase Robot que se utiliza normalmente tenia un comportamiento inadecuado y fallaba al cargar los archivos cuando es más de uno, por lo que se busco otra opción dando lugar a autoit.


Para descargar autoit: https://www.autoitscript.com/site/autoit/downloads/

cualquier duda favor de mandar mail a jesus.acosta.solis@gmail.com

## Ejecución del Script

Para que pueda ser ejecutado sin problema el tc_001_RegistrarNuevoUsuario.feature se debe de cambiar el valor del correo en el paso:
 Y El usuario captura en el campo email el valor jesus156@jesus.com por uno que no este registrado en el sistema.
 
 ![paso](https://user-images.githubusercontent.com/61878768/76103324-be3ec180-5f8e-11ea-9dc4-8249e90c17aa.png)
 
 
 
 El tc_002_VerificarUsuarioExistenteNoSePuedaRegistrar.feature el mismo valor es un dato de un usuario ya registrado y el objetivo es que valide que no pueda registrarse, por lo que no es necesario cambiarlo dado caso.


