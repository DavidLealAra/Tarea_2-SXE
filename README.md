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

# 3. Crea un contenedor con el nombre 'dam_alp1'. ¿Como puedes acceder a él?

Para crear un contenedor con un nombre concreto en este caso dam_alp1 se haria de esta manera:
```bash
sudo docker run --name dam_alp1 -it alpine
```
Sin salida

Comprobación
```bash
sudo docker ps -a
```
Salida:
CONTAINER ID   | IMAGE         | COMMAND     | CREATED         | STATUS                      | PORTS     | NAMES
|     :---:	|     :---: 	|     :---:   |    :---:         |:---:	                     |     :---:	|     :---: 	|
|**46c0491ee9c3**   | **alpine**   | **"/bin/sh"**   | **8 minutes ago **   | **Exited (0) 7 minutes ago**  |                     | **dam_alp1**  |

Para acceder a el se usaria el siguiente comando:
```bash
sudo docker exec -it dam_alp1 sh
```
Sin salida

# 4. Comprueba que ip tiene y si puedes hacer un ping a google.com

Para obtener la ip del contenedor se consigue mediante este comando:
```bash
sudo docker inspect dam_alp1 |grep IPA
```
Salida:

"SecondaryIPAddresses": null,
	    
"IPAddress": "172.17.0.2",
	    
"IPAMConfig": null,
"IPAddress": "172.17.0.2",
Para hacer un ping a google desde el contenedor primero tienes que entrar al mismo con el comando anterior y una vez dentro usar el siguiente comando:
```bash
ping -c 2 google.com
```
Salida:

PING google.com (142.250.200.110): 56 data bytes
64 bytes from 142.250.200.110: seq=0 ttl=61 time=16.128 ms
64 bytes from 142.250.200.110: seq=1 ttl=61 time=16.986 ms
--- google.com ping statistics ---
2 packets transmitted, 2 packets received, 0% packet loss
round-trip min/avg/max = 16.128/16.557/16.986 ms

# 5. Crea un contenedor con el nombre 'dam_alp2'. ¿Puedes hacer ping entre los contenedores?

Para hacer un ping entre dos contenedores se hace con el siguiente comando:
```bash
sudo docker run --name dam_alp2 -it alpine
```
Salida:

/ # ping -c 2 172.17.0.2
PING 172.17.0.2 (172.17.0.2): 56 data bytes
64 bytes from 172.17.0.2: seq=0 ttl=64 time=0.202 ms
@@ -127,6 +127,39 @@ PING 172.17.0.2 (172.17.0.2): 56 data bytes
2 packets transmitted, 2 packets received, 0% packet loss
round-trip min/avg/max = 0.202/0.230/0.258 ms

## 6. Sal del terminal, ¿que ocurrió con el contenedor?

Siguen iniciados aunque salgan de la terminal.

## 7. ¿Cuanta memoria en el disco duro ocupaste?

Con el siguiente comando puedes saber cuanta memoria ocupé en el disco.
```bash
sudo docker system df
```
Salida:

|TYPE       |  TOTAL |  ACTIVE | SIZE |     RECLAIMABLE |
|     :---:|  :---: |  :---:  |:---:|:---:	       |
|Images          |3         |3         |85.92MB   |0B (0%)|
|Containers      |7         |2         |83B       |31B (37%)|
|Local Volumes   |0         |0         |0B        |0B|
|Build Cache     |0         |0         |0B        |0B|

## 8. ¿Cuanta RAM ocupan los contenedores? ¿Hay algún comando docker para saber esto?

Con este comando se pude saber la ram utilizada por los contenedores:
```bash
sudo docker stats
```
Salida:

| CONTAINER ID  | NAME 		|     CPU %         | **MEM USAGE / LIMIT**   	| **MEM %**     	| NET I/O       	| BLOCK I/O     	| PIDS				|
|     :---:	|     :---: 	|     :---:  	    |:---:			|:---:			|:---:			|:---:			|:---:			|
| 4778d7912c10  | dam_alp2      |	0.00%       | **472KiB / 7.883GiB**  	| **0.01%**     	| 3.56kB / 0B   	| 8.19kB / 0B   	| 1				|
| 46c0491ee9c3  | dam_alp1     |	 0.00%      | **588KiB / 7.883GiB**  	| **0.01%**     	| 7.66kB / 0B   	| 1.33MB / 0B   	| 1				|
		    







 
	
	
