# pdf-extraction-service

Microservicio stateless que extrae el texto de un PDF y lo devuelve en Markdown liviano o en texto plano.

Expone `POST /extract`: recibe el PDF como cuerpo binario o como `multipart/form-data` y responde `{"content": "...", "page_count": N}`. Escucha en el puerto `8001`, no guarda estado y usa PyMuPDF para la extracción.

## Tests

Requiere Python 3.11 o superior y [uv](https://docs.astral.sh/uv/).

```bash
uv sync
uv run pytest -q
```

Los tests no necesitan Docker.

## Despliegue

Este servicio se despliega desde [VickySB23/pdf-extractext-microservicios](https://github.com/VickySB23/pdf-extractext-microservicios), que contiene el `docker-compose.yml` con Traefik, Consul y MongoDB, la documentación y las pruebas de carga.

## Origen

Este repositorio surge de separar la carpeta `services/extraction-service` de [VickySB23/pdf-extractext-microservicios](https://github.com/VickySB23/pdf-extractext-microservicios), conservando su historial, para que cada microservicio tenga su propio repositorio.
