ZenML

# Check ZenML status
poetry run zenml status
# Connect to ZenML
poetry run zenml connect
poetry run zenml disconnect
# Stack management
poetry poe set-local-stack
poetry poe set-aws-stack
# Export/Import settings
poetry poe export-settings-to-zenml
poetry poe delete-settings-zenml

MONGO DB
# MongoDB Connection URI
mongodb://llm_engineering:llm_engineering@127.0.0.1:27017
# Database Info
Database name: twin
Username: llm_engineering
Password: llm_engineering
# Export/Import data warehouse
poetry poe run-export-data-warehouse-to-json
poetry poe run-import-data-warehouse-from-json

QDRANT
# Qdrant URLs
REST API: localhost:6333
Dashboard: localhost:6333/dashboard

INFRA MANAGEMENT
# Check running containers
podman ps
podman ps -a  # shows all containers, including stopped ones
# Container logs
podman logs <container_id>
# Enter container shell
podman exec -it <container_id> bash
# Clean up
podman system prune  # clean up unused resources
## Local infrastructure
local-docker-infrastructure-up = "podman compose up -d"
local-docker-infrastructure-down = "podman compose stop"
local-zenml-server-down = "poetry run zenml down"
local-infrastructure-up = [
    "local-docker-infrastructure-up",
    "local-zenml-server-down",
    "local-zenml-server-up",
]
local-infrastructure-down = [
    "local-docker-infrastructure-down",
    "local-zenml-server-down",
]