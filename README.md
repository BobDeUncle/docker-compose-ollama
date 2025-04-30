# Ollama Docker Setup

This repository contains a Docker Compose configuration for running [Ollama](https://ollama.ai/) with automatic updates via Watchtower.

## Overview

Ollama is an open-source framework for running large language models (LLMs) locally.

## Prerequisites

- [Docker](https://docs.docker.com/get-docker/) and [Docker Compose](https://docs.docker.com/compose/install/)
- NVIDIA GPU with [NVIDIA Container Toolkit](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html) installed (for GPU acceleration)

## Installation

1. Clone this repository:
   ```bash
   git clone https://github.com/BobDeUncle/docker-compose-ollama.git
   cd docker-compose-ollama
   ```

2. Start the containers:
   ```bash
   docker compose up -d
   ```

3. Verify installation:
   ```bash
   docker ps
   ```

You should see both the Ollama and Watchtower containers running.

## Usage

### Accessing Ollama

Ollama is accessible on port 11434. You can interact with it using:

- The [Ollama CLI client](https://github.com/ollama/ollama#client-usage)
   - My docker-compose configuration can be found [here](https://github.com/BobDeUncle/docker-compose-ollamawebui)
- Ollama's REST API
- Compatible UI applications like [OpenWebUI](https://github.com/open-webui/open-webui)
   - My docker-compose configuration can be found [here](https://github.com/BobDeUncle/docker-compose-openwebui)

## Configuration

### Customize the `docker-compose.yml`

- **Port**: The default port is 11434. Change `11434:11434` if you need a different port mapping.
- **Volume**: Models and data are stored in the `ollama-data` volume. You can modify this or use a bind mount instead.
- **GPU Settings**: The configuration includes GPU support. Remove the `deploy` section if you don't have a compatible GPU.
- **Watchtower**: Update polling interval can be adjusted via the `WATCHTOWER_POLL_INTERVAL` environment variable (in seconds).

## Maintenance

### Updating

The Watchtower container automatically checks for updates to the Ollama image every 15 minutes and applies them if available.

To manually update:
```bash
docker compose pull
docker compose up -d
```

## License

This Docker Compose setup is provided under the MIT License. Ollama itself has its own licensing terms, which can be found at [ollama.ai](https://ollama.ai/).

## Additional Resources

- [Ollama Documentation](https://github.com/ollama/ollama/tree/main/docs)
- [Ollama Models Library](https://ollama.ai/library)
- [Docker Documentation](https://docs.docker.com/)
- [NVIDIA Container Toolkit Documentation](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/overview.html)
