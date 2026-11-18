# pdf-extraction-service

Microservicio stateless que extrae el texto de un PDF y lo devuelve en Markdown liviano o en texto plano.

Expone `POST /extract`: recibe el PDF como cuerpo binario o como `multipart/form-data` y responde `{"content": "...", "page_count": N}`. Escucha en el puerto `8001`, no guarda estado y usa PyMuPDF para la extracción.

## Dependencias

PyMuPDF está en la 2.1, una versión mayor: con la 1.28.2 y con la 2.1, los 4 PDFs de prueba dan el mismo `content` y `page_count`. La 2.x incorpora pymupdf4llm y suma dependencias que el servicio no usa, como onnxruntime y numpy, que agrandan la imagen unos 150 MB; Trivy no informó vulnerabilidades en ellas.

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
