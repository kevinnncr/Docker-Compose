Informe: Creación de Contenedores de PostgreSQL y PgAdmin con Docker
Compose

1. Objetivo de la Práctica
   La práctica consiste en levantar un entorno de base de datos en contenedores que incluya:
   • PostgreSQL como motor de base de datos.
   • PgAdmin como herramienta de administración de PostgreSQL.
   • Configuración de un archivo YAML para definir estos servicios de manera estructurada.
2. Explicación del Archivo docker-compose.yml
   Aquí está el archivo docker-compose.yml utilizado: abrir "docker-compose.yml".
   Explicación de las configuraciones principales:
   • version: Define la versión de Docker Compose.
   • services: Lista de servicios a ejecutar.
   o PostgreSQL (postgres):
   ▪ image: postgres:13, especifica la versión de PostgreSQL.
   ▪ container_name: Nombra el contenedor como postgres_db.
   ▪ environment: Define variables de entorno:
   ▪ POSTGRES_USER: Usuario de la base de datos.
   ▪ POSTGRES_PASSWORD: Contraseña de la base de datos.
   ▪ POSTGRES_DB: Nombre de la base de datos.
   ▪ volumes: Crea un volumen persistente (postgres_data) para almacenar
   datos y evitar pérdida tras detener el contenedor.
   ▪ ports: Mapea el puerto 5432 del contenedor al 5432 del host, permitiendo
   conexiones a PostgreSQL.
   o PgAdmin (pgadmin):
   ▪ image: dpage/pgadmin4, imagen de PgAdmin.
   ▪ container_name: Nombra el contenedor como pgadmin.
   ▪ environment: Define variables de entorno para acceso a PgAdmin:
   ▪ PGADMIN_DEFAULT_EMAIL y
   PGADMIN_DEFAULT_PASSWORD configuran las
   credenciales.
   ▪ ports: Mapea el puerto 80 del contenedor al 5050 del host, habilitando el
   acceso a la interfaz web de PgAdmin.
   4
   ▪ depends_on: Asegura que PostgreSQL se inicie antes que PgAdmin.
3. Pasos para Ejecutar el Archivo docker-compose.yml
4. Iniciar Docker Compose: Ejecuta el comando para levantar ambos contenedores:

## docker-compose up -d

Este comando descarga las imágenes necesarias, crea los contenedores y los inicia en
segundo plano.
Acceso a PgAdmin:
• Abre el navegador e ingresa http://localhost:5050.
• Inicia sesión en PgAdmin con las credenciales configuradas (admin@admin.com y
admin123).
• Agregar Servidor de PostgreSQL: En PgAdmin, agrega un servidor PostgreSQL:
o Nombre: Usa un nombre de referencia (ej. Local PostgreSQL).
o Host name/address: Especifica postgres (nombre del contenedor PostgreSQL).
o Username y Password: Usa las credenciales (admin y admin123).
Pruebas y Confirmación de Conexión:
• Una vez conectado, puedes ver y gestionar la base de datos mydatabase y realizar
consultas o configuraciones adicionales.
