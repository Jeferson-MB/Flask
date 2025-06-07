# MyPinterest - Proyecto Fullstack

Este proyecto está compuesto por dos repositorios principales: **Frontend** y **Backend**. Juntos conforman una aplicación de galería de imágenes tipo Pinterest, donde los usuarios pueden registrarse, iniciar sesión, subir imágenes, dar 'me gusta' y comentar fotos de otros usuarios.

---

## Tabla de Contenidos

- [Descripción General](#descripción-general)
- [Arquitectura y Componentes](#arquitectura-y-componentes)
  - [Frontend](#frontend)
  - [Backend](#backend)
- [Despliegue en Render](#despliegue-en-render)
- [Pruebas de Estrés con Locust](#pruebas-de-estrés-con-locust)
- [Instalación y Ejecución Local](#instalación-y-ejecución-local)
- [Principales Funcionalidades](#principales-funcionalidades)
- [Tecnologías Usadas](#tecnologías-usadas)
- [Licencia](#licencia)

---

## Descripción General

El sistema permite a los usuarios:
- Registrarse e iniciar sesión.
- Subir imágenes a la galería general o personal.
- Comentar y dar 'me gusta' a fotos.
- Visualizar perfiles y galerías de otros usuarios.

La comunicación entre el frontend y backend se realiza mediante peticiones HTTP (principalmente fetch), siguiendo el paradigma SPA (Single Page Application) para una experiencia fluida.

---

## Arquitectura y Componentes

### Frontend

- **Lenguajes:** JavaScript (84%), CSS (8%), HTML (8%)
- **Frameworks/Librerías:** Materialize CSS, módulos ES6, Web Components.

Las rutas y endpoints del frontend están configurados para consumir la API REST del backend desplegado en Render.

### Backend

- **Lenguaje:** Python (100%)
- **Framework principal:** Flask

El backend está preparado para ejecutarse en Render y expone todos los endpoints necesarios para la gestión de usuarios, imágenes, comentarios y likes. Se utilizan archivos JSON y SQLite como almacenamiento.

---

## Despliegue en Render

Ambos repositorios están diseñados para funcionar correctamente en la nube usando [Render](https://render.com/):

- **Variables de entorno:** Asegúrate de configurar correctamente las variables y rutas para que apunten al backend publicado en Render.
- **CORS y CSP:** El backend ya incluye configuración CORS y políticas de seguridad CSP para funcionar de manera segura en producción.
- **Archivos persistentes:** Render soporta almacenamiento persistente, asegúrate de que la carpeta `/data` sea persistente si necesitas mantener datos.

---

## Pruebas de Estrés con Locust

Para evaluar el rendimiento del backend desplegado en Render, se recomienda el uso de [Locust](https://locust.io/):

1. Instala Locust en tu máquina local:
   ```bash
   pip install locust
   ```
2. Crea un archivo `locustfile.py` especificando los endpoints a testear (login, registro, subida de imágenes, comentarios, likes).
3. Lanza Locust apuntando a la URL pública de Render:
   ```bash
   locust -H https://tu-backend.onrender.com
   ```
4. Abre el navegador en `http://localhost:8089` y configura la cantidad de usuarios simulados y tasa de aparición.

**Recomendación:** Empieza con una carga baja y aumenta progresivamente para identificar el límite antes de que Render limite los recursos (por ser un entorno compartido/free).

---

## Instalación y Ejecución Local

### Backend

1. Clona el repositorio `Backend` y navega a la carpeta.
2. Instala dependencias:
   ```bash
   pip install flask flask-cors bcrypt
   ```
3. Ejecuta el servidor:
   ```bash
   python app.py
   ```

### Frontend

1. Clona el repositorio `Frontend` y navega a la carpeta.
2. Abre `index.html` en tu navegador preferido.
3. Configura la URL del backend si es necesario en los archivos JS principales.

---

## Principales Funcionalidades

- **Autenticación:** Registro e inicio de sesión seguro.
- **Subida de imágenes:** Formulario amigable para cargar fotos.
- **Galería:** Visualización de imágenes en tarjetas, filtrado por usuario.
- **Likes y comentarios:** Interacción en tiempo real, actualización de contadores.
- **Perfil de usuario:** Visualización y edición de foto de perfil.

---

## Tecnologías Usadas

- **Frontend:** JavaScript ES6, Web Components, Materialize CSS, HTML5, CSS3.
- **Backend:** Python, Flask, SQLite, JSON para imágenes y comentarios, bcrypt para seguridad.
- **Comunicación:** API RESTful con CORS.

---

## Licencia

Este proyecto reutiliza Materialize CSS bajo licencia MIT. El resto del código es de uso académico y libre para aprendizaje.

---