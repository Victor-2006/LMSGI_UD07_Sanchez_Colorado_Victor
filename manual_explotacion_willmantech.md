# Manual de Explotacion WillmanTech S.L
## Introduccion
Sistema desplegado mediante Docker Compose:

- Odoo ERP
- PostgreSQL
- Servicio web

## Guia de instalacion
docker -compose up -d

## Seguridad
Administrador 
Contable
Comercial

## Backup

docker exec postgres pg_dump -U odoo postgres > backup.sql

## Flujo operativo de facturacion

Usuario crea la factura
Odoo guarda los datos
QWeb genera el HTML
wkhtmltopdf convierte el HTML
PDF se genera