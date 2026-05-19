# Manual de Explotacion WillmanTech S.L
## Introducción y Arquitectura
Sistema desplegado mediante Docker Compose:

- Odoo ERP
- PostgreSQL
- Servicio web

## Guía de Instalación y Reinstalación
docker -compose up -d

## Seguridad y Control de Acceso
Administrador 
Contable
Comercial

## Procedimiento de Backup y Restauración

docker exec postgres pg_dump -U odoo postgres > backup.sql

## Flujo Operativo de Facturación e Informes

Usuario crea la factura
Odoo guarda los datos
QWeb genera el HTML
wkhtmltopdf convierte el HTML
PDF se genera