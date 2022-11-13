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

### 5. HttpClient el componente de @angular/common/http que permite hacer peticiones http: get, post, put, pacth, delete al backend

Este componente se usa en el cliente.service.ts

![image](https://user-images.githubusercontent.com/31961588/201538828-d8cf1284-4d24-454c-9e8b-a2a306eb3a76.png)

#### 5.1 Inicializar el path back en el método constructo del cliente.service.ts

![image](https://user-images.githubusercontent.com/31961588/201538991-23ef9e51-d890-470b-96fe-383a69d458b3.png)



