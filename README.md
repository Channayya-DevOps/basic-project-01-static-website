🚀 DevOps Project 01 – Dockerized Static Website on AWS EC2
📌 Project Overview

This project demonstrates how to deploy a static website using Docker and Nginx on an AWS EC2 instance.
It is a beginner-friendly DevOps project covering Linux, Docker, AWS EC2, Security Groups, and basic networking.

The website is built using HTML, containerized using Docker, served via Nginx, and exposed to the internet through an AWS EC2 public IP.

🛠️ Technologies Used

AWS EC2 (Amazon Linux 2023)

Docker

Nginx

HTML

Linux (Amazon Linux)

AWS Security Groups

📂 Project Structure
DevOps-Projects/
└── Basic-Projects/
    └── project01/
        ├── Dockerfile
        ├── index.html
        └── README.md

📄 Application Details

Web Server: Nginx

Application Type: Static Website

Port Used: 8080

Container Port: 80

Host Port: 8080

🌐 Live Application Access
http://<EC2-PUBLIC-IP>:8080


Example:

http://3.8.82.27:8080

🧾 index.html (Static Web Page)
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
FROM nginx:latest
COPY index.html /usr/share/nginx/html/index.html


Explanation:

Uses official Nginx image

Copies index.html into Nginx default web directory

Nginx serves the file automatically on port 80

🔐 AWS Security Group Configuration

Ensure the following Inbound Rules are configured:

Type	Protocol	Port	Source
SSH	TCP	22	Your IP
Custom TCP	TCP	8080	0.0.0.0/0

⚠️ Important:
Without port 8080 open, the website will not be accessible from the browser.

🧑‍💻 Step-by-Step Deployment Guide
1️⃣ Connect to EC2 Instance
ssh -i your-key.pem ec2-user@<EC2-PUBLIC-IP>

2️⃣ Install Docker
sudo yum update -y
sudo yum install docker -y
sudo systemctl start docker
sudo systemctl enable docker
sudo usermod -aG docker ec2-user


➡️ Logout and login again to apply Docker group changes.

3️⃣ Verify Docker Installation
docker --version

4️⃣ Navigate to Project Directory
cd DevOps-Projects/Basic-Projects/project01

5️⃣ Build Docker Image
docker build -t project01-static-web .

6️⃣ Run Docker Container
docker run -d -p 8080:80 --name project01-container project01-static-web

7️⃣ Verify Container Status
docker ps


Expected output should show:

Container running

Port mapping 0.0.0.0:8080->80/tcp

8️⃣ Test Locally on EC2
curl http://localhost:8080

9️⃣ Access from Browser

Open your browser and visit:

http://<EC2-PUBLIC-IP>:8080

🧹 Docker Cleanup Commands (Optional)

Stop container:

docker stop project01-container


Remove container:

docker rm project01-container


Remove image:

docker rmi project01-static-web

❗ Common Issues & Fixes
❌ Website not opening in browser

✔ Check Security Group allows port 8080
✔ Ensure Docker container is running
✔ Verify correct EC2 public IP

❌ curl: Failed to connect to localhost:8080

✔ Container not running
✔ Port not mapped correctly
✔ Nginx not serving content

📈 Learning Outcomes

Docker image creation

Container port mapping

Nginx web server basics

AWS EC2 networking

Security Group configuration

Linux command line usage

👨‍💻 Author

Channayya Hiremath
DevOps Engineer (Learning & Practice Projects)
