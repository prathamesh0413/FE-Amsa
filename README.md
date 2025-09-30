# 🌟 AMSA Website  

![Project Banner](https://via.placeholder.com/1200x300?text=AMSA+Website+Project)  

**AMSA** is a full-stack web application designed to manage and showcase AMSA activities, events, and member engagement.  
It uses a modern React frontend, a Node.js backend, automated CI/CD pipeline, and secure AWS-based deployment.  

---

## 🚀 Features  

- ⚡ **Fast Frontend**: React + Vite for optimized builds and performance  
- 🔧 **Backend API**: Node.js + Express for business logic and APIs  
- 🛠️ **CI/CD Pipeline**: Automated builds and deployments via GitHub Actions  
- 🌍 **CloudFront CDN**: Global delivery of static frontend assets  
- 📊 **Monitoring & Alerts**: Server health and error tracking via AWS CloudWatch  
- ☁️ **AWS Hosting**: Frontend + Backend deployed on AWS EC2  
- 🔐 **Secure by Default**: HTTPS + SSL certificates  

---

## 🗂 Project Structure  

```
amsa-website/
├── CloudFormation/         # AWS infrastructure templates
├── frontend/               # React + Vite frontend
├── backend/                # Node.js + Express backend
├── .github/workflows/      # CI/CD pipeline
└── README.md               # Documentation
```

---

## 🛠️ Tech Stack  

| Component   | Technology                     |
|-------------|--------------------------------|
| Frontend    | React, Vite                    |
| Backend     | Node.js, Express               |
| Hosting     | AWS EC2                        |
| CDN         | AWS CloudFront                 |
| CI/CD       | GitHub Actions                 |
| Monitoring  | AWS CloudWatch / Dashboards    |
| Security    | HTTPS / SSL Certificates       |

---

## 🏗️ Architecture Overview  

- **GitHub Actions** → Builds, tests, and deploys frontend + backend  
- **EC2 Instances** → Hosts frontend and backend servers  
- **CloudFront CDN** → Caches frontend for global performance  
- **Monitoring** → Tracks uptime, CPU, memory, network, and errors  

---

## 📦 Deployment Process  

### 1️⃣ CloudFormation (IaC)  
- Spins up EC2 instances for frontend & backend  
- Configures networking, ports, and security groups  
- Sets up CloudFront distribution  

### 2️⃣ CI/CD (GitHub Actions)  
- Triggered on `push` to `main`  
- **Frontend:** Install → Test → Build → Deploy to EC2  
- **Backend:** Install → Test → Deploy with `pm2`  

### 3️⃣ Monitoring & Alerts  
- CloudWatch dashboards for performance  
- Alerts via Email / Slack  

### 4️⃣ Manual Deployment (first time setup)  

**Frontend**
```bash
cd frontend
npm install
npm run build

# Copy build to EC2
scp -r dist/ ubuntu@<FRONTEND_EC2_IP>:/var/www/html
```

**Backend**
```bash
cd backend
npm install

# Copy backend to EC2
scp -r ./ ubuntu@<BACKEND_EC2_IP>:/home/ubuntu/backend

# SSH into EC2 and start
ssh ubuntu@<BACKEND_EC2_IP>
cd backend
pm2 start index.js --name backend
```

**CloudFront + SSL**
- Configure CloudFront to serve `/dist`  
- Attach SSL certificate for HTTPS  

---

## 🌐 Demo URLs  

- Frontend (HTTPS): `https://<FRONTEND_EC2_IP>`  
- Backend API (HTTPS): `https://<BACKEND_EC2_IP>`  
*(Replace with EC2 IPs or CloudFront URLs)*  

---

## 💻 Quick Setup Guide  

```bash
# Clone repo
git clone https://github.com/<your-username>/amsa-website.git
cd amsa-website

# Frontend
cd frontend
npm install
npm run dev      # Development
npm run build    # Production

# Backend
cd ../backend
npm install
npm start        # Development
pm2 start index.js --name backend  # Production
```

---

## 🏷️ Badges  

![React](https://img.shields.io/badge/Frontend-React-blue)  
![Vite](https://img.shields.io/badge/Build-Vite-yellow)  
![Node.js](https://img.shields.io/badge/Backend-Node.js-green)  
![AWS](https://img.shields.io/badge/Cloud-AWS-orange)  
![GitHub Actions](https://img.shields.io/badge/CI/CD-GitHub_Actions-black)  

---

## 📄 License  

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file.  
