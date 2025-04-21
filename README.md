# 🧩 NGINX Configs – project-1.0.0

This repository contains custom configuration files for an NGINX server that is part of the Docker environment for the `project-1.0.0`. It is designed to route traffic properly to frontend and backend (API) services within a container network.

---

## 📁 Included Files

```
nginx/
├── frontend.conf   # Configuration to route requests to the frontend
└── api.conf        # Configuration to route requests to the API (orchestrator)
```

---

## 🔧 Usage

These configurations are meant to be mounted into the NGINX container as volumes in a Docker Compose setup. Example:

```yaml
services:
  nginx:
    image: nginx:alpine
    container_name: nginx-project-1.0.0
    volumes:
      - ./nginx/frontend.conf:/etc/nginx/conf.d/frontend.conf
      - ./nginx/api.conf:/etc/nginx/conf.d/api.conf
    ports:
      - "80:80"
    networks:
      - network-project-1.0.0
```

---

## 🧠 Requirements

- Docker and Docker Compose installed
- Internal Docker network (`network-project-1.0.0`)
- Services referenced in the configs (such as `sur-ticket` or `orchestrator`) must be defined in `docker-compose.yml`

---

## 📌 Notes

- If using relative paths, run `docker-compose` from the root of the project.
- Use `resolver 127.0.0.11` if resolving services inside the Docker network.

---

## 🛠 Author

This repository is maintained as part of the service ecosystem for the `project-1.0.0`.
