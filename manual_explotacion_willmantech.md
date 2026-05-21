# Manual de Explotacion WillmanTech S.L
## Introducción y Arquitectura
Sistema desplegado mediante Docker Compose:

Modulos activados:

- Gestion de clientes (CRM)
- Facturación
- Ventas
- Informes QWeb
- Gestion de usuarios

Topologia:

Usuario
    ↓
Interfaz usuario
    ↓
Servidor Web Odoo
    ↓
Servidor ERP
    ↓
Base de datos PostgreSQL



## Guía de Instalación y Reinstalación
Necesitas:

- Docker
- Docker Compose
- PostgreSQL
- Navegador web

Variables de entorno:

HOST=localhost

DB_USER=odoo

DB_PASSWORD=odoo

DB_NAME=postgres

Proceso de instalacion:
1. Crear el docker-compose.yml
2. Lo creas con esas variables y las demas cosas que le quieras meter al contenedor
3. Ejecutas el yml
4. Utiliza docker -compose up -d
5. Verifica que los contenedores esten activos con docker ps
6. Abres odoo en el navegador con el puerto que le hayas puesto

## Seguridad y Control de Acceso
Administrador: Tiene el control de todo el sistema y puede gestionar los usuarios

Contable: Gestiona las facturas y los informes finacieros

Comercial: Gestiona los clientes y las ventas

Politicas de seguridad:

- Contraseñas de minimo 8 caracteres
- Renovacion de la contraseña periodica
- Acceso restringido por permisos
- Gestion de privilegios segun rol

## Procedimiento de Backup y Restauración
Procedimiento para copia de seguridad

docker exec postgres pg_dump -U odoo postgres > backup.sql

Procedimiento para restaurar:

docker exec -i postgres psql -U odoo postgres < backup.sql

Recomendacion:
- Realizar copias diarias
- Almacenar copias externas
- Verificar periodicamente la integridad

## Flujo Operativo de Facturación e Informes

1. El usuario accede al modulo de Facturación
2. Se crea la nueva factura
3. Se selecciona cliente y productos
4. Odoo almacena los datos PostgreSQL
5. El motor QWeb procesa la plantilla XML
6. Se genera una representacion HTML
7. wkhtmltopdf convierte HTML a PDF
8. El PDF final se muestra o se descarga para el usuario

Es decir:

Factura --> QWeb --> HTML --> wkhtmltopdf --> PDF