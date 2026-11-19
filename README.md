# IronLink Care | Secure Client Portal

A secure, full-stack web application built to intercept, validate, and securely transmit Electronic Visit Verification (EVV) CSV files for IronLink Care. 

Designed with a strict security-first architecture, this portal ensures complete HIPAA compliance by utilizing memory-storage buffering. At no point is Protected Health Information (PHI) ever written to the server's physical disk.

## 🚀 Key Features
* **HIPAA-Compliant Pass-Through:** Utilizes `multer.memoryStorage()` to buffer EVV uploads directly in RAM before forwarding them to an external scrubber API via `axios`.
* **Asynchronous Processing & Secure Delivery:** Securely forwards the memory buffer alongside client metadata to an external Apps Script webhook. The frontend instantly detaches to provide a seamless UI experience, while the external scrubber processes the file and asynchronously emails the final results under a BAA-compliant Google Workspace architecture.
* **Enterprise-Grade Authentication:** Features `bcryptjs` password hashing and secure, `httpOnly` server-side session management to protect client accounts against XSS attacks.
* **White-Labeled UI:** Custom Handlebars (`.hbs`) templating matching the IronLink Care brand guidelines.

## 🛠️ Tech Stack
* **Frontend:** HTML5, CSS3, Express-Handlebars
* **Backend:** Node.js, Express.js
* **Database:** MongoDB Atlas, Mongoose
* **Core Middleware:** Multer (Memory Storage), Axios, Express-Session
* **Deployment:** Render (App Hosting), Squarespace (DNS Routing)

## 💻 Local Development Setup

**1. Clone the repository**
```bash
git clone https://github.com/RBroDev/ironlink-portal.git
cd ironlink-portal
```

**2. Install dependencies**
```bash
npm install
```

**3. Configure Environment Variables**
Create a `.env` file in the root directory and add the following keys:
```text
PORT=3000
MONGO_URI=your_mongodb_connection_string
SESSION_SECRET=your_secure_session_key
APPS_SCRIPT_URL=your_google_webhook_url
```

**4. Start the development server**
```bash
npm run dev
```
The application will be running at `http://localhost:3000`.

---
*Developed for IronLink Care.*
