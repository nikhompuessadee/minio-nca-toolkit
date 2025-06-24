# 🧰 MinIO + NCA Toolkit Deployment

This project provides a complete Docker Compose setup for:

- 📦 **MinIO** – An S3-compatible object storage server
- 🧱 **NCA Toolkit** – No-Code Architect Toolkit (uses S3 backend)
- ☁️ **Cloudflare Tunnel** – For secure public access

---

## 🔧 Setup Instructions

### 1. Clone the repository

```bash
git clone https://github.com/yourusername/your-repo.git
cd minio-nca-toolkit
2. Create your configuration file
bash
Copy
Edit
cp docker-compose.yml.example docker-compose.yml
3. Edit the docker-compose.yml
Replace the following placeholders:

Placeholder	Description
MINIO_ROOT_PASSWORD	Root password for MinIO Console
TUNNEL_TOKEN	Cloudflare Tunnel token
API_KEY	Key for NCA Toolkit authentication
S3_ACCESS_KEY	Access key for S3 (MinIO)
S3_SECRET_KEY	Secret key for S3 (MinIO)

🚀 Start the stack
bash
Copy
Edit
docker-compose up -d
Verify containers are running:

bash
Copy
Edit
docker ps
🌐 Access
Service	URL/Port	Notes
MinIO Console	http://localhost:4000	S3 UI
MinIO API	http://localhost:4001	S3-compatible endpoint
NCA Toolkit	http://localhost:8080	API and Admin Dashboard
Cloudflare	Your public tunnel URL	Check logs/dashboard

🔐 Default Credentials (Example)
text
Copy
Edit
MinIO:
  - Username: admin
  - Password: changeme

NCA Toolkit:
  - API_KEY: changeme
⚠️ Do not use these values in production. Always replace with secure secrets.

📁 Storage & Volumes
./volume/ → MinIO bucket data (S3)

/data/nca-toolkit/logs → Toolkit logs

/data/nca-toolkit/config → Toolkit configuration

/data/nca-toolkit/temp → Temp storage

📦 Docker Network
All services use a dedicated Docker bridge network named nca-network to communicate securely.

🛡 Recommendations
✅ Add docker-compose.yml to .gitignore

✅ Keep real secrets in environment variables or secrets manager

✅ Backup /volume and /data/nca-toolkit/ periodically

📚 Resources
MinIO Docs

NCA Toolkit DockerHub

Cloudflare Tunnel Docs

