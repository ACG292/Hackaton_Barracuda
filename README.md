# Hackaton_Barracuda

# Proyecto de Análisis Financiero con Flask y Google Cloud

Este proyecto es una aplicación web que utiliza Flask para proporcionar un servicio de resumen de información financiera. Se integra con Google Cloud para buscar datos relevantes y utiliza un modelo generativo de Vertex AI para procesar y generar respuestas.

## Descripción de los Componentes

### 1. `app.py`

Este es el archivo principal de la aplicación Flask. Contiene la configuración del servidor, habilita CORS para permitir solicitudes desde otros orígenes y define una ruta API (`/api/summarize`) que maneja solicitudes POST para resumir información financiera.

#### Características:

- **CORS:** Permite solicitudes desde cualquier origen.
- **Ruta `/api/summarize`:** Recibe datos desde un cliente (por ejemplo, FlutterFlow), busca información en bases de datos y genera un resumen utilizando un modelo de IA.
- **Manejo de Errores:** Responde con un mensaje de error si ocurre alguna excepción durante el procesamiento.

### 2. `google_cloud_functions.py`

Este archivo contiene funciones que interactúan con Google Cloud para crear y gestionar un Data Store, importar documentos y crear un motor de búsqueda. Utiliza la biblioteca `google.cloud` para conectarse con Google Cloud Discovery Engine.

#### Funciones Clave:

- **`create_data_store`:** Crea un nuevo Data Store en Google Cloud.
- **`import_documents`:** Importa documentos desde Google Cloud Storage a un Data Store.
- **`create_engine`:** Crea un motor de búsqueda en Google Cloud asociado con un Data Store.
- **`search`:** Realiza búsquedas en un Data Store específico y devuelve resultados relevantes.

### 3. `Dockerfile`

Este archivo Docker define la imagen de contenedor para la aplicación. Utiliza una imagen base de Python 3.11, instala las dependencias desde `requirements.txt`, y configura el contenedor para ejecutar la aplicación Flask con Gunicorn.

#### Pasos en el Dockerfile:

- **Base de Python:** Utiliza `python:3.11-slim-buster` como base.
- **Instalación de Dependencias:** Copia `requirements.txt` y ejecuta `pip install` para instalar las dependencias necesarias.
- **Copiar Archivos:** Copia el resto de los archivos de la aplicación al contenedor.
- **Exponer el Puerto:** Expone el puerto 8080.
- **Ejecutar la Aplicación:** Configura Gunicorn para servir la aplicación Flask.

## Requisitos

- Python 3.11
- Dependencias en `requirements.txt`
- Cuenta de Google Cloud con acceso a Vertex AI y Google Cloud Discovery Engine.

## Cómo Ejecutar el Proyecto

1. **Instalar Dependencias:**
   ```bash
   pip install -r requirements.txt
