# Tarea_2-SXE

# 1. Descarga la imagen "alpine" SIN ARRANCARLA y comprueba que está en tu equipo

  Para descargar una imagen llamada alpine sin arrancarla es necesario utilizar el comando **sudo docker pull alpine** en el siguiente codigo se muestra como lo he utilizado:
  ```bash
  sudo docker pull alpine
```
Salida:

Using default tag: latest

latest: Pulling from library/alpine

Digest: sha256:beefdbd8a1da6d2915566fde36db9db0b524eb737fc57cd1367effd16dc0d06d

Status: Image is up to date for alpine:latest

docker.io/library/alpine:latest

```bash
sudo docker images
```
Salida:

|REPOSITORY    | TAG       | IMAGE ID       | CREATED        | SIZE	|
|     :---:	|     :---: 	|     :---:  	    |:---:  |:---:	|
|ubuntu        | latest    | 61b2756d6fa9   | 3 weeks ago     | 78.1MB	|
|**alpine**      | **latest**    | **91ef0af61f39**   | **4 weeks ago**     | **7.8MB**|
|hello-world   | latest    | d2c94e258dcb   | 17 months ago  | 13.3kB	|

# 2. Crea un contenedor sin ponerle nombre. ¿está arrancado? Obtén el nombre

Para crear un contenedor sin ponerle nombre se hace uso de este comando **sudo docker ps -a** en el siguiente codigo se muestra como lo he utilizado y a su vez respondo las dos ultimas preguntas:

```bash
sudo docker run alpine
```
Sin salida

Para saber si esta arrancado y obtener el nombre se utiliza el siguiente comando en la salida se ve que no esta arrancado:
```bash
sudo docker ps -a
```
Salida:

|CONTAINER ID   | IMAGE         | COMMAND     | CREATED         | STATUS                         | PORTS     | NAMES		|
|     :---:	|     :---: 	|     :---:   |    :---:         |:---:	                         |     :---:	|     :---: 	|
|**48cf4f815984**   | **alpine**   | **"/bin/sh"**   | **33 seconds ago**    | **Exited (0) 33 seconds ago** | 	|**dreamy_jemison**|
|2fe19b0b420d   | ubuntu        | "bash"      | 33 minutes ago      | Exited (0) 32 minutes ago | 		|busy_hodgkin|
|6d4c969701ca   | ubuntu        | "bash"      | About an hour ago   | Exited (0) About an hour ago |		 |cranky_noyce|
|000663703dc3   | hello-world   | "/hello"    | About an hour ago   | Exited (0) About an hour ago | 		|eager_shaw|
|ca9f975d9c31   | hello-world   | "/hello"    | About an hour ago   | Exited (0) About an hour ago | 		|thirsty_saha|





		    







 
	
	
