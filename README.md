# 🚀 DevOps Project 01 – Static Website Deployment using Docker & AWS EC2

## 📌 Project Overview
This project demonstrates how to deploy a **static website** using **Docker (Nginx)** on an **AWS EC2 instance**.  
The website is containerized using Docker and exposed to the internet via EC2 Security Groups.

---

## 🧰 Tech Stack Used
- **AWS EC2** (Amazon Linux 2023)
- **Docker**
- **Nginx**
- **HTML**
- **Git & GitHub**
- **Linux (Amazon Linux 2023)**

---

## 📂 Project Structure
```bash
DevOps-Projects/
└── Basic-Projects/
    └── project01/
        ├── Dockerfile
        ├── index.html
        └── README.md
🖥️ Application Details
The website is a static HTML page

Served using Nginx

Exposed on Port 8080

Accessible via Public IP of EC2 instance

📄 index.html
This file contains the static web content:

html
Copy code
<!DOCTYPE html>
<html>
<head>
    <title>DevOps Project 01</title>
</head>
<body>
    <h1>Welcome to DevOps</h1>
    <p>Project 01 by Channayya Hiremath</p>
</body>
</html>
🐳 Dockerfile
Dockerfile used to build the image:

dockerfile
Copy code
FROM nginx:latest
COPY index.html /usr/share/nginx/html/index.html
⚙️ Step-by-Step Implementation
1️⃣ Launch EC2 Instance
AMI: Amazon Linux 2023

Instance type: t2.micro (Free Tier)

Create or use an existing Key Pair

Configure Security Group:

Allow SSH (22) – for login

Allow Custom TCP (8080) – for web access

2️⃣ Install Docker on EC2
bash
Copy code
sudo yum update -y
sudo yum install docker -y
sudo systemctl start docker
sudo systemctl enable docker
sudo usermod -aG docker ec2-user
👉 Logout and login again to apply Docker group permissions.

3️⃣ Clone or Create Project Directory
bash
Copy code
mkdir DevOps-Projects
cd DevOps-Projects
mkdir -p Basic-Projects/project01
cd Basic-Projects/project01
4️⃣ Build Docker Image
bash
Copy code
docker build -t project01-static-web .
5️⃣ Run Docker Container
bash
Copy code
docker run -d -p 8080:80 --name project01-container project01-static-web
6️⃣ Verify Container Status
bash
Copy code
docker ps
7️⃣ Test Application Locally (EC2)
bash
Copy code
curl http://localhost:8080
8️⃣ Access from Browser
Open browser and visit:

text
Copy code
http://<EC2-PUBLIC-IP>:8080
✅ Example:

cpp
Copy code
http://3.8.82.27:8080
🔐 Security Group Configuration
Inbound Rules:

Type	Port	Source
SSH	22	Your IP
Custom TCP	8080	0.0.0.0/0

💰 Cost Information
EC2 t2.micro → Free Tier eligible

Security Groups → Free

Docker & Nginx → Free
⚠️ Charges may apply only if Free Tier limits are exceeded

🧪 Common Troubleshooting
❌ Site not opening?
Check:

bash
Copy code
docker ps
❌ Port not reachable?
Verify Security Group allows port 8080

Ensure container is running with -p 8080:80

🧹 Cleanup (Optional)
bash
Copy code
docker stop project01-container
docker rm project01-container
docker rmi project01-static-web
📚 Learning Outcomes
Learned Docker image creation

Understood container port mapping

Gained hands-on AWS EC2 experience

Deployed a real application on cloud

🧑‍💻 Author
Channayya Hiremath
DevOps Engineer – Learning & Practicing 🚀
