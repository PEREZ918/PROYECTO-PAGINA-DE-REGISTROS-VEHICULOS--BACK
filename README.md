# PROYECTO-PAGINA-DE-REGISTROS-VEHICULOS--BACK

En este proyecto se desea realizar una pagina web para el almacenamiento de vehiculos y motos la cual nos enseñera ls siguientes caracteristicas: modelo de el vehiculo o moto, marca de el vehiculo o moto, año de fabricacion de dicho vehiculo moto y una imagen descriptva de el vehiculo o moto


## Tecnologías Utilizadas

- **Spring Boot 3.5.6**: Framework principal para el desarrollo de la aplicación
- **Spring Data JPA**: Para la persistencia de datos
- **H2 Database**: Base de datos en memoria para desarrollo y pruebas
- **Spring Validation**: Para validación de datos de entrada
- **Maven**: Gestión de dependencias y construcción del proyecto

## Funcionamiento de la Aplicación

La aplicación expone endpoints REST para gestionar dos tipos de entidades:

1. **Vehículos** (`/api/vehiculos`): Entidades de vehículos
2. **Motos** (`/api/motos`): Entidades de motos que heredan de vehículos

Cada entidad tiene los siguientes campos:
- `id`: Identificador único
- `marca`: Marca del vehículo/moto (obligatorio, 2-50 caracteres)
- `modelo`: Modelo del vehículo/moto (obligatorio, 1-50 caracteres)
- `anio`: Año del vehículo/moto (obligatorio)
- `imagenUrl`: URL de la imagen subida (opcional)

### Endpoints Disponibles

#### Vehículos

- `GET /api/vehiculos`: Lista todos los vehículos
- `POST /api/vehiculos`: Crea un nuevo vehículo
- `GET /api/vehiculos/{id}`: Obtiene un vehículo por ID
- `PUT /api/vehiculos/{id}`: Actualiza un vehículo por ID
- `DELETE /api/vehiculos/{id}`: Elimina un vehículo por ID

#### Motos

- `GET /api/motos`: Lista todas las motos
- `POST /api/motos`: Crea una nueva moto
- `GET /api/motos/{id}`: Obtiene una moto por ID.
- `PUT /api/motos/{id}`: Actualiza una moto por ID
- `DELETE /api/motos/{id}`: Elimina una moto por ID

### Configuración

La aplicación utiliza H2 como base de datos en memoria. La configuración se encuentra en `src/main/resources/application.properties`:

- Base de datos: `jdbc:h2:mem:testdb`
- Consola H2 habilitada: `http://localhost:8080/h2-console`
- Directorio de uploads: `./uploads`
- Tamaño máximo de archivo: 10MB
- Tamaño máximo de request: 12MB

## Cómo Ejecutar la Aplicación

1. Asegúrate de tener Java 17+ y Maven instalados
2. descarga el proyecto
3. Navega al directorio raíz del proyecto
4. Ejecuta el comando: `mvn spring-boot:run`
5. La aplicación estará disponible en `http://localhost:8080`

## Extensiones Recomendadas para VSCode

- **Java Extension Pack**: Proporciona soporte completo para desarrollo Java, incluyendo sintaxis, debugging y más.
- **Spring Boot Extension Pack**: Ofrece herramientas específicas para Spring Boot, como asistencia en configuración, navegación de código y plantillas.
- **Thunder Client**: Extensión para testing de APIs REST directamente desde VSCode. Permite crear, guardar y ejecutar requests HTTP.

## Pruebas con Thunder Client

Thunder Client es una extensión de VSCode que permite probar APIs REST de manera sencilla. A continuación, se detallan todas las pruebas que se pueden realizar para validar el funcionamiento de la aplicación. Asegúrate de que la aplicación esté ejecutándose en `http://localhost:8080` antes de realizar las pruebas.

### Configuración Inicial en Thunder Client

1. Abre VSCode e instala la extensión "Thunder Client".
2. Abre la pestaña de Thunder Client (icono de rayo en la barra lateral).
3. Crea una nueva colección llamada "Vehículos API".
4. Establece la base URL como `http://localhost:8080`.

### Pruebas para Vehículos

#### 1. Crear Vehículo (POST /api/vehiculos)
- **Método**: POST
- **URL**: `http://localhost:8080/api/vehiculos`
- **Body** (Form-Data):
  - vehiculo:  `{"marca":"Toyota","modelo":"Corolla","anio":2020}`
  - imagen: (tipo file, opcional) Selecciona una imagen (jpg, png, webp, avif)

#### 2. Listar Vehículos (GET /api/vehiculos)
- **Método**: GET
- **URL**: `http://localhost:8080/api/vehiculos`
- **Body**: Ninguno


#### 3. Obtener Vehículo por ID (GET /api/vehiculos/{id})
- **Método**: GET
- **URL**: `http://localhost:8080/api/vehiculos/1` (reemplaza 1 con un ID existente)
- **Body**: Ninguno

#### 4. Actualizar Vehículo (PUT /api/vehiculos/{id})
- **Método**: PUT
- **URL**: `http://localhost:8080/api/vehiculos/1` (reemplaza 1 con un ID existente)
- **Body** 
  - vehiculo: `{"marca":"Toyota","modelo":"Corolla Updated","anio":2021}`
  - imagen: (tipo file, opcional) Selecciona una nueva imagen

#### 5. Eliminar Vehículo (DELETE /api/vehiculos/{id})
- **Método**: DELETE
- **URL**: `http://localhost:8080/api/vehiculos/1` (reemplaza 1 con un ID existente)
- **Body**: Ninguno

### Pruebas para Motos

#### 6. Crear Moto (POST /api/motos)
- **Método**: POST
- **URL**: `http://localhost:8080/api/motos`
- **Body** (Form-Data):
  - moto: `{"marca":"Honda","modelo":"CBR600","anio":2019}`
  - imagen: (tipo file, opcional) Selecciona una imagen
  

#### 7. Listar Motos (GET /api/motos)
- **Método**: GET
- **URL**: `http://localhost:8080/api/motos`
- **Headers**: Ninguno
- **Body**: Ninguno


#### 8. Obtener Moto por ID (GET /api/motos/{id})
- **Método**: GET
- **URL**: `http://localhost:8080/api/motos/1` (reemplaza 1 con un ID existente)
- **Headers**: Ninguno
- **Body**: Ninguno


#### 9. Actualizar Moto (PUT /api/motos/{id})
- **Método**: PUT
- **URL**: `http://localhost:8080/api/motos/1` (reemplaza 1 con un ID existente)
- **Body** (Form-Data):
  - moto: (tipo text) `{"marca":"Honda","modelo":"CBR600 Updated","anio":2020}`
  - imagen: (tipo file, opcional) Selecciona una nueva imagen


#### 10. Eliminar Moto (DELETE /api/motos/{id})
- **Método**: DELETE
- **URL**: `http://localhost:8080/api/motos/1` (reemplaza 1 con un ID existente)
- **Body**: Ninguno


### Verificación en H2 Console

Después de realizar algunas pruebas, puedes verificar los datos en la base de datos:

1. Abre `http://localhost:8080/h2-console` en tu navegador.
2. Conecta con los datos por defecto (JDBC URL: `jdbc:h2:mem:testdb`, User: `sa`, Password: vacío).
3. Ejecuta consultas SQL como `SELECT * FROM vehiculo;` o `SELECT * FROM moto;`.

### Notas Adicionales

- La aplicación soporta archivos de imagen con extensiones: jpg, jpeg, png, gif, webp, avif.
- Los datos se pierden al reiniciar la aplicación ya que usa H2 en memoria.


### METODOS PARA MOTOS

CREAR MOTO 

<img width="1337" height="709" alt="Captura de pantalla 2025-11-06 182149" src="https://github.com/user-attachments/assets/1baa4e22-4345-4a41-9ec9-bf26a5682000" />

LISTAR TODOS LAS MOTOS

<img width="1356" height="668" alt="Captura de pantalla 2025-11-06 182544" src="https://github.com/user-attachments/assets/df7f4212-8656-475c-b66a-36305e08df77" />

LISTAR MOTOS POR ID

<img width="1341" height="680" alt="Captura de pantalla 2025-11-06 182322" src="https://github.com/user-attachments/assets/20b6fef2-e8dd-4ef6-acd1-aae91b118204" />

EDITAR MOTOS 

<img width="1352" height="671" alt="Captura de pantalla 2025-11-06 182427" src="https://github.com/user-attachments/assets/86e8482d-e495-4cc2-b029-36d3fd93e98d" />

ELIMINAR MOTO

<img width="1356" height="668" alt="Captura de pantalla 2025-11-06 182544" src="https://github.com/user-attachments/assets/e0733445-7c6e-4354-bfc8-5810d8fe9e93" />



### METODOS PARA VEHICULO

CREAR VEHICULO

<img width="1348" height="605" alt="Captura de pantalla 2025-11-06 183630" src="https://github.com/user-attachments/assets/e406b9bf-148e-45e6-92ae-8103ad6d5d9f" />


LISTAR TODOS LOS VEHICULOS

<img width="1356" height="624" alt="Captura de pantalla 2025-11-06 183917" src="https://github.com/user-attachments/assets/06f4c6ba-884d-4f15-87df-8bdc353d541f" />


LISTAR MOTOS POR ID

<img width="1359" height="661" alt="Captura de pantalla 2025-11-06 183945" src="https://github.com/user-attachments/assets/a005f64f-85ef-4d57-a9d4-b0612722edb3" />


EDITAR MOTOS

<img width="1357" height="670" alt="Captura de pantalla 2025-11-06 184107" src="https://github.com/user-attachments/assets/ed4c551b-13af-4bea-9f42-609d525a8981" />


ELIMINAR MOTO

<img width="1353" height="666" alt="Captura de pantalla 2025-11-06 184134" src="https://github.com/user-attachments/assets/28356018-61d4-4d4b-bffc-e4dcb8bfc6a4" />


