# 🚀 Reverse Proxy System with Docker & Nginx

Hi! 👋 I'm Karan, and this is my submission for the DevOps intern assignment. The goal was to set up two backend services behind an Nginx reverse proxy using Docker Compose—and I went a little further with health checks, clean logs, and modular setup.

---

## 🔧 What I Built

This setup runs **two backend services** (Go & Python Flask) and an **Nginx reverse proxy** that routes requests like this:

- `/service1` → Go service (port 8001)
- `/service2` → Flask service (port 8002)

Everything runs in containers and is spun up with one command.

---

## 🧪 How to Run It

If you have Docker and Docker Compose installed, just run:

```bash
docker compose up --build
```
Wait a few seconds and you’ll have:

Go service running at localhost:8080/service1
Flask service running at localhost:8080/service2

Test it out:
```
curl http://localhost:8080/service1/ping
# {"status": "ok", "service": "1"}

curl http://localhost:8080/service2/hello
# {"message": "Hello from Service 2"}
```
---
## 🌐 How Routing Works

Nginx is configured to:

- Proxy /service1 → service_1 container (Go app)
- Proxy /service2 → service_2 container (Flask app)

it also logs every request with timestamps and URL's. So you'll see clean logs in real-time when requests hit the proxy.

---
## ✅ Bonus Features

- 🩺 Health Checks
Docker keeps an eye on both services. If one goes down, it reports unhealthy.
- 📄 Custom Logs
Nginx logs every incoming request in the format:
[$time_local] $request_uri
- 🧪 Test Script
Run ./test.sh to automatically check that both services are responding.
---
## 🧼 Tech Notes

- Nginx runs inside a container (not on host).
- All services use bridge networking.
- Clean separation of Dockerfiles and config for maintainability.
- Used uv (by Astral) for Python dependency management and modern packaging.
---
💬 Reflections

This project helped me practice real-world container orchestration. Debugging container health checks, handling Go modules, and integrating uv for Python was a great learning experience.

🤝 Thanks for Reviewing!

If you have any feedback, I’d love to hear it.
Looking forward to the opportunity!

