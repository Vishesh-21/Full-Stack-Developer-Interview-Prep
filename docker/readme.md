#### What is docker?

> Docker is a containerization platform that lets you package an application and all its dependencies (libraries, configs, runtime) into a lightweight, portable container so it runs the same everywhere — on your laptop, a server, or the cloud.

#### Why docker is used?

> No “works on my machine” problem
> Lightweight & fast
> Easy deployments : You can ship a Docker image to any server and run it instantly.
> Scalable : Used heavily in DevOps, CI/CD, Kubernetes, cloud apps.

#### How docker works?
> Docker works by using Linux features to isolate and run applications in lightweight containers. It mainly uses:
>   1. Namespaces → Provide isolation.
> Each container gets its own processes, network, hostname, and filesystem so it behaves > like a separate system.
>   2. Cgroups (Control Groups) → Manage resources.
> They limit how much CPU, RAM, and I/O a container can use.
>   3. Union File System (Layered Images) → Efficient storage.
> Docker images are built in layers, which makes them fast to build and reuse.
> 4. Docker Daemon → The main service.
> It builds images, runs containers, manages networks, and handles storage.
> In simple words:
> Docker runs your app as an isolated process using the host’s OS, not a full virtual machine. This makes containers fast, lightweight, and consistent everywhere.

#### What is difference between Docker and VM ?
| Feature         | Docker        | VM            |
| --------------- | ------------- | ------------- |
| Startup time    | ~1 sec        | 20–60 sec     |
| Size            | MBs           | GBs           |
| OS per instance | ❌ No          | ✔ Yes         |
| Performance     | Near-native   | Slower        |
| Isolation       | Process-level | Full OS-level |
| Resource usage  | Low           | High          |

#### What is Docker Image?
> A Docker image is a blueprint/template for your application.It contains: Your app code, Dependencies, Libraries, Runtime, System tools, configurations. It is read-only and used to create containers.

#### What is a Docker Container?
> A Docker container is a running instance of a Docker image. It is: Lightweight, Isolated, Starts instantly,Uses the host OS kernel.

#### What is a Docker Network ?
> A Docker network allows containers to communicate with each other, with the host machine, or with the outside internet. It creates virtual networks inside Docker so containers can talk safely and reliably.
> Docker Network = A private network created for containers to communicate.