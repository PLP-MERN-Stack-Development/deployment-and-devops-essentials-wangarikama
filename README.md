# Deployment and DevOps Essentials - Week 7

This repository contains the configuration files, workflow templates, and documentation for the deployment of a full-stack MERN application. It demonstrates a complete DevOps lifecycle including deployment to cloud platforms, CI/CD automation, and server monitoring.

## 🚀 Live Application Links

| Application | Status | URL |
| :--- | :--- | :--- |
| **Frontend** (Vercel) | 🟢 Live | [https://blog-web-three-blue.vercel.app](https://blog-web-three-blue.vercel.app) |
| **Backend API** (Render) | 🟢 Live | [https://my-mern-blog-api.onrender.com](https://my-mern-blog-api.onrender.com) |

> *Note: The root endpoint of the API returns "MERN Blog API is running".*

---

## 🛠️ Deployment Strategy

The application follows a decoupled deployment architecture, separating the client and server into optimized hosting environments.

### 1. Backend Deployment (Render)
The Express/Node.js backend is deployed as a Web Service on Render.
- **Platform:** Render Web Service
- **Repository:** `mern-stack-integration-wangarikama`
- **Build Command:** `npm install`
- **Start Command:** `node server.js`
- **Environment Variables Configured:**
  - `MONGODB_URI`: Connection string to MongoDB Atlas Cluster.
  - `JWT_SECRET`: Secure key for user authentication.
  - `NODE_ENV`: Set to `production` for performance optimization.

### 2. Frontend Deployment (Vercel)
The React/Vite frontend is deployed on Vercel's Edge Network.
- **Platform:** Vercel
- **Framework:** Vite / React
- **Build Settings:**
  - Command: `npm run build`
  - Output Directory: `dist`
- **Environment Variables:**
  - `VITE_API_URL`: `https://my-mern-blog-api.onrender.com/api` (Points to the live backend).
- **Configuration:** Custom `vercel.json` was implemented to handle Single Page Application (SPA) routing, ensuring 404s fallback to `index.html`.

---

## ⚙️ CI/CD Pipeline

We implemented a Continuous Integration (CI) pipeline using **GitHub Actions** to automate testing and build verification.

- **Trigger:** Automatic execution on pushes to the `main` branch.
- **Workflow Scope:**
  - Checks out the latest code.
  - Installs backend dependencies within the `server/` directory.
  - Verifies that the application builds/starts without errors.

![CI/CD Pipeline Success](./cicd-pipeline.png)

*The reusable workflow templates can be found in the `.github/workflows/` directory.*

---

## 📊 Monitoring Setup

To ensure high availability and rapid incident response, server monitoring was implemented using **UptimeRobot**.

- **Tool:** UptimeRobot
- **Target Endpoint:** Backend Health Check / Root URL
- **Check Frequency:** Every 5 minutes
- **Alert Policy:** Instant email notifications if the service status changes to "Down".

*For detailed monitoring configuration and evidence, please refer to the `monitoring/` directory.*

---

## 📂 Repository Structure

- `deployment/` - Contains deployment configuration files (e.g., `vercel.json`) and strategy documentation.
- `monitoring/` - Evidence of UptimeRobot setup.
- `.github/workflows/` - CI/CD pipeline YAML templates.
- `.env.example` - Template for required environment variables.