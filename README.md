# Docker-nginx
### Creando una imagen personalizada en docker: Nginx (servidor web)

Primero de todo, voy a descargar la imagen oficial de nginx,

![image](https://user-images.githubusercontent.com/91556405/159945004-b0a1b324-d94d-4ced-b373-c2b7b61a53a3.png)

con el comando ```$ docker pull nginx```.

![image](https://user-images.githubusercontent.com/91556405/159945812-38caa2c5-3066-44e2-ab39-c422069f4878.png)

Luego, ejecuto la imagen nginx con ```$ docker run --rm -d -p 8080:80 --name web nginx``` ,
donde indicando:
- el puerto del host con ```-p```
- que el contenedor se ejecute en segundo plano con ```-d```
- que se borre automaticamente cuando sales del contenedor con ```--rm```
- y el nombre del contenedor con ```--name```

![image](https://user-images.githubusercontent.com/91556405/159949539-b22a93ef-be55-4fc9-92ac-a5014e6d76b5.png)

Ahora, si se accede a http://localhost:8080 con el contenedor activo, podremos comprobar que funciona si aparece un mensaje de bienvenida de nginx.

![image](https://user-images.githubusercontent.com/91556405/159950400-7149b4d2-fa97-46a4-b2a5-916070adb12f.png)

Después, para cerrar el contenedor utilizaremos ```$ docker stop web```.

![image](https://user-images.githubusercontent.com/91556405/159951971-b2eabb23-3d38-4713-848a-074fbd2f1400.png)

#### Agregar HTML personalizado
Creamos una página html personalizada y luego la publicamos usando la imagen Nginx.
Para ello, una vez creado el archivo html en el directorio ```~/Documentos/nginx/site-content```,
lanzamos el siguinte comando: ```docker run --rm -d -p 8080:80 --name web -v ~/Documentos/nginx/site-content:/usr/share/nginx/html nginx```
![Captura de pantalla 2022-04-25 182851](https://user-images.githubusercontent.com/91556405/165134417-9df218eb-c612-4f10-9f07-4acc0a62bc75.png)
![Captura de pantalla 2022-04-25 182706](https://user-images.githubusercontent.com/91556405/165134433-1e644fd0-b57f-4cdd-ba2e-4836cfe0daf9.png)

## Nginx con la maquina de Azure
Primero, añadimos una nueva regla de puerto de entrada para el puerto 8080 en el portal de azure.
![Captura de pantalla 2022-04-25 210142](https://user-images.githubusercontent.com/91556405/165339901-883b9dec-ca4e-4dfc-8f26-e91c9899fea7.png)

Luego, entramos en la maquina virtual desde la consola
![8](https://user-images.githubusercontent.com/91556405/165344056-7d8cbb2c-95c5-4321-bfce-986ac7a60477.png)

Y hacemos un pull de la imagen de nginx, con sudo al principio para darle privilegios de usuario ```sudo docker pull nginx:latest```
![3](https://user-images.githubusercontent.com/91556405/165341978-64768b32-11d4-4f77-9ea7-58f1acd90f10.png)

Finalmente, creamos el volumen con un html personalizado que hemos creado anteriormente
![Captura de pantalla 2022-04-25 210052](https://user-images.githubusercontent.com/91556405/165342819-d1e0b425-750c-44f6-8879-452b921523bd.png)
![Captura de pantalla 2022-04-25 210120](https://user-images.githubusercontent.com/91556405/165342860-8cbc1c63-cd33-4b6b-97d5-69d888b0407b.png)


