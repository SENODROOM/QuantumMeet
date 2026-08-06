# ⬡ QuantumMeet

> **Video calls at the speed of light.**  
> A full-stack, real-time video conferencing app built with MERN, WebRTC, Ably, and Vercel serverless.

![QuantumMeet Banner](https://placehold.co/900x300/050810/00d4ff?text=⬡+QuantumMeet&font=monospace)

---

## Features

| Feature | Description |
|---|---|
| **Instant Rooms** | Create shareable meeting links with one click |
| **HD Video Calls** | Peer-to-peer WebRTC video with multiple participants |
| **Fully Responsive** | Optimized UI that scales on mobile and tablets |
| **Picture-in-Picture (PiP)** | Native Document PiP to keep videos floating while changing tabs |
| **Live Transcription** | Real-time speech-to-text transcription panel during meetings |
| **Interactive Q&A / Polls** | Ask questions, upvote, and run real-time polls |
| **Collaborative Whiteboard** | Built-in synced whiteboard for drawing and explaining ideas |
| **Breakout Rooms** | Split the main meeting into smaller sub-rooms |
| **SecretMeet** | Anonymous random matching for instant 1-on-1 networking |
| **Audio / Video / Screen** | Mute, camera toggle, and screen sharing |
| **In-Room Chat** | Real-time text messaging via Ably + REST |
| **P2P Encrypted** | Direct WebRTC connections (no video relayed through server) |
| **MongoDB Rooms** | Rooms and meeting state auto-expire after 24 hours |
| **No Signup** | Enter a name and go — no account required for meetings |

---

## Architecture

```
QuantumMeet/
├── server/                 # Express API (Vercel serverless)
│   ├── index.js            # App entry (listen locally / export for Vercel)
│   ├── roomRealtime.js     # Meeting room REST + Ably fan-out
│   ├── realtimeToken.js    # Ably token minting
│   ├── lib/ably.js         # Ably REST client
│   ├── lib/db.js           # Cached Mongo connection
│   ├── vercel.json         # Serverless rewrites
│   └── .env.example
│
├── client/                 # React SPA (Vercel static)
│   ├── src/
│   │   ├── lib/realtimeClient.js  # Ably + REST (socket-shaped API)
│   │   ├── hooks/useWebRTC.js
│   │   ├── pages/Home.js, Room.js
│   │   └── components/
│   ├── vercel.json         # SPA fallback for React Router
│   └── package.json
│
├── package.json
└── README.md
```

### How It Works

```
Client A                     API (Vercel)              Ably                 Client B
   |                              |                      |                      |
   |── POST /api/rooms ──────────>|                      |                      |
   |<─ { roomId, link } ──────────|                      |                      |
   |                              |                      |                      |
   |── POST /api/realtime/token ─>|                      |                      |
   |── Ably connect + presence ───┼─────────────────────>|                      |
   |                              |                      |── presence / events ─>|
   |── offer (Ably channel) ──────┼─────────────────────>|── offer ─────────────>|
   |◄══════════════ P2P WebRTC (direct) ═══════════════════════════════════════►|
   |── POST /api/rooms/.../chat ─>|── persist Mongo ────>|── chat-message ──────>|
```

Ephemeral signaling (WebRTC offer/answer/ICE, whiteboard strokes) goes **client → Ably**. Durable actions (chat, polls, knocks, host controls) hit the **Express API**, which persists to Mongo and publishes on Ably via REST.

---

## Quick Start

### Prerequisites

- **Node.js** ≥ 18.x
- **MongoDB** — local install or [MongoDB Atlas](https://www.mongodb.com/atlas) (required for shared room state)
- **Ably** account + API key ([ably.com](https://ably.com))
- **npm** ≥ 9.x

### 1. Clone the Project

```bash
git clone https://github.com/your-username/QuantumMeet.git
cd QuantumMeet
```

### 2. Set Up the Server

```bash
cd server
cp .env.example .env
```

Edit `server/.env`:
```env
PORT=5000
MONGO_URI=mongodb://localhost:27017/quantummeet
CLIENT_URL=http://localhost:3000
JWT_SECRET=dev-secret-change-me
ABLY_API_KEY=your-ably-key
```

```bash
npm install
npm run dev     # nodemon
# or
npm start
```

### 3. Set Up the Client

Open a **new terminal**:

```bash
cd client
cp .env.example .env
npm install
npm start
```

React starts at **http://localhost:3000**.

---

## Quick Test (local smoke)

### Test A: Single Browser

1. Open **http://localhost:3000**
2. Enter your name → **New Meeting** → **Join Now**

### Test B: Two Participants

1. Browser 1: create a meeting as "Alice", copy the link, join
2. Browser 2 / incognito: open the same link as "Bob"
3. You should see both video streams; chat and mute signals should sync via Ably

### Test C: API health

```bash
curl http://localhost:5000/api/health
```

---

## Tech Stack

| Layer | Technology |
|---|---|
| **Frontend** | React 18, React Router v6, CSS Modules |
| **Backend** | Node.js, Express.js (Vercel serverless) |
| **Real-time** | Ably (pub/sub + presence) |
| **Video** | WebRTC (browser-native P2P) |
| **Database** | MongoDB + Mongoose |
| **Uploads** | Vercel Blob (classroom) |
| **ICE Servers** | Google STUN (add TURN for strict NAT) |

---

## Security Notes

- Video/audio streams are **peer-to-peer** — they never touch the server
- The API mints scoped Ably tokens and persists durable meeting state; signaling fan-out is Ably
- Rooms and meeting state auto-expire in MongoDB after **24 hours**
- Login rate limiting is in-memory per serverless instance (not shared across lambdas)
- For production, add TURN servers for users behind strict NAT/firewalls

---

## Production Deployment (Vercel)

Deploy as **two Vercel projects** (not one monorepo project).

### API project

- **Root directory:** `server/`
- Uses [`server/vercel.json`](server/vercel.json) rewrites to `index.js`
- Environment variables:

| Variable | Required | Purpose |
|---|---|---|
| `MONGO_URI` | Yes | Shared room/chat/host state across lambdas |
| `ABLY_API_KEY` | Yes | Token mint + REST publish |
| `JWT_SECRET` | Yes (classrooms) | Classroom auth |
| `BLOB_READ_WRITE_TOKEN` | Yes (classrooms) | File uploads (auto if Blob enabled) |
| `CLIENT_URL` | Yes | Primary frontend origin for CORS |
| `EXTRA_ALLOWED_ORIGINS` | No | Comma-separated extra CORS origins |

Preview frontends matching `quantum-meet-frontend*.vercel.app` are already allowed by CORS in `server/index.js`.

### Frontend project

- **Root directory:** `client/`
- Build: `npm run build` (or `vercel-build`)
- Uses [`client/vercel.json`](client/vercel.json) SPA rewrite for React Router
- Environment variables:

| Variable | Required | Purpose |
|---|---|---|
| `REACT_APP_SERVER_URL` | Yes | API base URL (no trailing slash) |
| `REACT_APP_ICE_SERVERS` | No | JSON array of STUN/TURN servers |

### Vercel preview smoke checklist

1. Deploy API → set env → `GET https://<api>/api/health` returns `{ status: "ok" }`
2. Deploy client with `REACT_APP_SERVER_URL` pointing at the API
3. Create a room, join from two browsers, confirm video + chat
4. Optional: knock/admit, SecretMeet match, classroom Blob upload

---

## Troubleshooting

**Camera/mic not working?**
- Allow browser permissions when prompted
- Use HTTPS in production (browsers block getUserMedia on insecure origins)

**Participants can't see each other?**
- Confirm both clients use the same `REACT_APP_SERVER_URL`
- Confirm `ABLY_API_KEY` is set on the API
- Try TURN via `REACT_APP_ICE_SERVERS` if STUN-only fails behind strict NAT

**MongoDB connection fails?**
- Meeting state (rooms, chat, host checks) needs Mongo across serverless instances — fix `MONGO_URI`
- For Atlas: allow Vercel egress / `0.0.0.0/0` or use Atlas network access for serverless

**CORS errors on preview?**
- Frontend previews under `quantum-meet-frontend*.vercel.app` are allowed by default
- Otherwise set `CLIENT_URL` or `EXTRA_ALLOWED_ORIGINS`

**Port already in use (local)?**
- Change `PORT` in `server/.env`

---

## License

MIT — free to use, modify, and distribute.

---

<p align="center">Built with WebRTC + Ably + React + Express on Vercel</p>
