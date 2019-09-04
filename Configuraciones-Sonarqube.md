# Instalacion de Sonarquebe.
Para fines practicos utilizaremos la imagen docker de sonarqube ya que esta lista para utilizarse
sin ninguna instalacion alguna.
Paso:
 1. Instalacion de docker en ubuntu:
 - Agregar los repositorios de Docker a ubuntu.
 ```docker
$ sudo apt-get update
$ sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
$ sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
$ sudo apt-get update
$ sudo apt-get install docker-ce docker-ce-cli containerd.io
$ sudo groupadd docker
$ sudo usermod -aG docker $USER
```
*salir  y volver a entrar a la terminal
Correr un contenedor de prueba
```
$ docker run hello-world
```

2. Descargar la imagen de Sonarqube
```
$ docker pull sonarqube
```

3. Crear las siguientes carpetas para darle persistencia de datos al contenedor de Sonarqube.

```
$ mkdir -p ~/sonar/conf
$ mkdir -p ~/sonar/data
$ mkdir -p ~/sonar/logs
$ mkdir -p ~/sonar/extensions
$ chmod 777 -R ~/sonar
```
4. Correr el contenedor de Sonarquebe
```
$docker run -d --name sonarqube -p 5001:9000 -v ~/sonar/conf:/opt/sonarqube/conf 
-v ~/sonar/data:/opt/sonarqube/data -v ~/sonar/logs:/opt/sonarqube/logs -v ~/sonar/extensions:/opt/sonarqube/extens
ions sonarqube
```
*el parametro para -p n:9000; n tiene que ser un puerto de su maquina en donde el trafico tcp este habilitado

# Configuraciones que se hacen en Sonarqube.
- Generar Token para agregar servidor en jenkins.

![imagen1][logo]

[logo]: https://raw.githubusercontent.com/dragonbjgt/Laboratorio_AYD2/Confs-Sonnarqube/imagenes/Generacion-token-server.png "generacion token-server"

guardar el token generado por que servira para crear una credencial en jenkins.

- Instalar plugins en el marketplace segun los lenguajes que se analizaran en el server.
![imagen2][logo]

[logo]: https://raw.githubusercontent.com/dragonbjgt/Laboratorio_AYD2/Confs-Sonnarqube/imagenes/instalar-plugin-segun-lenguaje-a-analizar.png " instalar plugins en sonarqube"

- crear un proyecto nuevo.
![imagen3][logo]

[logo]: https://raw.githubusercontent.com/dragonbjgt/Laboratorio_AYD2/Confs-Sonnarqube/imagenes/crear-proyecto-nuevo.png "crear proyecto nuevo"

1. darle nombre a proyecto.
![imagen4][logo]

[logo]: https://raw.githubusercontent.com/dragonbjgt/Laboratorio_AYD2/Confs-Sonnarqube/imagenes/nombre-proyecto.png "nombre del proyecto"

2. generar token del proyecto y seguir el wizard hasta obtener el comando para conectar al proyecto desde el cliente.

![imagen5][logo]

[logo]: https://raw.githubusercontent.com/dragonbjgt/Laboratorio_AYD2/Confs-Sonnarqube/imagenes/configuracion-token-del-proyecto.png"token y comando para el proyecto"

- Crear webhook en el proyecto de sonarqube para comunicar el estado del analisis a jenkins.

![imagen6][logo]

[logo]: https://raw.githubusercontent.com/dragonbjgt/Laboratorio_AYD2/Confs-Sonnarqube/imagenes/crear-webhook-jenkins-sonar1.png"opcion de webhook en el proyecto"

![imagen7][logo]

[logo]: https://raw.githubusercontent.com/dragonbjgt/Laboratorio_AYD2/Confs-Sonnarqube/imagenes/webhook-sonar-jenkins-2.png"configurar webhook"


# Configuracion de Sonarqube en jenkins
### Las siguientes configuraciones las tendran que realizar en el servidor de jenkins.
```
```   