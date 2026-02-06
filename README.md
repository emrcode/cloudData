# cloudData
Local Kafka practice environment using Confluent (Apache Kafka) containers via Docker Compose. This setup is designed to run on Windows with Docker Desktop. It can be committed to GitHub as a reusable lab project.

## Prerequisites
- Windows 10/11 with [Docker Desktop](https://www.docker.com/products/docker-desktop/) installed
- Git

## Quick Start (Windows)
```powershell
git clone https://github.com/emrcode/cloudData.git
cd cloudData
docker compose up -d
docker compose ps
```

Kafka will be available on:
- `localhost:9092` (host access)

## Create a Topic and Test
```powershell
docker exec -it kafka kafka-topics --create --topic demo-topic --bootstrap-server localhost:9092 --partitions 1 --replication-factor 1
```

Start a consumer:
```powershell
docker exec -it kafka kafka-console-consumer --topic demo-topic --bootstrap-server localhost:9092 --from-beginning
```

In another terminal, start a producer:
```powershell
docker exec -it kafka kafka-console-producer --topic demo-topic --bootstrap-server localhost:9092
```

## Stop the Environment
```powershell
docker compose down
```

## Notes
- The Docker Compose file uses Confluent images for Apache Kafka.
- You can keep this repository in GitHub to track changes to your local practice environment.
