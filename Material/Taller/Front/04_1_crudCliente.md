# Crear el crud de cliente

### 1. Crear el componente cliente con ng g c client

![image](https://user-images.githubusercontent.com/31961588/201538124-aea040dd-f747-489b-88ab-a43ae4c90cfb.png)


### 2. Crear el modelo Client desde el lado del front con un interfaz. 

Se crea dentro del componente Client un archivio client.ts y en el se define la interfaz Client que representa el modelo Client desde el lado del cliente. 

![image](https://user-images.githubusercontent.com/31961588/201538290-3f8afca3-8b4c-452a-a10d-30c8b6f52659.png)

### 3. Crear el service Client  que proporciona la conexión con el back

![image](https://user-images.githubusercontent.com/31961588/201538618-6639bb67-1a1b-4790-81b1-8eba3bd48228.png)

### 4. Configuración path back como variable de entorno

![image](https://user-images.githubusercontent.com/31961588/201538691-3c7a97c3-bf02-41c7-8871-49e9bb5a43e1.png)

### 5. HttpClient el componente de @angular/common/http que permite hacer peticiones http: get, post, put, pacth, delete al backend}

Para poder usar el HttpClient en cada servicio se debe implementar el HttpClientModule en app.module.ts

![image](https://user-images.githubusercontent.com/31961588/201544374-7908f717-2c94-4abb-af4f-edcf4e826ea4.png)


Este componente se usa en el cliente.service.ts

![image](https://user-images.githubusercontent.com/31961588/201538828-d8cf1284-4d24-454c-9e8b-a2a306eb3a76.png)

#### 5.1 Inicializar el path back en el método constructo del cliente.service.ts

![image](https://user-images.githubusercontent.com/31961588/201538991-23ef9e51-d890-470b-96fe-383a69d458b3.png)

#### 5.2 Crear el método getClients que obtiene el listado de clientes desde el back

![image](https://user-images.githubusercontent.com/31961588/201540520-1441ae71-7676-43f4-997a-8f73836deefc.png)

### 6. Listar los clientes en client.componente.html 

Para listar los clients en client.component se debe hacer el llamado del getClients en el servicio que se creo en el punto anterior y listarlos en la vista del componente cliente que sería el client.component.html. Lo primero es llamar al getClientes en client.componet.ts

#### 6.1 client.component.ts

![image](https://user-images.githubusercontent.com/31961588/201542894-8a1f4b8c-b41e-4f53-9ca2-a2c83daf77ff.png)


#### 6.2 client.componet.html

![image](https://user-images.githubusercontent.com/31961588/201543449-25cf1bce-7670-49b0-bb9f-e184fdbd3f7f.png)


#### 6.2.1 Table client

![image](https://user-images.githubusercontent.com/31961588/201543425-5c89fa39-cff8-4b2f-b7b3-a886068f3282.png)


