# Redis Docker Compose Setup

This project provides a simple and reusable **Redis** server deployment using **Docker Compose**. It is configured for development and production environments where persistence, configurability, and security are required.

---

## 📦 Services

### Redis Server
- **Image:** `redis:latest`
- **Container Name:** `redis`
- **Restart Policy:** Always
- **Ports:** Exposes port `6379` to the host.
- **Volumes:**
  - `redis-data` for persistent Redis data storage.
  - `redis-config` for Redis configuration files.

---

## 🚀 Getting Started

### Prerequisites
Make sure you have the following installed:
- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/)

### How to Run
1. Clone the repository:
    ```bash
    git clone https://github.com/cynegeirus/docker-redis.git
    cd redis-docker-compose
    ```

2. Update the password in `docker-compose.yml`:
    ```yaml
    environment:
      - REDIS_PASSWORD=YOUR_SECURE_PASSWORD
    ```

3. Start the services:
    ```bash
    docker-compose up -d
    ```

4. Redis will be available at:
    ```
    redis://localhost:6379
    ```

---

## 🔐 Authentication

You must provide the Redis password when connecting:
```bash
redis-cli -h localhost -p 6379 -a YOUR_SECURE_PASSWORD
````

Make sure to replace `YOUR_SECURE_PASSWORD` with your configured password.

---

## 📂 Volumes

* `redis-data`: Stores Redis persistent data to prevent data loss when the container is restarted.
* `redis-config`: Stores Redis configuration files if you want to customize the Redis server settings.

---

## ⚙️ Configuration

You can add your custom Redis configuration files into the `redis-config` volume. Update the Redis startup command if you need to load a specific configuration file.

---

## 📌 Notes

* The default number of databases is set to **16**.
* The `REDIS_PASSWORD` environment variable does not configure the Redis password directly. You need to mount a custom configuration file with the `requirepass` directive or use the official Redis `--requirepass` argument in the command section.

Example:

```yaml
command: ["redis-server", "--requirepass", "YOUR_SECURE_PASSWORD"]
```

---

## ✅ Best Practices

* Always use a strong password in production environments.
* Consider restricting external access to the Redis port using firewall rules.
* For advanced setups, configure persistence and security settings through a custom Redis configuration file.

---

## 📚 References

* [Redis Documentation](https://redis.io/documentation)
* [Docker Hub - Redis](https://hub.docker.com/_/redis)
* [Docker Compose Documentation](https://docs.docker.com/compose/)

---

## 📜 License

This project is licensed under the [MIT License](LICENSE). See the license file for details.

---

## 🙌 Issues, Feature Requests or Support

Please use the Issue > New Issue button to submit issues, feature requests or support issues directly to me. You can also send an e-mail to akin.bicer@outlook.com.tr.
