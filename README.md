
---

# 💻 TechInterview - Collaborative Coding Platform

**TechInterview** is a full-stack real-time collaboration platform designed for technical interviews. It allows interviewers and candidates to write code together in a shared environment, communicate via high-quality video/audio, and chat in real-time.

## 🚀 Key Features

* **Real-time Collaboration:** Shared code editor powered by Monaco Editor.
* **Video & Audio Calls:** Integrated high-latency video conferencing using Stream.
* **Live Chat:** Real-time messaging alongside the coding interface.
* **Authentication:** Secure user authentication and management via Clerk.
* **Session Management:** Create, join, and track interview sessions.
* **Multi-language Support:** Built-in support for JavaScript, Python, C, C++, and Java.
* **Session History:** View past interview sessions and details.

## 🛠️ Tech Stack

### <img width="30" height="30" alt="image" src="https://github.com/user-attachments/assets/c27e6c7d-8a59-4edc-9816-f717d4ca4af3" /> **Frontend**

* **Framework:** React (Vite)
* **Styling:** Tailwind CSS
* **Editor:** Monaco Editor (`@monaco-editor/react`)
* **Video/Chat:** Stream Video & Chat SDKs
* **State/Data:** TanStack Query, Axios
* **Icons:** Lucide React

### <img  width="30" height="30" alt="image" src="https://github.com/user-attachments/assets/0a5bbb79-6be0-4dd7-a046-4679ef28e0aa" /> **Backend**

* **Runtime:** Node.js
* **Framework:** Express.js
* **Database:** MongoDB (Mongoose)
* **Authentication:** Clerk SDK (`@clerk/express`)
* **Background Jobs:** Inngest (for webhook handling and user sync)
* **Real-time Services:** Stream Chat & Video Node SDKs

---

## ⚙️ Prerequisites

Before running the project, ensure you have the following installed:

* [Node.js](https://nodejs.org/) (v18+)
* [MongoDB](https://www.mongodb.com/) (Local or Atlas)

You will also need accounts and API keys for:

* **Clerk** (Authentication)
* **Stream** (Video & Chat)
* **MongoDB Atlas** (Database)

---

## 🔐 Environment Variables

Create a `.env` file in both the `backend` and `frontend` directories.

### **Backend (`/backend/.env`)**

```env
PORT=3000
MONGODB_URI=your_mongodb_connection_string

# Clerk Authentication
CLERK_PUBLISHABLE_KEY=pk_test_...
CLERK_SECRET_KEY=sk_test_...
CLERK_WEBHOOK_SECRET=whsec_...

# Stream IO (Video/Chat)
STREAM_API_KEY=your_stream_api_key
STREAM_SECRET_KEY=your_stream_secret_key

# Inngest (Background Jobs)
INNGEST_SIGNING_KEY=your_inngest_signing_key
INNGEST_EVENT_KEY=your_inngest_event_key

```

### **Frontend (`/frontend/.env`)**

```env
VITE_CLERK_PUBLISHABLE_KEY=pk_test_...
VITE_API_URL=http://localhost:5000

```

---

## 📦 Installation & Setup

This project uses a split structure for Backend and Frontend. You will need to run two terminals.

### 1. Backend Setup

Navigate to the backend folder and install dependencies:

```bash
cd backend
npm install

```

Start the development server:

```bash
npm run dev
# Server runs on http://localhost:3000

```

### 2. Frontend Setup

Navigate to the frontend folder and install dependencies:

```bash
cd frontend
npm install

```

Start the Vite development server:

```bash
npm run dev
# Application runs on http://localhost:5173

```

---

## 🏃‍♂️ Running Background Jobs (Inngest)

To handle user synchronization (Clerk Webhooks) locally, you need the Inngest Dev Server.

1. Make sure the backend is running.
2. Run the Inngest UI:
```bash
npx inngest-cli@latest dev

```


3. Open the Inngest dashboard (usually `http://localhost:8288`) to monitor events.

---

## 📂 Project Structure

```text
/
├── backend/
│   ├── controllers/      # Logic for Auth, Sessions, Stream
│   ├── db/               # MongoDB connection setup
│   ├── inngest/          # Background functions (User sync)
│   ├── lib/              # Stream client configuration
│   ├── models/           # Mongoose Schemas (User, Session)
│   ├── routes/           # API Endpoints
│   └── server.js         # Entry point
│
├── frontend/
│   ├── src/
│   │   ├── components/   # UI Components (Editor, VideoCall, etc.)
│   │   ├── hooks/        # Custom hooks
│   │   ├── lib/          # Utils and Axios setup
│   │   └── pages/        # Dashboard, Session Room
│   └── index.html
└── README.md

```

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository.
2. Create a new branch (`git checkout -b feature/NewFeature`).
3. Commit your changes.
4. Push to the branch.
5. Open a Pull Request.

## 📄 License

This project is licensed under the MIT License.
