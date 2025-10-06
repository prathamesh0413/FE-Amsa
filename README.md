# 🌟 AMSA Website  

![Project Banner](https://media.gettyimages.com/id/1363235639/vector/vector-set-of-illustration-project-management-concept-line-art-style-background-design-for.jpg?s=612x612&w=gi&k=20&c=cLm0WqjWbDPB4ICiJT8eIZ-ydEHjUpIzY6iZEBLF46g=)  

**AMSA** is a full-stack web application designed to manage and showcase AMSA activities, events, and member engagement.  
It uses a modern React frontend, a Node.js backend, automated CI/CD pipeline, and secure AWS-based deployment.  

---

## 🚀 Features  

- ⚡ **Fast Frontend**: React & Typescript for optimized builds and performance  
- 🔧 **Backend API**: Node.js + Express for business logic and APIs  
- 🛠️ **CI/CD Pipeline**: Automated builds and deployments via GitHub Actions   
- 📊 **Monitoring & Alerts**: Server health and error tracking via AWS CloudWatch and Sns
- ☁️ **AWS Hosting**: Frontend + Backend deployed on AWS EC2  
- 🔐 **Secure by Default**: HTTPS + SSL certificates  

---

## 🗂 Project Structure  

```
amsa-website/
├── CloudFormation/        # AWS infrastructure templates
├── frontend/               # React + Typescript frontend
├── backend/                # Node.js + Express backend
├── .github/workflows/      # CI/CD pipeline
└── README.md               # Documentation
```

---

## 🛠️ Tech Stack  

| Component   | Technology                     |
|-------------|--------------------------------|
| Frontend    | React,Typescript               |
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
- Sets up Monitoring through Cloudwatch & SNS.  

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
npm run export(for out folder)

# Copy build to EC2
# Prepare frontend directory
          mkdir -p /var/www/amsa-fe
```

**Backend**
```bash
name: Build Backend
      working-directory: backend
      run: npm install
# Copy backend to EC2
scp -r ./ ubuntu@<BACKEND_EC2_IP>:/home/ubuntu/backend

# SSH into EC2 and start
cd /home/ubuntu/BE-Amsa
          git pull origin main
          npm install
          pm2 restart amsa-backend || pm2 start server.js --name amsa-backend --watch
          pm2 save
```

**CloudFront + SSL**
- Configure CloudFront to serve `/dist`  
- Attach SSL certificate for HTTPS  

---

## 🌐 Demo URLs  

- Frontend (HTTPS): `https://<FRONTEND_EC2_IP>`  
- Backend API (HTTPS): `https://<FRONTEND_EC2_IP>/api/contact`  
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
npm run export   #For out folder

# Backend
cd ../backend
npm install
npm start        # Development
pm2 start server.js --name backend  # Production
```

---
| Repository                         | Description                                                                                                                                                           | Link                                                                    |
| ---------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------- |
| 🖥️ **Frontend (Amsa-website-FE)** | React + TypeScript-based single-page application with modern UI for AMSA’s website. It handles user interaction, event display, and API integration with the backend. | [🔗 View Repository](https://github.com/prathamesh0413/FE-Amsa) |
| ⚙️ **Backend (Amsa-website-BE)**   | Node.js + Express REST API providing backend logic, email services (contact form), and database integration. Deployed with PM2 on AWS EC2.                            | [🔗 View Repository](https://github.com/prathamesh0413/BE-Amsa) |


## 🏷️ Badges  

![React](https://img.shields.io/badge/Frontend-React-blue)  
![Vite](https://img.shields.io/badge/Build-Vite-yellow)  
![Node.js](https://img.shields.io/badge/Backend-Node.js-green)  
![AWS](https://img.shields.io/badge/Cloud-AWS-orange)  
![GitHub Actions](https://img.shields.io/badge/CI/CD-GitHub_Actions-black)  

---

## 📄 License  

This project is licensed under the **MIT License**  
