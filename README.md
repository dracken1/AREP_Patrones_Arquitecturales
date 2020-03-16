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
  Nota: También puede conectarse a través de SSH o PuTTY;

  ### Paso 5: terminar instancias
  Si bien puede empezar a utilizar Amazon EC2 de manera gratuita, debe terminar las instancias para evitar que se apliquen cargos adicionales. La instancia EC2 y los datos asociados se eliminarán.

  Seleccione la instancia EC2, elija "Actions" (Acciones), seleccione "Instance State" (Estado de la instancia) y "Terminate" (Terminar).
  
  ### Desplegar el formulario
  
  Teniendo una coneccion con la maquina, la forma mas sencilla de agregar el proyecto donde se encuentra el formulario para posteriormente poder desplegarlo, es usando github.
  Lo que se debe hacer es clonar el repositorio del proyecto en la maquina usando el comando de github
  
  ´´´
  git clone nombrerepositorio
  ´´´
  
  Una vez que el proyecto se encuentra dentro de la maquina, lo unico que debe hacer es compilarlo/instalarlo y luego ponerlo a correr.
  Ya sea que este usando Proyecto creado con React, Spring, Spark, etc. Lo unico que cambia son los comandos para poner a correr el proyecto.(Debe asegurarse que la maquina tenga instalado todo lo necesario)
  Para el caso de Spring y si construyo el proyecto usando maven, dentro de la carpeta del proyecto, use los siguientes comandos
  
  ´´´
  mvn package
  
  mvn spring-boot:run
  ´´´
  Esto pondra a correr el proyecto con el formulario adentro, ahora solo debe verificar que el formulario sea accesible, para esto solo debe acceder al navegador de su computador(no la instancia de EC2) y buscar ´´´ipmaquina:8080´´´ donde ipmaquina es la ip de la instancia de EC2. Si la construccion del formulario es correcta, este deberia poderse ver desde el navegador.
  
## 3. Enlazar el formulario a una base de datos relacional o no-relacional, para almacenar y traer los datos almacenados. Use servicios de base de datos de AWS.

  ### Lo primero es crear la base de datos
  
  1.  Inicie sesión en la Consola de administración de AWS y abra la consola de Amazon RDS en https://console.aws.amazon.com/rds/.

  2.  En la esquina superior derecha de la consola de Amazon RDS, elija la región de AWS en la que desea crear la instancia de base de datos.

  3.  En el panel de navegación, seleccione Databases (Bases de datos).

  4.  Seleccione Create database (Crear base de datos) y asegúrese de que la opción Easy Create (Creación sencilla) esté seleccionada.
  5.  En Configuration (Configuración), seleccione PostgreSQL.

  6.  En DB instance size (Tamaño de la instancia de base de datos), seleccione Free tier (Capa gratuita).

  7.  En DB instance identifier (Identificador de instancias de base de datos), introduzca un nombre para la instancia de base de datos o deje el nombre predeterminado.

  8.  En Master username (Nombre de usuario maestro), introduzca un nombre para el usuario maestro o deje el nombre predeterminado.

  9.  La página Create database (Crear base de datos) debe ser similar a la siguiente imagen:
  
  ![Images](https://docs.aws.amazon.com/es_es/AmazonRDS/latest/UserGuide/images/easy-create-postgresql.png)
  
  10. Elija Create database (Crear base de datos). Si decide utilizar una contraseña generada automáticamente, el botón View credential details (Ver detalles de credenciales) aparece en la página Databases (Bases de datos). Para consultar la contraseña y el nombre de usuario maestros de la instancia de base de datos, seleccione View credential details (Ver detalles de credenciales).
  
  11. En Databases (Bases de datos), seleccione el nombre de la nueva base de datos PostgreSQL. Los detalles de la nueva instancia de base de datos aparecen en la consola de RDS. La instancia de base de datos tendrá el estado creating hasta que esté lista para el uso. Cuando el estado cambie a available, podrá conectarse a la instancia de base de datos. Dependiendo de la clase de instancia de base de datos y de la cantidad de almacenamiento, es posible que la nueva instancia tarde hasta 20 minutos en estar disponible.

## 4. Configurar un VPC para gestionar la seguridad y los permisos de acceso a sus servidores.

  ### Para crear una VPC y las subredes

  Abra la consola de Amazon VPC en https://console.aws.amazon.com/vpc/.

  En la esquina superior derecha de la Consola de administración de AWS, elija la región en la que desea crear la VPC. En este ejemplo se utiliza la región EE.UU. Oeste (Oregón).

  En la esquina superior izquierda, elija VPC Dashboard. Para comenzar a crear una VPC, elija Launch VPC Wizard (Lanzar asistente de VPC).

  En la página Step 1: Select a VPC Configuration, elija VPC with Public and Private Subnets y, a continuación, elija Select.

  En la página Step 2: VPC with Public and Private Subnets, establezca estos valores:

  IPv4 CIDR block: 10.0.0.0/16

  IPv6 CIDR block: No IPv6 CIDR Block

  VPC name: tutorial-vpc

  Public subnet's IPv4 CIDR: 10.0.0.0/24

  Availability Zone: us-west-2a

  Public subnet name: Tutorial public

  Private subnet's IPv4 CIDR: 10.0.1.0/24

  Availability Zone: us-west-2a

  Private subnet name: Tutorial Private 1

  Instance type: t2.small

  ### importante
  Si no ve el cuadro Instance type (Tipo de instancia) en la consola, elija Use a NAT instance instead (Usar una instancia NAT). Este enlace está a la derecha.

  ### nota
  Si no aparece el tipo de instancia t2.small, puede elegir un tipo de instancia diferente.

  Key pair name: No key pair

  Service endpoints: omita este campo.

  Enable DNS hostnames: Yes

  Hardware tenancy: Default
