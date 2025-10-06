# Contenedores

### Crear un contenedor
Para crear un nuevo contenedor Docker a partir de una imagen específica, pero sin iniciarlo automáticamente. 

```
docker create --name <nombre contenedor> <nombre imagen>:<tag>
```
Crear el contenedor  **srv-web** usando la imagen nginx version alpine
# COMPLETAR
```
C:\Windows\System32>docker create --name srv-web nginx:alpine
350213c176146415e214618a08d328f497fff973da586040b76d19dad4b91332
```
Si creas un contenedor en Docker sin asignarle un nombre específico utilizando la opción --name, Docker asignará automáticamente un nombre aleatorio al contenedor. Este nombre suele consistir en una combinación de palabras y números.  

Crear el contenedor usando la imagen hello-world
# COMPLETAR
```C:\Windows\System32>docker create hello-world
fb90ea76ddc0a09a4bf07d3c105c8b2e81e61faa4199b36be3433fc4eac68a24
```
### Listar los contenedores ejecutándose o no

```
docker ps -a
```
<img width="386" height="83" alt="image" src="https://github.com/user-attachments/assets/6f120b3c-f9d7-47d3-8b8f-99ecaa4d297d" />


### Para iniciar un contenedor

```
docker start <nombre contenedor o identificador>
```
Iniciar el contenedor srv-web 
# COMPLETAR
```
C:\Windows\System32>docker start srv-web
srv-web
```
### Listar los contenedores ejecutándose
```
docker ps 
docker ps | grep <nombre contenedor>
```
<img width="381" height="46" alt="image" src="https://github.com/user-attachments/assets/92065fdf-5867-4f6a-aaed-af33d2e07598" />

### Para detener un contenedor

```
docker stop <nombre contenedor>
```
```
C:\Windows\System32>docker stop srv-web
srv-web
```
### Para crear un contenedor y ejecutarlo inmediatamente

```
docker run --name <nombre contenedor> <nombre imagen>:<tag>
```
![Ecosistema de Docker](dockerRun.PNG)

Crear y ejecutar inmediatamente el contenedor **srv-web2** usando la imagen nginx:alpine
# COMPLETAR
```
C:\Windows\System32>docker run --name srv-web2 ngix:alpine
Unable to find image 'ngix:alpine' locally
docker: Error response from daemon: pull access denied for ngix, repository does not exist or may require 'docker login'
```
Run 'docker run --help' for more information
```
C:\Windows\System32>docker run --name srv-web2 nginx:alpine
/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
/docker-entrypoint.sh: Sourcing /docker-entrypoint.d/15-local-resolvers.envsh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
/docker-entrypoint.sh: Configuration complete; ready for start up
2025/10/06 03:49:21 [notice] 1#1: using the "epoll" event method
2025/10/06 03:49:21 [notice] 1#1: nginx/1.29.1
2025/10/06 03:49:21 [notice] 1#1: built by gcc 14.2.0 (Alpine 14.2.0)
2025/10/06 03:49:21 [notice] 1#1: OS: Linux 6.6.87.2-microsoft-standard-WSL2
2025/10/06 03:49:21 [notice] 1#1: getrlimit(RLIMIT_NOFILE): 1048576:1048576
2025/10/06 03:49:21 [notice] 1#1: start worker processes
2025/10/06 03:49:21 [notice] 1#1: start worker process 30
2025/10/06 03:49:21 [notice] 1#1: start worker process 31
2025/10/06 03:49:21 [notice] 1#1: start worker process 32
2025/10/06 03:49:21 [notice] 1#1: start worker process 33
2025/10/06 03:49:21 [notice] 1#1: start worker process 34
2025/10/06 03:49:21 [notice] 1#1: start worker process 35
2025/10/06 03:49:21 [notice] 1#1: start worker process 36
2025/10/06 03:49:21 [notice] 1#1: start worker process 37
2025/10/06 03:49:21 [notice] 1#1: start worker process 38
2025/10/06 03:49:21 [notice] 1#1: start worker process 39
2025/10/06 03:49:21 [notice] 1#1: start worker process 40
2025/10/06 03:49:21 [notice] 1#1: start worker process 41
2025/10/06 03:49:21 [notice] 1#1: start worker process 42
2025/10/06 03:49:21 [notice] 1#1: start worker process 43
2025/10/06 03:49:21 [notice] 1#1: start worker process 44
2025/10/06 03:49:21 [notice] 1#1: start worker process 45
2025/10/06 03:49:21 [notice] 1#1: start worker process 46
2025/10/06 03:49:21 [notice] 1#1: start worker process 47
2025/10/06 03:49:21 [notice] 1#1: start worker process 48
2025/10/06 03:49:21 [notice] 1#1: start worker process 49
2025/10/06 03:49:21 [notice] 1#1: start worker process 50
2025/10/06 03:49:21 [notice] 1#1: start worker process 51
```
**¿Qué sucede luego de la ejecución del comando?**
# COMPLETAR  
Se ejectura el contenedor en primer plano y se captura la entrada estandar de la terminal.

Cuando ejecutas un contenedor en primer plano sin la opción -d (modo detach), el contenedor captura la entrada estándar (stdin) del terminal, lo que significa que el terminal queda "atrapado" y no puedes introducir más comandos hasta que detengas el contenedor.

### Para crear un contenedor y ejecutarlo inmediatamente sin estar vinculados al mismo
-d: Es la opción que indica a Docker que ejecute el contenedor en segundo plano (en modo "detach").
Cuando un contenedor se ejecuta en segundo plano, Docker devuelve el control al terminal inmediatamente después de iniciar el contenedor, lo que permite al usuario seguir ejecutando otros comandos en el mismo terminal sin que el contenedor detenga la interacción.

```
docker run -d --name <nombre contenedor> <nombre imagen>:tag
```
Crear y ejecutar inmediatamente el contenedor **srv-web3** en modo detach usando la imagen nginx:alpine
# COMPLETAR
```
C:\Windows\System32>docker run -d --name srv-web3 nginx:alpine
70a9ac2406d80292e9f7f7743f87c6c21ae5c560d5c052d66f2699b0bdc74889
```
### Para eliminar un contenedor

```
docker rm <nombre contenedor>
```
Eliminar el contenedor que se creó a partir de la imagen hello-world 
# COMPLETAR
<img width="539" height="68" alt="image" src="https://github.com/user-attachments/assets/59b84779-a891-4a57-bc8d-743444d2176f" />

Verificar que el contenedor que se eliminó
# COMPLETAR
```
C:\Windows\System32>docker rm eloquent_lumiere
eloquent_lumiere
```
<img width="515" height="57" alt="image" src="https://github.com/user-attachments/assets/4a4c9386-71ae-47fe-8c94-9da3184a5517" />


### Para eliminar un contenedor que esté ejecutándose

```
docker rm -f <nombre contenedor>
```
Eliminar el contenedor **srv-web3** 
# COMPLETAR
```
C:\Windows\System32>docker rm -f srv-web3
srv-web3
```
Verificar que el contenedor que se eliminó
# COMPLETAR
<img width="510" height="49" alt="image" src="https://github.com/user-attachments/assets/0bcd9bb9-fc95-4370-8dd5-fa648b719abf" />

### Para inspecionar un contenedor 

Inspeccionar el contenedor **srv-web** 
# COMPLETAR
```
C:\Windows\System32>docker inspect srv-web
[
    {
        "Id": "350213c176146415e214618a08d328f497fff973da586040b76d19dad4b91332",
        "Created": "2025-10-06T03:41:23.239338186Z",
        "Path": "/docker-entrypoint.sh",
        "Args": [
            "nginx",
            "-g",
            "daemon off;"
        ],
        "State": {
            "Status": "exited",
            "Running": false,
            "Paused": false,
            "Restarting": false,
            "OOMKilled": false,
            "Dead": false,
            "Pid": 0,
            "ExitCode": 0,
            "Error": "",
            "StartedAt": "2025-10-06T03:43:37.778531152Z",
            "FinishedAt": "2025-10-06T03:46:42.908616354Z"
        },
        "Image": "sha256:42a516af16b852e33b7682d5ef8acbd5d13fe08fecadc7ed98605ba5e3b26ab8",
        "ResolvConfPath": "/var/lib/docker/containers/350213c176146415e214618a08d328f497fff973da586040b76d19dad4b91332/resolv.conf",
        "HostnamePath": "/var/lib/docker/containers/350213c176146415e214618a08d328f497fff973da586040b76d19dad4b91332/hostname",
        "HostsPath": "/var/lib/docker/containers/350213c176146415e214618a08d328f497fff973da586040b76d19dad4b91332/hosts",
        "LogPath": "/var/lib/docker/containers/350213c176146415e214618a08d328f497fff973da586040b76d19dad4b91332/350213c176146415e214618a08d328f497fff973da586040b76d19dad4b91332-json.log",
        "Name": "/srv-web",
        "RestartCount": 0,
        "Driver": "overlayfs",
        "Platform": "linux",
        "MountLabel": "",
        "ProcessLabel": "",
        "AppArmorProfile": "",
        "ExecIDs": null,
        "HostConfig": {
            "Binds": null,
            "ContainerIDFile": "",
            "LogConfig": {
                "Type": "json-file",
                "Config": {}
            },
            "NetworkMode": "bridge",
            "PortBindings": {},
            "RestartPolicy": {
                "Name": "no",
                "MaximumRetryCount": 0
            },
            "AutoRemove": false,
            "VolumeDriver": "",
            "VolumesFrom": null,
            "ConsoleSize": [
                51,
                97
            ],
            "CapAdd": null,
            "CapDrop": null,
            "CgroupnsMode": "private",
            "Dns": [],
            "DnsOptions": [],
            "DnsSearch": [],
            "ExtraHosts": null,
            "GroupAdd": null,
            "IpcMode": "private",
            "Cgroup": "",
            "Links": null,
            "OomScoreAdj": 0,
            "PidMode": "",
            "Privileged": false,
            "PublishAllPorts": false,
            "ReadonlyRootfs": false,
            "SecurityOpt": null,
            "UTSMode": "",
            "UsernsMode": "",
            "ShmSize": 67108864,
            "Runtime": "runc",
            "Isolation": "",
            "CpuShares": 0,
            "Memory": 0,
            "NanoCpus": 0,
            "CgroupParent": "",
            "BlkioWeight": 0,
            "BlkioWeightDevice": [],
            "BlkioDeviceReadBps": [],
            "BlkioDeviceWriteBps": [],
            "BlkioDeviceReadIOps": [],
            "BlkioDeviceWriteIOps": [],
            "CpuPeriod": 0,
            "CpuQuota": 0,
            "CpuRealtimePeriod": 0,
            "CpuRealtimeRuntime": 0,
            "CpusetCpus": "",
            "CpusetMems": "",
            "Devices": [],
            "DeviceCgroupRules": null,
            "DeviceRequests": null,
            "MemoryReservation": 0,
            "MemorySwap": 0,
            "MemorySwappiness": null,
            "OomKillDisable": null,
            "PidsLimit": null,
            "Ulimits": [],
            "CpuCount": 0,
            "CpuPercent": 0,
            "IOMaximumIOps": 0,
            "IOMaximumBandwidth": 0,
            "MaskedPaths": [
                "/proc/asound",
                "/proc/acpi",
                "/proc/interrupts",
                "/proc/kcore",
                "/proc/keys",
                "/proc/latency_stats",
                "/proc/timer_list",
                "/proc/timer_stats",
                "/proc/sched_debug",
                "/proc/scsi",
                "/sys/firmware",
                "/sys/devices/virtual/powercap"
            ],
            "ReadonlyPaths": [
                "/proc/bus",
                "/proc/fs",
                "/proc/irq",
                "/proc/sys",
                "/proc/sysrq-trigger"
            ]
        },
        "GraphDriver": {
            "Data": null,
            "Name": "overlayfs"
        },
        "Mounts": [],
        "Config": {
            "Hostname": "350213c17614",
            "Domainname": "",
            "User": "",
            "AttachStdin": false,
            "AttachStdout": true,
            "AttachStderr": true,
            "ExposedPorts": {
                "80/tcp": {}
            },
            "Tty": false,
            "OpenStdin": false,
            "StdinOnce": false,
            "Env": [
                "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin",
                "NGINX_VERSION=1.29.1",
                "PKG_RELEASE=1",
                "DYNPKG_RELEASE=1",
                "NJS_VERSION=0.9.1",
                "NJS_RELEASE=1"
            ],
            "Cmd": [
                "nginx",
                "-g",
                "daemon off;"
            ],
            "Image": "nginx:alpine",
            "Volumes": null,
            "WorkingDir": "/",
            "Entrypoint": [
                "/docker-entrypoint.sh"
            ],
            "OnBuild": null,
            "Labels": {
                "maintainer": "NGINX Docker Maintainers \u003cdocker-maint@nginx.com\u003e"
            },
            "StopSignal": "SIGQUIT"
        },
        "NetworkSettings": {
            "Bridge": "",
            "SandboxID": "",
            "SandboxKey": "",
            "Ports": {},
            "HairpinMode": false,
            "LinkLocalIPv6Address": "",
            "LinkLocalIPv6PrefixLen": 0,
            "SecondaryIPAddresses": null,
            "SecondaryIPv6Addresses": null,
            "EndpointID": "",
            "Gateway": "",
            "GlobalIPv6Address": "",
            "GlobalIPv6PrefixLen": 0,
            "IPAddress": "",
            "IPPrefixLen": 0,
            "IPv6Gateway": "",
            "MacAddress": "",
            "Networks": {
                "bridge": {
                    "IPAMConfig": null,
                    "Links": null,
                    "Aliases": null,
                    "MacAddress": "",
                    "DriverOpts": null,
                    "GwPriority": 0,
                    "NetworkID": "95884bd3f4468a065a8de209cf4b08cffad4ea66aaa7a56bf7031b3cc460fe42",
                    "EndpointID": "",
                    "Gateway": "",
                    "IPAddress": "",
                    "IPPrefixLen": 0,
                    "IPv6Gateway": "",
                    "GlobalIPv6Address": "",
                    "GlobalIPv6PrefixLen": 0,
                    "DNSNames": null
                }
            }
        },
        "ImageManifestDescriptor": {
            "mediaType": "application/vnd.oci.image.manifest.v1+json",
            "digest": "sha256:60e48a050b6408d0c5dd59b98b6e36bf0937a0bbe99304e3e9c0e63b7563443a",
            "size": 2495,
            "annotations": {
                "com.docker.official-images.bashbrew.arch": "amd64",
                "org.opencontainers.image.base.digest": "sha256:94f11b88c5d30105df2236d818a2dd50577bd2314f70374ae53ccaec61ac34f0",
                "org.opencontainers.image.base.name": "nginx:1.29.1-alpine-slim",
                "org.opencontainers.image.created": "2025-08-13T18:57:48Z",
                "org.opencontainers.image.revision": "5a4ad48c733b365d69a4d1c9946a9d8480469c7f",
                "org.opencontainers.image.source": "https://github.com/nginx/docker-nginx.git#5a4ad48c733b365d69a4d1c9946a9d8480469c7f:mainline/alpine",
                "org.opencontainers.image.url": "https://hub.docker.com/_/nginx",
                "org.opencontainers.image.version": "1.29.1-alpine"
            },
            "platform": {
                "architecture": "amd64",
                "os": "linux"
            }
        }
    }
]

```
