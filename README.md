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
- y el nombre del contenedor con ````--name```

![image](https://user-images.githubusercontent.com/91556405/159949539-b22a93ef-be55-4fc9-92ac-a5014e6d76b5.png)

Ahora, si se accede a http://localhost:8080 con el contenedor activo, podremos comprobar que funciona si aparece un mensaje de bienvenida de nginx.

![image](https://user-images.githubusercontent.com/91556405/159950400-7149b4d2-fa97-46a4-b2a5-916070adb12f.png)

Después, para cerrar el contenedor utilizaremos ```$ docker stop web```.

![image](https://user-images.githubusercontent.com/91556405/159951971-b2eabb23-3d38-4713-848a-074fbd2f1400.png)
