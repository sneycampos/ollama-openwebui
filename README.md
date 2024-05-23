# Ollama and Open WebUI Docker Setup

This repository contains a `docker-compose.yml` file to run Ollama and Open WebUI using Docker, with support for both GPU and non-GPU setups.

## Prerequisites

- [Docker](https://www.docker.com/get-started)
- [Docker Compose](https://docs.docker.com/compose/install/)

## Getting Started

### Clone the Repository

```bash
git clone https://github.com/sneycampos/ollama-openwebui.git
cd ollama-openwebui
```

### Running the Containers

To start the containers, simply run:
```bash
docker compose up -d
```
This command will start both the Ollama and Open WebUI services.

### GPU Support

If you have a GPU and want to utilize it, ensure that the following lines in the `docker-compose.yml` file are uncommented:

```yaml
deploy:
  resources:
    reservations:
      devices:
        - capabilities: [gpu]
```

If you do not have a GPU, you can comment out these lines.

### Accessing the Services

- **Ollama**: Accessible at `http://localhost:11434`
- **Open WebUI**: Accessible at `http://localhost:8080`

The Open WebUI is configured to interact with Ollama using the environment variable `OLLAMA_BASE_URL`.

## Volumes

This setup uses Docker volumes to persist data:

- `ollama` volume for Ollama's data.
- `open-webui` volume for Open WebUI's data.

## Container Management

To stop the containers, run:

```bash
docker compose down
```

To view the logs of the running containers, use:
```bash
docker compose logs -f
```
