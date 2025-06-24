# DevOps Intern Assignment

## Setup Instructions
1. Clone repository: `git clone https://github.com/yourusername/devops-assignment.git`
2. Build and start containers: `docker-compose up --build`
3. Access services:
   - Service 1: http://localhost:8080/service1/ping
   - Service 2: http://localhost:8080/service2/ping

## Routing
- Nginx reverse proxy routes:
  - `/service1` → Go service (port 8001)
  - `/service2` → Python service (port 8002)
- All services accessible through port 8080

## Features
- **Health Checks**: Services monitored with curl-based health checks
- **Logging**: Timestamped request logging in Nginx
- **Bridge Networking**: All containers on custom bridge network
- **Single Command Setup**: `docker-compose up --build`

## Verification
1. Check health status: `docker ps --filter "health=healthy"`
2. View logs: `docker-compose logs`
3. Test endpoints:
   ```bash
   curl http://localhost:8080/service1/ping
   curl http://localhost:8080/service2/hello