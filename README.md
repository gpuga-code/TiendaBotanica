# 🌱 Tienda de Plantas — Django

Aplicación web de e-commerce para la venta de plantas, desarrollada con **Django** y **Django REST Framework**. Incluye un sitio web con catálogo de productos, gestión de usuarios y carrito de compras, además de una **API REST** con autenticación por token para el manejo de productos.

## ✨ Funcionalidades

### Sitio web
- **Catálogo de plantas** con categorías, precio, stock e imagen de cada producto.
- **CRUD de plantas**: listar, crear, modificar y eliminar productos.
- **Registro de usuarios** y formulario de suscripción.
- **Carrito de compras** y seguimiento del estado del pedido.
- Páginas de contacto, términos y condiciones, y login.

### API REST (`/api/`)
- `GET/POST /api/lista_plantas` — listar y crear plantas.
- `GET/PUT/DELETE /api/detalle_planta/<id>` — obtener, actualizar o eliminar una planta específica.
- `POST /api/loginApi` — login que retorna un token de autenticación.
- Protegida con `TokenAuthentication` de Django REST Framework: todos los endpoints de plantas requieren un token válido.

### Panel de administración
- Gestión de `Categoria`, `Planta` y `Usuario` desde el admin de Django (`/admin`).

## 🏗️ Estructura del proyecto

```
tienda/           # Configuración principal del proyecto (settings, urls)
app/              # App principal: modelos, vistas, templates, estáticos
api_app/          # API REST (endpoints de plantas y login por token)
media/            # Imágenes de productos subidas
```

## 🛠️ Tecnologías

- **Django 4.0**
- **Django REST Framework** (API + autenticación por token)
- **Oracle Database** (vía `cx_Oracle`)
- **Pillow** (manejo de imágenes)
- **Bootstrap 5** (interfaz)

## 📋 Requisitos previos

- Python 3.8+
- Una base de datos Oracle accesible (local o remota)
- pip

## ⚙️ Instalación

1. Clona el repositorio:
   ```bash
   git clone https://github.com/tu-usuario/Tienda-Django.git
   cd Tienda-Django
   ```

2. Crea un entorno virtual e instala las dependencias:
   ```bash
   python -m venv venv
   source venv/bin/activate  # En Windows: venv\Scripts\activate
   pip install -r requeriments.txt
   ```

3. Copia el archivo de variables de entorno de ejemplo y complétalo con tus datos:
   ```bash
   cp .env.example .env
   ```
   Deberás definir `SECRET_KEY`, `DEBUG`, `ALLOWED_HOSTS` y los datos de conexión a tu base de datos Oracle (`DB_NAME`, `DB_USER`, `DB_PASSWORD`).

   Puedes generar una `SECRET_KEY` nueva con:
   ```bash
   python -c "from django.core.management.utils import get_random_secret_key; print(get_random_secret_key())"
   ```

4. Aplica las migraciones:
   ```bash
   python manage.py migrate
   ```

5. (Opcional) Crea un superusuario para acceder al panel de administración:
   ```bash
   python manage.py createsuperuser
   ```

6. Ejecuta el servidor:
   ```bash
   python manage.py runserver
   ```

## 🔑 Variables de entorno

Este proyecto no incluye ninguna credencial en el código — todas se cargan desde un archivo `.env` (ver `.env.example`):

| Variable | Descripción |
|---|---|
| `SECRET_KEY` | Clave secreta de Django |
| `DEBUG` | `True` en desarrollo, `False` en producción |
| `ALLOWED_HOSTS` | Hosts permitidos, separados por coma |
| `DB_NAME` | Nombre/ubicación de la base de datos Oracle |
| `DB_USER` | Usuario de la base de datos |
| `DB_PASSWORD` | Contraseña de la base de datos |

> ⚠️ El archivo `.env` nunca debe subirse al repositorio (ya está excluido en `.gitignore`).

## 🚧 Estado del proyecto / próximos pasos

Este proyecto está en desarrollo activo. Algunas áreas pendientes de completar:

- Proteger las vistas de administración de productos (crear/modificar/eliminar) para que solo usuarios autenticados puedan usarlas.
- Migrar el modelo `Usuario` propio para usar el sistema de autenticación de Django (contraseñas hasheadas) en vez de un modelo con contraseña en texto plano.
- Completar la lógica del carrito de compras y el seguimiento de pedidos.

## 📄 Licencia

Este proyecto es de uso libre. Ajusta esta sección según lo que prefieras (MIT, uso académico, uso privado, etc.).
