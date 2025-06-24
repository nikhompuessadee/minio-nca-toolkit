# MinIO + NCA Toolkit Deployment

This stack includes:

- **MinIO**: S3-compatible object storage
- **NCA Toolkit**: No-Code Architect tool
- **Cloudflare Tunnel**: Secure public access

## 🚀 How to Start

```bash
docker-compose up -d


🔐 Default Credentials
MinIO:

URL: http://localhost:4000

User: admin

Pass: changme

NCA Toolkit:

URL: http://localhost:8080

Uses MinIO internally via S3-like credentials

⚙ Notes
Uses named nca-network for internal communication

Mounts persistent volumes under /data/nca-toolkit

Access to MinIO Console via port 4000, API via 4001

⚙ Notes
No persistent volumes needed

Based on CPU-optimized Kokoro FastAPI image

🗂 Data Persistence
Docker volume baserow_data used for persistent storage

⚙ Notes
BASEROW_PUBLIC_URL is set for tunnel domain
