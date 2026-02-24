# 🚚 GeoLogistics — Delivery Route Optimizer
### Full-Stack MERN Project · Architecture of Full-Stack Development

> **"My work is that I make using MERN Stack — Find shortest path across delivery logistics with clustering and mapping"**

---

## 📌 About The Project

GeoLogistics is a full-stack delivery route optimizer built using the MERN stack.
It uses **Dijkstra's Algorithm** on an adjacency matrix of GPS coordinates to compute
the shortest delivery path. Features an interactive 3D-style map, real-time location
sharing, call logs, notes, and a polished dark/light mode with wave animation.

---

## ⚙️ Tech Stack

| Layer      | Technology                          |
|------------|-------------------------------------|
| Frontend   | React 18, React Router v6           |
| Map        | React-Leaflet, Leaflet.js           |
| Styling    | Pure CSS (no framework)             |
| Backend    | Node.js, Express.js                 |
| Database   | MongoDB, Mongoose                   |
| Auth       | JWT (jsonwebtoken), bcryptjs        |
| HTTP       | Axios                               |
| Algorithm  | Dijkstra's Shortest Path (pure JS)  |
| Deploy     | Render (backend) + Netlify (frontend)|

---

## 📁 File Structure

```
geologistics-v2/
│
├── server/                         ← Node.js + Express API
│   ├── index.js                    ← Entry point, connects MongoDB
│   ├── middleware/
│   │   └── auth.js                 ← JWT auth middleware
│   ├── models/
│   │   ├── User.js                 ← User schema (name, email, password)
│   │   ├── Route.js                ← Saved delivery routes
│   │   ├── Call.js                 ← Call log entries
│   │   └── Note.js                 ← User notes
│   └── routes/
│       ├── auth.js                 ← /api/auth (login, register)
│       ├── routes.js               ← /api/routes (CRUD saved routes)
│       ├── calls.js                ← /api/calls (call logs)
│       └── notes.js                ← /api/notes (notes CRUD)
│
├── client/                         ← React Frontend
│   ├── public/
│   │   └── index.html
│   ├── src/
│   │   ├── index.js                ← React entry
│   │   ├── index.css               ← Global styles + dark/light + wave animation
│   │   ├── App.js                  ← Router + layout
│   │   ├── context/
│   │   │   ├── AuthContext.js      ← User auth state + axios
│   │   │   └── ThemeContext.js     ← Dark/light mode + wave toggle
│   │   ├── components/
│   │   │   ├── Navbar.js           ← Bottom nav (Dashboard/Calls/Home/Contact/Notes)
│   │   │   ├── TopBar.js           ← "Hi, User!" header + theme toggle
│   │   │   ├── MapView.js          ← Leaflet map with 3D dark tiles
│   │   │   ├── Footer.js           ← Copyright + real location + live time
│   │   │   └── WaveTransition.js   ← Bottom-to-top wave animation
│   │   ├── pages/
│   │   │   ├── AuthPage.js         ← Login / Register
│   │   │   ├── Dashboard.js        ← Time+emoji card, Map 3D, Start/Stop/Save
│   │   │   ├── CallsPage.js        ← Call logs + phone number + share location
│   │   │   ├── HomePage.js         ← Home/landing inside app
│   │   │   ├── ContactPage.js      ← Contacts list
│   │   │   ├── NotesPage.js        ← Add/view/delete notes
│   │   │   ├── ShareLocationPage.js← Share location → copy/paste WhatsApp
│   │   │   └── LogisticDetailPage.js← Route detail: info panel + history
│   │   └── utils/
│   │       └── optimizer.js        ← Dijkstra's algorithm + haversine distance
│   └── package.json
│
├── .env.example                    ← Environment variable template
└── README.md                       ← You are here
```

---

## ✨ Features

### ✅ Done
- [x] JWT Authentication (Register / Login)
- [x] Interactive Leaflet Map with dark 3D-style tiles
- [x] Dijkstra's Algorithm — shortest delivery path
- [x] Click map to add delivery stops
- [x] Start / Stop / Save route session
- [x] Dashboard with live time + emoji greeting
- [x] Dark / Light mode toggle with **bottom-to-top wave animation**
- [x] "Hi, [User]!" greeting on top bar
- [x] Save Call / Call log history with phone number
- [x] Last location + location history
- [x] Share location → copy link → paste to WhatsApp
- [x] Notes — add/view/delete personal notes
- [x] Logistic Detail page with information panel
- [x] Footer with copyright + real GPS location + live clock
- [x] Bottom navigation bar (Dashboard · Calls · Home · Contact · Notes)

### 🔜 Upcoming Features
- [ ] Real-time driver tracking (WebSocket / Socket.io)
- [ ] Push notifications for delivery updates
- [ ] Route export as PDF
- [ ] Multi-driver assignment per route
- [ ] Google Maps / Mapbox integration
- [ ] SMS alert on delivery completion
- [ ] Analytics dashboard (charts per week/month)
- [ ] Offline mode (PWA support)
- [ ] Dark map 3D terrain tiles upgrade
- [ ] Mobile app (React Native port)

---

## 📦 Install All Packages

### Backend
```bash
cd server
npm install express mongoose cors dotenv bcryptjs jsonwebtoken
npm install --save-dev nodemon
```

### Frontend
```bash
cd client
npm install react react-dom react-scripts
npm install react-router-dom
npm install axios
npm install leaflet react-leaflet
```

---

## 🚀 Run Commands

### 1. Clone & Setup Environment
```bash
git clone <your-repo-url>
cd geologistics-v2

# Copy and fill in your env
cp .env.example .env
```

### 2. Configure `.env` (inside `server/`)
```
MONGO_URI=mongodb+srv://<user>:<pass>@cluster.mongodb.net/geologistics
JWT_SECRET=your_secret_key
PORT=5000
CLIENT_URL=http://localhost:3000
```

### 3. Configure `client/.env`
```
REACT_APP_API_URL=http://localhost:5000
```

### 4. Install & Run Backend
```bash
cd server
npm install
npm run dev          # development (nodemon)
# OR
npm start            # production
```

### 5. Install & Run Frontend
```bash
cd client
npm install
npm start            # opens http://localhost:3000
```

### 6. Build Frontend for Production
```bash
cd client
npm run build        # creates build/ folder
```

---

## 🌐 Deploy

### Backend → Render.com (Free)
1. Push `server/` to GitHub
2. New Web Service on [render.com](https://render.com)
3. Build Command: `npm install`
4. Start Command: `node index.js`
5. Add environment variables: `MONGO_URI`, `JWT_SECRET`, `CLIENT_URL`

### Frontend → Netlify (Free)
1. `cd client && npm run build`
2. Drag `build/` folder to [netlify.com/drop](https://netlify.com/drop)
3. Environment variable: `REACT_APP_API_URL=https://your-app.onrender.com`

---

## 🧠 Algorithm

**Dijkstra's Shortest Path** runs entirely in the browser (no server needed):
1. Build N×N adjacency matrix using **Haversine formula** (real GPS distances)
2. Run Dijkstra from each node — all-pairs shortest distances
3. Greedy nearest-neighbor assembles the optimal visiting order

> *"Implemented Dijkstra's algorithm on a GPS coordinate adjacency matrix to compute optimized delivery sequences client-side in React."*

---

## 📜 Conclusion

GeoLogistics demonstrates a complete full-stack MERN architecture:
clean separation of concerns, JWT-secured REST API, MongoDB persistence,
client-side routing with React, and a non-trivial DSA algorithm
(Dijkstra's) implemented in production JavaScript.
It is designed as a portfolio-quality demo project — simple enough to
understand end-to-end, sophisticated enough to talk about in interviews.

---

## © Copyright

**GeoLogistics Delivery Optimizer**
© 2025 Thijs · All Rights Reserved

Built with ❤️ using the MERN Stack.
This project is for portfolio/educational purposes.
Do not redistribute without permission.

---
*Last updated: 2025 · Version 1.0.0*
