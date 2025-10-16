# Mapeo de puertos
El mapeo de puertos es un mecanismo que permite redirigir el tráfico de red desde un puerto en el host (tu máquina local o servidor) hacia un puerto específico en un contenedor Docker.
Por ejemplo, supongamos que tienes un contenedor que ejecuta un servidor web en el puerto 80 dentro del contenedor, pero quieres acceder a ese servidor desde tu navegador en la máquina host. Puedes usar el mapeo de puertos para redirigir el tráfico del puerto 80 del contenedor al puerto 3000 en el host. De esta manera, cuando accedas a http://localhost:3000 en tu navegador, el tráfico se dirigirá al servidor web dentro del contenedor en el puerto 80.

![mapeo](mapeoPuertos.PNG)

### Para crear un mapeo de puertos (puerto host y puerto contenedor)
El mapeo de puertos se especifica al ejecutar un contenedor Docker utilizando la opción -p o --publish seguida de los puertos que deseas mapear
```
docker run -d --name <nombre contenedor> -p <puerto host>:<puerto contenedor> <nombre imagen>:<tag>

```
Crear un contenedor a partir de la imagen nginx version alpine con el mapeo de puertos del ejemplo gráfico, host 3000 y contenedor 80
# COMPLETAR
```
docker run -d --name nginx -p 3000:80 nginx:alpine
```
```
C:\Windows\System32>docker run -d --name nginx -p 3000:80 nginx:alpine
aab6264cbf11429df49f96af6ee5c853508b7dfd854674cc40a7505d4f9c0089

```
# COLOCAR UNA CAPTURA DE PANTALLA  DEL ACCESO http://localhost:3000
<img width="929" height="313" alt="image" src="https://github.com/user-attachments/assets/1bcfcc5e-39d4-4060-bfee-8baeb5aad0cb" />

### Para mapear más de un puerto

```
docker run -d --name <nombre contenedor> -p <puerto host 01>:<puerto contenedor 01> -p <puerto host 02>:<puerto contenedor 02> <nombre imagen>:<tag>
```

Crear un contenedor a partir de la imagen rabbitmq version management-alpine, para este mapeo de puertos usar en el host los mismos puertos del contenedor.
# COMPLETAR
```
docker run -d --name rabbit -p 8080:8080 -p 5050:5050 rabbitmq:management-alpine
```
### Usando una forma más semántica cuando se especifican puertos

```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> <nombre imagen>:<tag> 
```
### Publicando todos los puertos
```
docker run -P -d --name <nombre contenedor> <nombre imagen>:<tag> 
```

-P: le indica a Docker que asigne automáticamente puertos aleatorios en tu host para todos los puertos expuestos por el contenedor.

**Recordar**
No puedes mapear puertos a un contenedor existente directamente después de su creación con Docker. El mapeo de puertos debe especificarse en el momento de crear y ejecutar el contenedor.

### Crear contenedor de Jenkins puertos contenedor: 8080 (interface web) y 50000 (comunicación entre nodos) imagen: jenkins/jenkins:alpine3.18-jdk11
# COMPLETAR
```
docker run -d --name jenkins_server -p 8080:8080 -p 50000:50000 jenkins/jenkins:alpine3.18-jdk11
```
```
C:\Windows\System32>docker run -d --name jenkins_server -p 8080:8080 -p 50000:50000 jenkins/jenkins:alpine3.18-jdk11
Unable to find image 'jenkins/jenkins:alpine3.18-jdk11' locally
alpine3.18-jdk11: Pulling from jenkins/jenkins
064a3e26f4c3: Pull complete
8034e9541195: Pull complete
8c8b33a11025: Pull complete
a97ebf1389b9: Pull complete
c4d0d28b6211: Pull complete
c926b61bad3b: Pull complete
12edf75a8110: Pull complete
0425be0277df: Pull complete
f53b573d02cc: Pull complete
1c5813922572: Pull complete
0f92a263615f: Pull complete
45f7db6458a9: Pull complete
Digest: sha256:3aeedd41d77f5f8284b77e7bfef5e10bcb3f57c57aa70a0034b90356300bb058
Status: Downloaded newer image for jenkins/jenkins:alpine3.18-jdk11
ab8ad7adb25fef92e389d8e3fa8badda7c48d0b7e7d9c3e62bf8c78c13a24355
```
# COLOCAR UNA CAPTURA DE PANTALLA  DEL ACCESO http://localhost:8080
<img width="926" height="526" alt="image" src="https://github.com/user-attachments/assets/68337162-1ab2-4902-9f20-a05b5ac25818" />

### ¿Cómo obtener la contraseña solicitada?
Para obtener la contraseña solicitada es necesario ingresar al contenedor.

![Imagen](jenkins.PNG)

