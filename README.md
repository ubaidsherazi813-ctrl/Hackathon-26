<<<<<<< HEAD
# Baari (باری) · Smart Queue & Wait-Time Optimizer

> **Skip the line. Keep your turn.**
> Wait anywhere. Be there when it's your turn.

Baari is a real-time smart queue management system built for government civic centers, hospitals, and high-traffic public offices. It features real-time wait estimation, fair priority lanes, Smart Leave alerts, interactive What-If staffing simulations, a live TV Display Board with voice announcements, thermal walk-in receipts, and trilingual RTL support (English, Urdu, Sindhi).

---

## 🌟 Key Features

1. **Mobile Join & Live Token Page** (`/` & `/t/:publicId`):
   - One-tap token issuance with service wait estimates.
   - Perforated tactile ticket with live progress dots in the Queue Lane.
   - Smart Leave Alert: calculates travel time so visitors arrive just before their turn.
   - Grace period arrival confirmation ("I'm here").
2. **Staff Console** (`/staff`):
   - Three-pane operator control room with live elapsed counter timers.
   - Single-key shortcut (`N`) to call next visitor.
   - Priority claim verification/rejection.
   - 58 mm thermal walk-in receipt printing with QR code.
   - Demo Lab drawer with rush triggers (+5, +10, +20), auto-serve mode, and live What-If staffing panel.
3. **Admin Dashboard** (`/admin`):
   - 4 key metrics: Average wait, Average service duration, Completed tokens, In queue now.
   - Combined Chart.js hourly chart (arrival volume bars + average wait trendline).
   - Counter performance table with no-show rate and Quietest hours hint.
4. **TV Display Board** (`/display/:branchId`):
   - High-contrast 16:9 layout viewable from 5 metres.
   - Now serving counters and next 5 tokens in queue.
   - Sound chime and speech synthesis announcement on token call.
5. **Languages & Accessibility**:
   - Trilingual support: English, Urdu (اردو), and Sindhi (سنڌي).
   - Dynamic RTL flipping with token codes (e.g. `L-014`) strictly preserved Left-to-Right.
   - Large text toggle (`A+`, 20px base) and High contrast mode.
   - Screen-reader live regions (`aria-live="polite"` and `aria-live="assertive"`).

---

## 🛠️ Tech Stack

- **Backend**: Node.js (v20.x), Express 5
- **Real-Time**: Socket.IO 4 (WebSockets with polling fallback)
- **Database**: MongoDB (Mongoose 9)
- **Frontend**: Vanilla HTML5, CSS3 with Design Tokens (`tokens.css`, `app.css`), Vanilla JavaScript
- **Fonts**: Archivo (display figures), Figtree (UI body), Noto Nastaliq Urdu, Noto Naskh Arabic

---

## 🚀 Quick Start (Local Development)

### 1. Prerequisites
- Node.js 20.x or newer
- MongoDB (local instance or MongoDB Atlas connection URI)

### 2. Setup
```bash
# Clone the repository
git clone https://github.com/your-username/baari.git
cd baari

# Install dependencies
npm install

# Configure environment
cp .env.example .env
# Edit .env with your MongoDB URI and port settings
```

### 3. Seed Database
```bash
npm run seed
```
> **Note:** The seed script resets existing collections (`Branch`, `Service`, `Counter`, `Token`, `QueueEvent`, `User`, `Sequence`) and creates the demo civic center branch with 7 days of realistic history, services, staff accounts, and waiting tokens.

### 4. Run Server
```bash
# Production mode
npm start

# Development mode (with nodemon)
npm run dev
```
Open [http://localhost:3000](http://localhost:3000) in your browser.

---

## 🔑 Demo Credentials

- **Staff Console**: [http://localhost:3000/login](http://localhost:3000/login)
  - **Email**: `staff@baari.test`
  - **Password**: `demo1234`
- **Admin Dashboard**: [http://localhost:3000/admin](http://localhost:3000/admin)
- **TV Display Board**: [http://localhost:3000/display/demo](http://localhost:3000/display/demo)

---

## ☁️ Deployment Guide (Render Free Tier)

Deploying Baari on Render's free tier with MongoDB Atlas takes less than 5 minutes:

### Step 1: Prepare MongoDB Atlas (Free M0 Cluster)
1. Log in to [MongoDB Atlas](https://cloud.mongodb.com/).
2. Under **Network Access**, add an IP Access entry for `0.0.0.0/0` (Allow Access from Anywhere) so Render dynamic instances can connect.
3. Under **Database Access**, create a user (e.g. `baari_user`) and note the password.
4. Click **Connect** > **Drivers** > copy your connection string (e.g., `mongodb+srv://baari_user:<password>@cluster0.abcde.mongodb.net/baari?retryWrites=true&w=majority`).

### Step 2: Create Web Service on Render
1. Push this repository to your GitHub account.
2. In the [Render Dashboard](https://dashboard.render.com/), click **New +** > **Web Service**.
3. Connect your GitHub repository.
4. Configure the service settings:
   - **Name**: `baari` (or any unique name)
   - **Region**: Choose closest to your judges/users (e.g. Singapore, Oregon, or Frankfurt)
   - **Branch**: `main`
   - **Runtime**: `Node`
   - **Build Command**: `npm install`
   - **Start Command**: `node server.js`
   - **Instance Type**: `Free`

### Step 3: Configure Environment Variables in Render
In the **Environment** tab, add the following variables:
| Key | Value | Notes |
|---|---|---|
| `NODE_ENV` | `production` | Enables production optimizations |
| `MONGODB_URI` | `mongodb+srv://...` | Your Atlas connection string with credentials |
| `JWT_SECRET` | *(Random 32+ char string)* | Used for staff token encryption |
| `BASE_URL` | `https://your-service-name.onrender.com` | Your public Render URL (no trailing slash) |
| `DEMO_MODE` | `true` | Enables Demo Lab controls and reset options |

*(Note: Render automatically injects `PORT`. The app listens on `process.env.PORT` automatically).*

### Step 4: Seed Demo Data
Once the deployment finishes:
1. In Render, open the **Shell** tab of your web service.
2. Run:
   ```bash
   npm run seed
   ```
3. Alternatively, run `npm run seed` locally with the `MONGODB_URI` pointing to your Atlas cluster.

### Step 5: Demo Day Tips & Fallback Plan
- **Render Free Tier Spin-Down**: Free services sleep after 15 minutes of inactivity. Open your deployed URL **5 minutes before judging** to ensure the instance is awake and warm.
- **WebSocket Verification**: Confirm Socket.IO connects over HTTPS (`wss://...`). If corporate networks block WebSockets, the built-in HTTP long-polling fallback activates automatically.
- **Backup Plan**: If internet connectivity is unstable during a presentation, run locally on a laptop (`npm start`) and connect devices to the laptop via phone Wi-Fi hotspot or a Cloudflare Tunnel (`cloudflared tunnel --url http://localhost:3000`).

---

## 📄 License
ISC License.
=======
# Hackathon-26
Smart Queue Management System for public services with digital tokens, live queue tracking, and estimated waiting times.   Copy description
>>>>>>> origin/main
