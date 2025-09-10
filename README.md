# 🚀 Docker Reverse Proxy & Load Balancing Project

## 📌 Context

Docker is a platform that allows you to **containerize your applications**, packaging them into portable, self-contained environments that can run anywhere.
This means you can move your application from local development to a server without worrying about dependencies or configuration issues.

Docker achieves this by using **containers**, which are lightweight, isolated environments containing everything an application needs:
- Libraries
- Dependencies
- Configurations

Containers can be started/stopped quickly and scaled easily, making them ideal for modern software development.

In this project, we will build an **infrastructure** that includes:
- A **reverse proxy** (entry point)
- A **load balancer** (distributing requests)
- Two **application servers**
- One **front-end static-content server**

---

## 🏗️ High-Level Design

The architecture looks like this:

- **Reverse Proxy / Load Balancer**:
  - Routes traffic to the correct service (front-end or API).
  - Balances requests between the two API servers using **Round Robin**.

- **Front-End Server**:
  - Serves static content (HTML, CSS, JS, images).
  - The client never directly communicates with this server — it goes through the proxy.

- **API Servers (x2)**:
  - Handle requests requiring backend logic.
  - The proxy balances traffic between them.

🔄 **Round Robin Load Balancing**:
- Requests are distributed sequentially across servers.
- Example with 3 servers (A, B, C):
  1st request → A
  2nd request → B
  3rd request → C
  4th request → A … and so on.

This ensures each server shares the load fairly.

---

## ✅ Prerequisites

Before starting, make sure you have:

- Installed **Docker Desktop** on your local machine:
  👉 [Download Docker](https://www.docker.com/)

Installation guides:
- [Windows](https://docs.docker.com/desktop/install/windows-install/)
- [Mac](https://docs.docker.com/desktop/install/mac-install/)
- [Linux](https://docs.docker.com/desktop/install/linux/)
- Chromebook (⚠️ limited support, prefer Windows/Mac/Linux)

---

## 📚 Useful Resources

- [Docker Tutorial](https://docs.docker.com/get-started/)
- [Docker Cheatsheet](https://docs.docker.com/get-started/docker_cheatsheet.pdf)
- [Proxy vs Reverse Proxy (examples)](https://www.cloudflare.com/learning/cdn/glossary/reverse-proxy/)
- [Reverse Proxy Explained (video, stop at 06:25)](https://www.youtube.com/watch?v=Yy6BfM3JYRY)

---

## ⚙️ What You Will Build

By the end of this project, you will have:
- A working **Dockerized infrastructure** with multiple containers.
- A **reverse proxy & load balancer** that routes traffic correctly.
- Two API servers serving requests in **Round Robin** fashion.
- A front-end server serving static files.
- A scalable setup, ready to extend with Docker Compose or orchestration tools.

---

## 🛠️ Project Steps

1. **Setup Dockerfiles** for each service (proxy, API servers, front-end).
2. **Configure Docker Compose** to define and run all containers.
3. **Setup Nginx (or HAProxy)** as reverse proxy + load balancer.
4. **Verify routing**:
   - `/` → Front-end server
   - `/api/...` → API servers (load balanced)
5. **Test scalability** by scaling API servers.

---

## 📦 Running the Project

```bash
# Clone repository
git clone <your-repo-link>
cd <project-folder>

# Build and run all containers
docker-compose up --build

# Stop containers
docker-compose down
