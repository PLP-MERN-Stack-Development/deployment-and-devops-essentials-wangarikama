# Deployment Strategy

## 1. Backend Deployment (Render)
- **Platform:** Render Web Service
- **Repository:** mern-stack-integration-wangarikama
- **Environment Variables Configured:**
  - `MONGODB_URI`: Connection string to MongoDB Atlas
  - `JWT_SECRET`: Secret key for authentication
  - `NODE_ENV`: production
- **Build Command:** `npm install`
- **Start Command:** `node server.js`

## 2. Frontend Deployment (Vercel)
- **Platform:** Vercel
- **Framework:** Vite / React
- **Environment Variables:**
  - `VITE_API_URL`: https://my-mern-blog-api.onrender.com/api
- **Configuration:** Used `vercel.json` to handle SPA routing (rewrites to index.html).