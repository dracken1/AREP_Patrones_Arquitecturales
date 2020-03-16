# AREP_Patrones_Arquitecturales

## 1. Desplegar un sitio estático usando S3

  ### Crear un Bucket S3 de Amazon usandos la consola de AWS.
  
  1.  Abrir la consola de Amazon S3 en https://console.aws.amazon.com/s3/  
  
  2.  En la consola, elegir **Crear bucket**.
  
  3.  Se abrira un formulario, para practicidad solo es necesario llenar el nombre del Bucket, puede ignorar todo lo demas, ya que las configuracion por defecto son suficientes, no es necesario cambiarlas. De **siquiente** y al final de click en **Crear bucket**.
  
  4.  El bucket se creara, de click sobre el nombre del bucket que acaba de crear, se abrira un overview del bucket, aqui podra cargar los archivos que necesite, en este caso un html. De click en **cargar**, se abrira una nueva pestaña, arrastre y suelte el archivo html, de click en **siguiente** hasta llegar a la pestaña de **Revision**, puede ignorar los permisos y las propiedades, lo que esta definido por defecto es suficiente. Por ultimo de click en **Cargar**, su archivo se cargara y lo podra ver en el overview de su bucket.
  
## 2. Desplegar un formulario dinámico usando EC2

  ### Lo primero es crear la instancia de EC2
  
  ### Paso 1: configurar e iniciar sesión en su cuenta de AWS
  Inicie sesión en la consola de administración de AWS y configure su cuenta raíz.
  ### Paso 2: Lanzar una instancia de Amazon EC2
  En el panel de Amazon EC2, haga clic en "Launch Instance" (Lanzar instancia) para crear y configurar la máquina virtual.

  ### Paso 3: Configurar su instancia
  En este asistente tiene la opción de configurar las características de su instancia. A continuación se incluyen algunas instrucciones para configurar la primera instancia.

  Seleccione una imagen de máquina de Amazon (AMI): en el paso 1 del asistente, recomendamos la AMI de Amazon Linux 2 (compatible con la capa gratuita).
  Seleccione un tipo de instancia: en el paso 2 del asistente, recomendamos la t2.micro (compatible con la capa gratuita).
  Grupo de seguridad: en el paso 6, tiene la opción de configurar su firewall virtual.
  Implemente la instancia: en el paso 7, revise la configuración de su instancia y seleccione "Launch" (Iniciar).
  Cree un par de claves: seleccione Create a new key pair (Crear nuevo par de claves) y asígnele un nombre. El archivo del par de claves (.pem) se descargará automáticamente. Guárdelo en un lugar seguro, ya que lo utilizaremos posteriormente para iniciar sesión en la instancia. Por último, haga clic en "Launch Instances" (Iniciar instancias) para finalizar el proceso de configuración.
  Nota: El inicio de la instancia puede demorar unos minutos.

  ### Paso 4: conectarse a la instancia
  Una vez lanzada la instancia, puede conectarse a ella y utilizarla como lo haría con cualquier equipo que tuviera delante. Para conectarse desde la consola, siga los pasos que se detallan a continuación:

  Seleccione la instancia EC2 que creó y haga clic en "Connect" (Conectar).
  Seleccione "A Java SSH client directly from my browser" (Un cliente SSH de Java directamente desde mi navegador). Asegúrese de que Java esté instalado y habilitado.
  Introduzca la ruta de la clave privada (como por ejemplo: C:\KeyPairs\my-key-pair.pem).
  Seleccione "Launch SSH Client" (Iniciar cliente SSH).
  Nota: También puede conectarse a través de SSH o PuTTY; haga clic aquí para obtener más información.

  ### Paso 5: terminar instancias
  Si bien puede empezar a utilizar Amazon EC2 de manera gratuita (más información), debe terminar las instancias para evitar que se apliquen cargos adicionales. La instancia EC2 y los datos asociados se eliminarán.

  Seleccione la instancia EC2, elija "Actions" (Acciones), seleccione "Instance State" (Estado de la instancia) y "Terminate" (Terminar).

## 3. Enlazar el formulario a una base de datos relacional o no-relacional, para almacenar y traer los datos almacenados. Use servicios de base de datos de AWS.

## 4. Configurar un VPC para gestionar la seguridad y los permisos de acceso a sus servidores.
