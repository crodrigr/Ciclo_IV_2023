# Separar las rutas y el controlador 


## 1. Crear el directorio routers y el user.js las rutas para el componente de usuarios

![image](https://user-images.githubusercontent.com/31961588/198838452-c196b5e4-8683-47ea-acf3-50f2e5283b85.png)


### 1.1 Crear la estructura del modulo user.js

![image](https://user-images.githubusercontent.com/31961588/198838529-bd5bdef1-5c19-4eed-928c-c7de136995b4.png)


### 1.2 Copiar lo de routers de server.js y llevarlo a user.js


#### 1.2.1 Server.js

![image](https://user-images.githubusercontent.com/31961588/198838738-4e6c3753-83cb-41b1-8a0c-2b3edd627450.png)

#### 1.2.2 User.js

![image](https://user-images.githubusercontent.com/31961588/198838698-6558a747-1a9c-4949-9105-e8e9e3156283.png)


![image](https://user-images.githubusercontent.com/31961588/198838791-d52b9931-d0e8-4044-a756-f1a0df53f39b.png)

### 2. Implementar los routers en el server.js

![image](https://user-images.githubusercontent.com/31961588/198838872-9c3daeb7-d489-40b0-9b07-65577ed49061.png)

#### 2.1 En user.js se ajusta el path, quitando el api por que ya está en el server.js

![image](https://user-images.githubusercontent.com/31961588/198838990-8efe4a61-8faf-4972-9f59-1c2cc5ef9a46.png)

![image](https://user-images.githubusercontent.com/31961588/198839053-75995f07-d6fd-4b1b-9971-4bc34945f177.png)

#### 2.2 En Server.js add un atributo de path para darle mejor presentación

![image](https://user-images.githubusercontent.com/31961588/198839137-cd131948-fcfd-4c60-b2f7-8d26ada69307.png)

![image](https://user-images.githubusercontent.com/31961588/198839161-ace8ccf5-c457-4e16-9975-970328d64fd8.png)

## 3. Separar de router las funcionalidad a través de controlladores. 

### 3.1 Crear el directorio controllers y el usuarios.js

![image](https://user-images.githubusercontent.com/31961588/198839278-9a23898c-d13f-47c5-955a-23ba6e756043.png)

### 3.2.1 Controller usuarios.js

![image](https://user-images.githubusercontent.com/31961588/198839426-a462b647-2b09-4c60-a285-4739a591c967.png)

### 3.2.2 Esto se debe hacer con los otros endpoints

![image](https://user-images.githubusercontent.com/31961588/198839501-5a8b99ac-080c-46a8-ac62-46b18ae362fe.png)

### 3.2.3 Probar 

![image](https://user-images.githubusercontent.com/31961588/198839725-b1ffa8dc-7f2b-4cd7-802c-08035d34cb9a.png)

### 3.2.4 Los otros endpoints

![image](https://user-images.githubusercontent.com/31961588/198839845-10192681-805a-418e-830e-2d3573a37323.png)

![image](https://user-images.githubusercontent.com/31961588/198839878-92bdd613-3b74-4bdf-9bae-26198d83118f.png)

#### 3.2.5 Ajsutamos las rutas en routers/usuarios.js de los otros endpoint

![image](https://user-images.githubusercontent.com/31961588/198839966-2874d272-74b8-4e79-b9d5-5ffb31d528ce.png)


