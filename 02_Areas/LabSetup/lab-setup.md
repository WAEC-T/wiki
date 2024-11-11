### Lab Setup

### Setting Up Raspberry Pi 5 (aarch64)

**Persistent Storage and Folder Structure**

- Persistent storage is located at `/media/persist`.
- Docker images are stored under `/media/persist/docker`.
- Environment configuration (`env.prod`) and Docker Compose files (`compose-files.yml`) are saved in `/media/persist/setup`.
- Rename `compose-prod.yml` to follow the format `application-name-compose-prod.yml` for better organization.