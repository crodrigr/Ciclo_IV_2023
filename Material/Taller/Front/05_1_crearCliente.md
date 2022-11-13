# Crear cliente

Para trabajar con fomularios a que importar FormsModule, ReactiveFormModule en el app.modules.ts

![image](https://user-images.githubusercontent.com/31961588/201549177-8fd2bed5-b1df-44d9-89ad-8d84a59d5a11.png)


### 1. Crear componente form 

![image](https://user-images.githubusercontent.com/31961588/201546906-f16d6c40-23ad-44a4-9037-c9e49cd001d8.png)

#### 1.1 Estructura de componente form

![image](https://user-images.githubusercontent.com/31961588/201546941-0a5f6a91-470b-4724-96ba-9acb5bfbce63.png)

### 2. En form.component.ts importar los componentes a necesitar

![image](https://user-images.githubusercontent.com/31961588/201547098-988ac6aa-9035-45cb-886f-643e1e49fcf7.png)

### 3. En form.component.ts definir variables

![image](https://user-images.githubusercontent.com/31961588/201547234-a7214fd8-5431-4457-b7db-6d0634763357.png)

### 3. En clientService.component.ts se define el servicio create cliente que llama al back

![image](https://user-images.githubusercontent.com/31961588/201548181-2ebdd233-ba46-4465-8500-87d916d03346.png)

### 4. En form.component.ts se define la función create que llama al clienteService.component.ts crea que envía la petición al back

![image](https://user-images.githubusercontent.com/31961588/201548571-472decd5-16c9-47f6-b5ce-f17c643fa08d.png)

### 5. Crear botón para ir a formulario de crear cliente y crear el path en en routing

**cliente.component.html**

![image](https://user-images.githubusercontent.com/31961588/201549603-a5fea628-b9fb-45cf-95dd-ee8a01ef1a61.png)

**app-routing.component.ts**

![image](https://user-images.githubusercontent.com/31961588/201549669-90f3dde8-25aa-42d2-9a89-b46f83f346c0.png)

**Ejemplo**

![image](https://user-images.githubusercontent.com/31961588/201549711-2f073e2d-25a0-48d7-9214-dd54aac20743.png)

![image](https://user-images.githubusercontent.com/31961588/201549720-70c98c38-e816-4b70-8aca-0f783082a291.png)


