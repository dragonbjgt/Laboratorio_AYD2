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
- Generar Token para agregar servidor en jenkins
[diagrama][logo]

[logo]: https://github.com/byronjl2003/SA_Tarea2/blob/master/diagramas/solicitud-servicio.png?raw=true "solicitud de ube"

# Configuracion de Sonarqube en jenkins
### Las siguientes configuraciones las tendran que realizar en el servidor de jenkins.
```
```   