# 🚀 Project 01 – Static Website using Docker & AWS EC2

This project demonstrates how to deploy a **static HTML website** using **Docker (Nginx)** on an **AWS EC2 instance** and make it accessible over the internet.

---

## 📌 Project Overview

- Host a static HTML website
- Use **Nginx** as a web server
- Containerize the application using **Docker**
- Deploy on **AWS EC2 (Amazon Linux 2023)**
- Expose the website via **port 8080**

---

## 🧱 Tech Stack

| Technology | Purpose |
|----------|--------|
| HTML | Static website content |
| Docker | Containerization |
| Nginx | Web server |
| AWS EC2 | Cloud compute |
| Amazon Linux 2023 | OS |
| Git | Version control |

---

## 📂 Project Structure

```bash
DevOps-Projects/
└── Basic-Projects/
    └── project01/
        ├── Dockerfile
        ├── index.html
        └── README.md
📝 index.html
html
Copy code
<!DOCTYPE html>
<html>
<head>
    <title>DevOps Project</title>
</head>
<body>
    <h1>Welcome to DevOps</h1>
    <p>Project 01 by Channayya Hiremath</p>
</body>
</html>
🐳 Dockerfile
dockerfile
Copy code
FROM nginx:latest
COPY index.html /usr/share/nginx/html/index.html
📌 Explanation

Uses official Nginx image

Replaces default Nginx HTML page with our custom index.html

☁️ AWS EC2 Setup
1️⃣ Launch EC2 Instance
AMI: Amazon Linux 2023

Instance Type: t2.micro (Free Tier)

Key Pair: Create or use existing .pem key

Storage: Default

2️⃣ Security Group Configuration
Inbound Rules
Type	Port	Source
SSH	22	Your IP
Custom TCP	8080	0.0.0.0/0

⚠️ Port 8080 is required to access the Docker container.

🔑 Connect to EC2
bash
Copy code
ssh -i your-key.pem ec2-user@<EC2-PUBLIC-IP>
🛠️ Install Docker on EC2
bash
Copy code
sudo yum update -y
sudo yum install docker -y
sudo systemctl start docker
sudo systemctl enable docker
sudo usermod -aG docker ec2-user
exit
➡️ Reconnect after logout.

Verify:

bash
Copy code
docker --version
📦 Build Docker Image
Navigate to project directory:

bash
Copy code
cd DevOps-Projects/Basic-Projects/project01
Build image:

bash
Copy code
docker build -t project01-static-web .
Verify:

bash
Copy code
docker images
▶️ Run Docker Container
bash
Copy code
docker run -d -p 8080:80 --name project01-container project01-static-web
Check container status:

bash
Copy code
docker ps
🌐 Access the Application
Open browser:

cpp
Copy code
http://<EC2-PUBLIC-IP>:8080
✅ You should see:

vbnet
Copy code
Welcome to DevOps
Project 01 by Channayya Hiremath
🧪 Troubleshooting
❌ curl localhost:8080 not working?
Ensure container is running: docker ps

Ensure port mapping: 8080:80

Ensure Security Group allows port 8080

❌ Container name conflict?
bash
Copy code
docker rm -f project01-container
🧹 Stop & Remove Container
bash
Copy code
docker stop project01-container
docker rm project01-container

📤 Push to GitHub
git init
git add .
git commit -m "Project 01: Static website using Docker on EC2"
git branch -M main
git remote add origin https://github.com/<username>/<repo>.git
git push -u origin main

🎯 Learning Outcomes

Docker image creation

Nginx static hosting

AWS EC2 networking & security groups

Port mapping & container lifecycle

Real-world DevOps deployment workflow

👨‍💻 Author

Channayya Hiremath
DevOps Engineer | Docker | AWS | Linux
