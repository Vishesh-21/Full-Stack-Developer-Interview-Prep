#### What is docker?

> Docker is a containerization platform that lets you package an application and all its dependencies (libraries, configs, runtime) into a lightweight, portable container so it runs the same everywhere — on your laptop, a server, or the cloud.

#### Why docker is used?

> No “works on my machine” problem
> Lightweight & fast
> Easy deployments : You can ship a Docker image to any server and run it instantly.
> Scalable : Used heavily in DevOps, CI/CD, Kubernetes, cloud apps.

#### How docker works?

> Docker works by using Linux features to isolate and run applications in lightweight containers. It mainly uses:
>
> 1. Namespaces → Provide isolation.
>    Each container gets its own processes, network, hostname, and filesystem so it behaves > like a separate system.
> 2. Cgroups (Control Groups) → Manage resources.
>    They limit how much CPU, RAM, and I/O a container can use.
> 3. Union File System (Layered Images) → Efficient storage.
>    Docker images are built in layers, which makes them fast to build and reuse.
> 4. Docker Daemon → The main service.
>    It builds images, runs containers, manages networks, and handles storage.
>    In simple words:
>    Docker runs your app as an isolated process using the host’s OS, not a full virtual machine. This makes containers fast, lightweight, and consistent everywhere.

#### What is difference between Docker and VM ?

| Feature         | Docker        | VM            |
| --------------- | ------------- | ------------- |
| Startup time    | ~1 sec        | 20–60 sec     |
| Size            | MBs           | GBs           |
| OS per instance | ❌ No         | ✔ Yes         |
| Performance     | Near-native   | Slower        |
| Isolation       | Process-level | Full OS-level |
| Resource usage  | Low           | High          |

#### What is a Docker File?

> A docker file is a simple text file with instruction to build an docker image.

#### What is Docker Image?

> A Docker image is a blueprint/template for your application.It contains: Your app code, Dependencies, Libraries, Runtime, System tools, configurations. It is read-only and used to create containers.

#### What is a Docker Container?

> A Docker container is a running instance of a Docker image. It is: Lightweight, Isolated, Starts instantly,Uses the host OS kernel.

#### What is a Docker Network ?

> A Docker network allows containers to communicate with each other, with the host machine, or with the outside internet. It creates virtual networks inside Docker so containers can talk safely and reliably.
> Docker Network = A private network created for containers to communicate.

#### What is Docker Hub?

> Docker Hub is a public online registry where Docker images are stored and shared — similar to how GitHub stores code. To Download ready-made images, Upload your own application images.

#### What is Docker Compose?

> Docker Compose is a tool that lets you run multiple Docker containers together using one configuration file (docker-compose.yml).

#### Why use Docker Compose?

| Benefit                                  | Explanation                            |
| ---------------------------------------- | -------------------------------------- |
| Start multiple containers with 1 command | `docker-compose up`                    |
| Easy environment setup for a team        | Same config runs everywhere            |
| Containers can talk to each other        | Compose creates internal networking    |
| Good for development and testing         | Quickly spin up full stack environment |

#### Docker Commands

1. **Image Commands**
   | Command | Description |
   | --------------------------------- | -------------------------------------- |
   | `docker pull <image>` | Download an image from Docker Hub |
   | `docker images` | List all downloaded images |
   | `docker rmi <image>` | Remove an image |
   | `docker build -t <name> .` | Build a Docker image from a Dockerfile |
   | `docker tag <image> <repo>:<tag>` | Tag an image for upload |

2. **Container Commands**
   | Command | Description |
   | ----------------------------------- | --------------------------------------- |
   | `docker run <image>` | Run a container |
   | `docker run -d <image>` | Run container in background (detached) |
   | `docker run -p 3000:3000 <image>` | Map local port to container port |
   | `docker ps` | List running containers |
   | `docker ps -a` | List all containers (running + stopped) |
   | `docker stop <container_id>` | Stop a running container |
   | `docker start <container_id>` | Start a container again |
   | `docker rm <container_id>` | Remove a stopped container |
   | `docker logs <container_id>` | View container logs |
   | `docker exec -it <container_id> sh` | Open shell terminal inside container |

3. **Useful Combined Commands**
   | Command | Use |
   | --------------------------- | ------------------------------------------- |
   | `docker run -it ubuntu` | Run Ubuntu container and open its shell |
   | `docker exec -it <id> bash` | Execute bash shell inside running container |
   | `docker logs -f <id>` | Stream logs in real-time |

4. **Docker Compose Commands**
   | Command | Description |
   | ------------------------ | -------------------------- |
   | `docker compose up` | Start all containers |
   | `docker compose up -d` | Start in background |
   | `docker compose down` | Stop and remove containers |
   | `docker compose ps` | List compose services |
   | `docker compose logs -f` | View logs |

5. **Cleanup / System Commands**
   | Command | Description |
   | -------------------------------- | --------------------------------------- |
   | `docker system prune` | Remove unused containers, images, cache |
   | `docker stop $(docker ps -q)` | Stop all running containers |
   | `docker rm $(docker ps -aq)` | Remove all containers |
   | `docker rmi $(docker images -q)` | Remove all images |
