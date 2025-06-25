# 🧰 MinIO + NCA Toolkit Deployment

โปรเจกต์นี้มี Docker Compose setup ที่ครบวงจรสำหรับ:
* 📦 **MinIO** – Object storage server ที่รองรับ S3 API
* 🧱 **NCA Toolkit** – No-Code Architect Toolkit (ใช้ S3 เป็น backend)
* ☁️ **Cloudflare Tunnel** – สำหรับการเข้าถึงแบบ public ที่ปลอดภัย

---

## 🔧 Setup Instructions

### 1. Clone the repository

เริ่มต้นด้วยการ Clone โค้ดโปรเจกต์นี้ลงมาที่เครื่องของคุณ:

```bash
git clone [https://github.com/nikhompuessadee/minio-nca-toolkit.git](https://github.com/nikhompuessadee/minio-nca-toolkit.git)
cd minio-nca-toolkit

2. Create your configuration file
คัดลอกไฟล์ docker-compose.yml.example เพื่อสร้างไฟล์ .yml สำหรับการตั้งค่าของคุณ:

cp docker-compose.yml.example docker-compose.yml

3. Edit the docker-compose.yml
เปิดไฟล์ docker-compose.yml ที่คุณสร้างขึ้นมา และแทนที่ค่า Placeholder ต่อไปนี้ด้วยข้อมูลของคุณ:

Placeholder	Description
MINIO_ROOT_PASSWORD	รหัสผ่านสำหรับ MinIO Console
TUNNEL_TOKEN	Cloudflare Tunnel token
API_KEY	Key สำหรับการยืนยันตัวตนของ NCA Toolkit
S3_ACCESS_KEY	Access key สำหรับ S3 (MinIO)
S3_SECRET_KEY	Secret key สำหรับ S3 (MinIO)

Export to Sheets

4. Start the stack
หลังจากตั้งค่าเรียบร้อยแล้ว ให้เริ่มบริการทั้งหมดด้วย Docker Compose:

docker-compose up -d
คุณสามารถตรวจสอบสถานะของ Container ที่กำลังรันอยู่ได้ด้วยคำสั่ง:

docker ps


🌐 Access
นี่คือ URL/Port สำหรับเข้าถึงแต่ละบริการ:

Service	URL/Port	Notes
MinIO Console	http://localhost:4000	S3 UI
MinIO API	http://localhost:4001	S3-compatible endpoint
NCA Toolkit	http://localhost:8080	API and Admin Dashboard
Cloudflare	Your public tunnel URL	ตรวจสอบใน logs/dashboard

Export to Sheets
🔐 Default Credentials (Example)
Plaintext

MinIO:
  - Username: admin
  - Password: changeme

NCA Toolkit:
  - API_KEY: changeme
⚠️ คำเตือน: ห้ามใช้ค่าเหล่านี้ในการ Production Environment เด็ดขาด! ควรแทนที่ด้วยรหัสผ่านและคีย์ที่มีความปลอดภัยสูงเสมอ.

📁 Storage & Volumes
./volume/ → ข้อมูล MinIO bucket (S3)
/data/nca-toolkit/logs → logs ของ Toolkit
/data/nca-toolkit/config → การตั้งค่าของ Toolkit
/data/nca-toolkit/temp → พื้นที่เก็บไฟล์ชั่วคราว
📦 Docker Network
บริการทั้งหมดจะใช้ Docker bridge network เฉพาะที่ชื่อ nca-network เพื่อการสื่อสารที่ปลอดภัย

🛡 Recommendations
✅ เพิ่ม docker-compose.yml ลงใน .gitignore เพื่อป้องกันการเผลอ commit ข้อมูลสำคัญ
✅ เก็บข้อมูลความลับ (secrets) ไว้ใน Environment Variables หรือ Secrets Manager
✅ สำรองข้อมูลใน /volume และ /data/nca-toolkit/ เป็นระยะๆ
📚 Resources
MinIO Docs
NCA Toolkit DockerHub
Cloudflare Tunnel Docs
