# Docker Certified Associate (DCA) Study Guide

This study guide is designed to help you prepare for the Docker Certified Associate (DCA) certification exam. The DCA exam validates a candidate's skills in Docker EE (Enterprise Edition) and CE (Community Edition) environments, focusing on core Docker platform functionalities.

### 1. Exam Overview

*   **Exam Name:** Docker Certified Associate (DCA)
*   **Duration:** 90 minutes
*   **Number of Questions:** Approximately 55 questions
*   **Format:** Multiple Choice and Discrete Option Multiple Choice (DOMC - scenario-based, choose best solution)
*   **Passing Score:** Typically around 65-70% (score is normalized, not raw percentage)
*   **Proctoring:** Online proctored or at a testing center.
*   **Prerequisites:** Docker recommends 6-12 months of hands-on experience with Docker.

### 2. Exam Domains & Key Topics

The DCA exam covers six main domains. The percentage next to each domain indicates its approximate weight in the exam. Focus your study efforts accordingly.

---

#### Domain 1: Orchestration (25%)

This domain focuses heavily on **Docker Swarm**. You should be proficient in deploying, managing, and troubleshooting Docker Swarm clusters and services.

*   **Swarm Architecture:**
    *   Understanding manager and worker nodes.
    *   High availability for managers (quorum).
    *   `docker swarm init`, `docker swarm join`.
    *   Troubleshooting `docker swarm` issues.
*   **Services Management:**
    *   `docker service create`, `docker service scale`, `docker service update`, `docker service rm`.
    *   Rolling updates and rollbacks.
    *   Placing constraints and preferences (`--constraint`, `--placement-pref`).
    *   Node draining and availability (`docker node update --availability drain`).
    *   Understanding `replicas` and `global` services.
*   **Stacks and Compose:**
    *   Deploying applications using `docker stack deploy` and `docker-compose.yml` (version 3 syntax).
    *   Managing multiple services with a stack.
    *   Secrets and Configs integration with services.
*   **Troubleshooting:**
    *   Identifying issues with services, tasks, and nodes.
    *   Using `docker service logs`, `docker service ps`, `docker node ls`, `docker event`.

**Key Commands to Master:**
`docker swarm`, `docker node`, `docker service`, `docker stack`

---

#### Domain 2: Image Creation, Management, and Registry (20%)

This domain covers the entire lifecycle of Docker images, from creation to distribution.

*   **Dockerfile Best Practices:**
    *   `FROM`, `RUN`, `CMD`, `ENTRYPOINT`, `COPY`, `ADD`, `EXPOSE`, `VOLUME`, `WORKDIR`, `ENV`, `ARG`, `LABEL`.
    *   Understanding the difference between `CMD` and `ENTRYPOINT`.
    *   Optimizing image size (multi-stage builds, reducing layers).
    *   `.dockerignore` file.
    *   Building images (`docker build`).
*   **Image Management:**
    *   Listing images (`docker images`).
    *   Tagging images (`docker tag`).
    *   Removing images (`docker rmi`).
    *   Inspecting images (`docker inspect`).
*   **Registry Interaction:**
    *   Pushing and pulling images from Docker Hub or private registries (`docker push`, `docker pull`).
    *   Logging into and out of registries (`docker login`, `docker logout`).
    *   Understanding image layers and caching.

**Key Commands to Master:**
`docker build`, `docker images`, `docker rmi`, `docker tag`, `docker login`, `docker push`, `docker pull`, `docker inspect`

---

#### Domain 3: Installation and Configuration (15%)

This domain focuses on setting up and configuring the Docker Engine on various operating systems.

*   **Docker Engine Installation:**
    *   Supported operating systems (Ubuntu, CentOS, RHEL, Windows Server).
    *   Installation methods (package managers like `apt`, `yum`).
    *   Post-installation configuration (non-root user access, starting/stopping daemon).
*   **Daemon Configuration (`daemon.json`):**
    *   Setting up logging drivers (json-file, syslog, journald, etc.).
    *   Configuring custom data directories.
    *   Setting up proxy configuration.
    *   Enabling experimental features.
    *   Configuring live-restore.
    *   `systemctl` commands for daemon management (start, stop, enable, restart).
*   **Engine Upgrades:**
    *   Understanding release cycles and upgrade paths.
    *   Performing rolling upgrades in a Swarm.
*   **Cgroups & Namespaces:**
    *   Basic understanding of how Docker uses these Linux kernel features for isolation.

**Key Concepts/Commands to Master:**
`daemon.json`, `systemctl`, `apt/yum install docker-ce`, `dockerd` (daemon process)

---

#### Domain 4: Networking (15%)

This domain covers different Docker networking drivers and how to manage connectivity between containers and services.

*   **Network Drivers:**
    *   `bridge`: Default network for standalone containers.
    *   `host`: Container shares host's network namespace.
    *   `none`: Container has no network interfaces.
    *   `overlay`: For Swarm services, enabling communication across nodes.
    *   `macvlan`: Assigns a MAC address to a container, making it a "first-class citizen" on the physical network.
*   **Custom Networks:**
    *   Creating and managing custom networks (`docker network create`, `docker network ls`, `docker network rm`).
    *   Connecting containers to custom networks (`docker network connect`).
    *   Understanding `--subnet` and `--gateway` options.
*   **Service Discovery:**
    *   DNS-based service discovery in Swarm (using service names).
    *   Publishing ports (`-p` for containers, `--publish` for services).
    *   Ingress network in Swarm.
*   **Troubleshooting:**
    *   Using `docker network inspect` to diagnose network issues.
    *   `docker exec` into containers for `ping`, `ip addr`, `netstat`.

**Key Commands to Master:**
`docker network`, `docker container run --network`, `docker service create --publish`

---

#### Domain 5: Security (15%)

This domain focuses on securing Docker deployments, including images, daemon, and runtime.

*   **Docker Content Trust (DCT):**
    *   Enabling and disabling DCT (`DOCKER_CONTENT_TRUST=1`).
    *   Understanding image signing and verification.
*   **Secrets and Configs:**
    *   Managing sensitive data using `docker secret create`, `docker secret ls`, `docker secret rm`.
    *   Managing non-sensitive configuration data using `docker config create`, `docker config ls`, `docker config rm`.
    *   Integrating secrets/configs with services.
*   **Daemon Security:**
    *   Restricting Docker daemon access.
    *   TLS authentication for client-daemon communication.
    *   User namespaces for rootless containers.
    *   CIS Docker Benchmarks (awareness of security best practices).
*   **Runtime Security:**
    *   `--privileged` flag (avoiding its use).
    *   Capability dropping (`--cap-drop`).
    *   Read-only root filesystems (`--read-only`).
    *   SELinux/AppArmor integration (basic understanding).
    *   Using non-root users in containers.

**Key Commands/Concepts to Master:**
`docker secret`, `docker config`, `DOCKER_CONTENT_TRUST`, `daemon.json` (security settings), `--user`, `--read-only`

---

#### Domain 6: Storage (10%)

This domain covers persistent data management for Docker containers and services.

*   **Volumes:**
    *   Creating and managing named volumes (`docker volume create`, `docker volume ls`, `docker volume rm`).
    *   Using volumes with containers (`-v <volume_name>:<container_path>`).
    *   Sharing volumes between containers.
    *   Volume drivers (basic understanding).
*   **Bind Mounts:**
    *   Mounting host directories into containers (`-v <host_path>:<container_path>`).
    *   Understanding the difference between volumes and bind mounts.
*   **`tmpfs` mounts:**
    *   Using temporary in-memory file systems for non-persistent data.
    *   `--tmpfs` option.
*   **Storage Best Practices:**
    *   Choosing the appropriate storage solution.
    *   Inspecting volume details (`docker volume inspect`).

**Key Commands to Master:**
`docker volume`, `docker container run -v`, `docker service create --mount`

---

### 3. Recommended Study Resources

*   **Official Docker Documentation:** This is your primary source of truth.
    *   [docs.docker.com](https://docs.docker.com/)
    *   Pay special attention to Swarm, Networking, Storage, and Security sections.
*   **Docker Certified Associate (DCA) Exam Guide:** The official exam guide outlines the topics.
    *   Search for "Docker Certified Associate Exam Guide"
*   **Online Courses:**
    *   **Udemy:** Look for courses by Bret Fisher ("Docker & Kubernetes: The Practical Guide," "Docker Swarm" specific courses) or Mumshad Mannambeth (KodeKloud).
    *   **Pluralsight / A Cloud Guru:** Offer comprehensive Docker learning paths.
    *   **Linux Academy (now A Cloud Guru):** Often has good lab-focused courses.
*   **Books:**
    *   "Docker Deep Dive" by Nigel Poulton (highly recommended for foundational knowledge).
*   **Practice Labs / Environment:**
    *   **Play-with-Docker (PWD):** [labs.play-with-docker.com](https://labs.play-with-docker.com/) - excellent for quick sandbox environments.
    *   **Local VMs:** Set up a few Linux VMs (e.g., VirtualBox, VMware) to create a multi-node Swarm cluster. This is crucial for hands-on practice.
    *   **Docker Desktop:** Good for local development and single-node container practice.
*   **Practice Tests:**
    *   Many online courses include practice tests.
    *   Search for "DCA practice exams" from reputable providers.

### 4. Study Strategy & Tips

1.  **Understand the "Why":** Don't just memorize commands. Understand *why* you use a certain command, `Dockerfile` instruction, or network driver.
2.  **Hands-On Practice (Crucial!):** Docker is a practical skill. You *must* get your hands dirty.
    *   Recreate scenarios from the official docs.
    *   Set up a multi-node Swarm cluster from scratch.
    *   Deploy multi-service applications using `docker-compose.yml` / `docker stack deploy`.
    *   Practice troubleshooting.
3.  **Focus on Swarm:** Orchestration is 25% of the exam. Make sure you are very comfortable with all aspects of Swarm.
4.  **`daemon.json`:** Understand its role and common configurations.
5.  **Networking Drivers:** Know when to use `bridge`, `host`, `overlay`, `macvlan`.
6.  **Security Best Practices:** Be aware of `DOCKER_CONTENT_TRUST`, secrets, and basic container hardening.
7.  **Review `docker inspect`:** This command is invaluable for debugging and understanding container/image/network/volume details.
8.  **Time Management:** 90 minutes for ~55 questions means roughly 1.5 minutes per question. Some questions might be scenario-based and require more thought. Practice pacing yourself.
9.  **Read Questions Carefully:** Pay attention to keywords like "least privilege," "most efficient," "best practice."
10. **Eliminate Wrong Answers:** If you're unsure, try to eliminate obviously incorrect options first.
11. **Bookmark Important Documentation:** During your practice, keep a running list of `docker` commands and `Dockerfile` instructions you find yourself looking up frequently.

### 5. Exam Day Tips

*   **Technical Check:** If taking online, ensure your internet connection is stable, your webcam/microphone work, and your room meets the proctoring requirements.
*   **Comfort:** Be in a quiet environment where you won't be disturbed.
*   **Stay Calm:** If you encounter a difficult question, mark it for review and move on. Don't let it derail your focus.
*   **Time Management:** Keep an eye on the clock. It's better to answer all questions, even if you have to guess on a few, than to leave many unanswered.
