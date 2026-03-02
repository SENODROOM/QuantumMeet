# ⬡ QuantumMeet

> **Video calls at the speed of light.**  
> A full-stack, real-time video conferencing app built with MERN stack, WebRTC, and Socket.io.

![QuantumMeet Banner](https://placehold.co/900x300/050810/00d4ff?text=⬡+QuantumMeet&font=monospace)

---

## ✨ Features

| Feature | Description |
|---|---|
| 🔗 **Instant Rooms** | Create shareable meeting links with one click |
| 📹 **HD Video Calls** | Peer-to-peer WebRTC video with multiple participants |
| 🎙️ **Audio Controls** | Mute/unmute microphone on the fly |
| 📷 **Video Toggle** | Enable/disable camera mid-call |
| 🖥️ **Screen Sharing** | Share your full screen or a specific window |
| 💬 **In-Room Chat** | Real-time text messaging with Socket.io |
| 🔒 **P2P Encrypted** | Direct WebRTC connections (no video relayed through server) |
| 🗄️ **MongoDB Rooms** | Rooms auto-expire after 24 hours |
| ⚡ **No Signup** | Enter a name and go — no account required |

---

## 🏗️ Architecture

```
QuantumMeet/
├── server/                 # Node.js + Express + Socket.io backend
│   ├── index.js            # Main server (REST API + WebSocket signaling)
│   ├── .env.example        # Environment variable template
│   └── package.json
│
├── client/                 # React frontend
│   ├── public/
│   │   └── index.html
│   ├── src/
│   │   ├── App.js              # Router setup
│   │   ├── App.css             # Global styles + design tokens
│   │   ├── context/
│   │   │   └── SocketContext.js  # Socket.io React context
│   │   ├── hooks/
│   │   │   └── useWebRTC.js    # WebRTC peer connection logic
│   │   ├── pages/
│   │   │   ├── Home.js         # Landing / create / join
│   │   │   └── Room.js         # Main meeting room
│   │   └── components/
│   │       ├── VideoTile.js    # Individual video stream tile
│   │       ├── Controls.js     # Mute / Camera / Share / Chat / Leave
│   │       └── ChatPanel.js    # Slide-in chat drawer
│   └── package.json
│
├── package.json            # Root helper scripts
└── README.md
```

### How It Works

```
Client A                     Server                    Client B
   |                           |                           |
   |── POST /api/rooms ──────>|                           |
   |<─ { roomId, link } ──────|                           |
   |                           |                           |
   |── WS: join-room ────────>|<── WS: join-room ─────────|
   |<─ existing-peers ─────────|── user-joined ──────────>|
   |                           |                           |
   |── offer ────────────────>|── offer ─────────────────>|
   |<─ answer ─────────────────|<─ answer ─────────────────|
   |── ice-candidate ─────────>|── ice-candidate ─────────>|
   |                           |                           |
   |◄══════════════ P2P WebRTC (direct) ══════════════════►|
   |                           |                           |
   |── chat-message ──────────>|── chat-message ──────────>|
```

---

## 🚀 Quick Start

### Prerequisites

- **Node.js** ≥ 18.x — [download](https://nodejs.org)
- **MongoDB** — local install or [MongoDB Atlas](https://www.mongodb.com/atlas) (free tier)
- **npm** ≥ 9.x

### 1. Clone / Extract the Project

```bash
# If you downloaded the zip:
unzip QuantumMeet.zip
cd QuantumMeet
```

### 2. Set Up the Server

```bash
cd server

# Copy env file and configure it
cp .env.example .env
```

Edit `server/.env`:
```env
PORT=5000
MONGO_URI=mongodb://localhost:27017/quantummeet
CLIENT_URL=http://localhost:3000
```

> **Note:** The server works even without MongoDB — rooms are tracked in-memory only. MongoDB adds persistence and auto-expiry.

```bash
npm install
npm run dev     # starts with nodemon (auto-reload)
# or
npm start       # starts with node
```

You should see:
```
✅ MongoDB connected
🚀 Server running on http://localhost:5000
```

### 3. Set Up the Client

Open a **new terminal**:

```bash
cd client

# Copy env file
cp .env.example .env
# (default values work for local development)

npm install
npm start
```

React starts at **http://localhost:3000** and opens in your browser.

---

## 🧪 Quick Test

### Test A: Single Browser (Basic UI)

1. Open **http://localhost:3000**
2. Enter your name → click **New Meeting**
3. Copy the meeting link displayed
4. Click **Join Now** → you enter the room
5. You'll see your own camera feed with your name tag
6. The controls bar shows: Mute | Camera | Share Screen | Chat | Leave

### Test B: Two Participants (Full WebRTC)

1. Open **http://localhost:3000** in **Browser 1** (Chrome)
2. Enter name "Alice" → Create meeting → copy link → Join Now
3. Open the same link in **Browser 2** (or a different browser / incognito)
4. Enter name "Bob" → you're now in the same call
5. ✅ You should see both video streams
6. Test mute, camera off, chat, and screen share

### Test C: API Health Check

```bash
# Check server health
curl http://localhost:5000/api/health

# Create a room via API
curl -X POST http://localhost:5000/api/rooms \
  -H "Content-Type: application/json" \
  -d '{"userId":"test123"}'
```

Expected response:
```json
{
  "roomId": "abc-1234-xyz",
  "link": "http://localhost:3000/room/abc-1234-xyz"
}
```

---

## 🌐 WebSocket Events Reference

### Client → Server

| Event | Payload | Description |
|---|---|---|
| `join-room` | `{ roomId, userId, userName }` | Join a meeting room |
| `offer` | `{ to, from, offer, userName }` | WebRTC offer to peer |
| `answer` | `{ to, from, answer }` | WebRTC answer to offer |
| `ice-candidate` | `{ to, from, candidate }` | ICE candidate exchange |
| `chat-message` | `{ roomId, message, userName, userId }` | Send chat message |
| `toggle-audio` | `{ roomId, userId, enabled }` | Notify peers of audio state |
| `toggle-video` | `{ roomId, userId, enabled }` | Notify peers of video state |

### Server → Client

| Event | Payload | Description |
|---|---|---|
| `existing-peers` | `[{ socketId, userId, userName }]` | Peers already in room |
| `user-joined` | `{ socketId, userId, userName }` | New user joined |
| `user-left` | `{ socketId, userName }` | User disconnected |
| `offer` | `{ from, offer, userName }` | Incoming WebRTC offer |
| `answer` | `{ from, answer }` | Incoming WebRTC answer |
| `ice-candidate` | `{ from, candidate }` | Incoming ICE candidate |
| `chat-message` | `{ id, message, userName, userId, timestamp }` | Incoming chat message |
| `peer-audio-toggle` | `{ socketId, userId, enabled }` | Peer muted/unmuted |
| `peer-video-toggle` | `{ socketId, userId, enabled }` | Peer camera toggled |

---

## 🔧 REST API

| Method | Endpoint | Description |
|---|---|---|
| `POST` | `/api/rooms` | Create a new meeting room |
| `GET` | `/api/rooms/:roomId` | Get room details |
| `GET` | `/api/health` | Server health check |

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| **Frontend** | React 18, React Router v6, CSS Modules |
| **Backend** | Node.js, Express.js |
| **Real-time** | Socket.io (WebSocket signaling) |
| **Video** | WebRTC (browser-native P2P) |
| **Database** | MongoDB + Mongoose (optional) |
| **Styling** | CSS Modules, Google Fonts (Syne + Space Mono) |
| **ICE Servers** | Google STUN servers (free) |

---

## 🔒 Security Notes

- Video/audio streams are **peer-to-peer** — they never touch the server
- The server only handles **signaling** (offer/answer/ICE exchange)
- Rooms auto-expire in MongoDB after **24 hours**
- For production, add TURN servers for users behind strict NAT/firewalls

---

## 📦 Production Deployment

### Using Environment Variables

**Server** (`server/.env`):
```env
PORT=5000
MONGO_URI=mongodb+srv://user:pass@cluster.mongodb.net/quantummeet
CLIENT_URL=https://yourdomain.com
```

**Client** (`client/.env`):
```env
REACT_APP_SERVER_URL=https://your-server-domain.com
```

### Build the React App

```bash
cd client
npm run build
# Outputs to client/build/
```

Serve `client/build` with nginx, Vercel, Netlify, or any static host.
Deploy the `server/` to Railway, Render, or any Node.js host.

---

## 🐛 Troubleshooting

**Camera/mic not working?**
- Allow browser permissions when prompted
- Try HTTPS (some browsers block getUserMedia on HTTP in production)

**Participants can't see each other?**
- Check both clients point to the same server URL
- Check the server console for join/signal logs
- Try in the same local network first

**MongoDB connection fails?**
- The server still works without MongoDB (rooms are in-memory)
- Check `MONGO_URI` in `.env`
- For Atlas: ensure your IP is whitelisted

**Port already in use?**
- Change `PORT` in `server/.env`
- Kill existing processes: `lsof -ti:5000 | xargs kill`

---

## 📄 License

MIT — free to use, modify, and distribute.

---

<p align="center">Built with ⚡ using WebRTC + Socket.io + React + Node.js</p>
