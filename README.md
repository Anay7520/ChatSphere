# ChatSphere

ChatSphere is a modern, real-time chat application built with a robust FastAPI backend and a responsive React frontend. It offers seamless messaging, user presence tracking, and a sleek user interface.

## 🚀 Features

- **Real-time Messaging**: Instant message delivery using Socket.IO.
- **User Authentication**: Secure sign-up and login with JWT-based authentication.
- **Presence System**: Real-time online/offline status updates.
- **Typing Indicators**: See when other users are typing.
- **Message History**: Persistent chat history stored in MongoDB.
- **Responsive Design**: customized CSS for a premium look and feel on desktop and mobile.
- **Rate Limiting**: API protection using SlowAPI.

## 🛠️ Tech Stack

### Backend
- **Framework**: [FastAPI](https://fastapi.tiangolo.com/) (Python)
- **Real-time**: [Socket.IO](https://python-socketio.readthedocs.io/)
- **Database**: [MongoDB](https://www.mongodb.com/) (via Motor async driver)
- **Caching/PubSub**: [Redis](https://redis.io/)
- **Authentication**: JWT (JSON Web Tokens) with `python-jose`
- **Rate Limiting**: SlowAPI

### Frontend
- **Framework**: [React](https://react.dev/)
- **Build Tool**: [Vite](https://vitejs.dev/)
- **Styling**: Custom CSS with CSS Variables
- **HTTP Client**: Axios
- **Socket Client**: socket.io-client

## 📋 Prerequisites

Before you begin, ensure you have the following installed:
- **Python** (v3.13+)
- **Node.js** (v18+) & npm
- **MongoDB** (Local or Atlas)
- **Redis** (Local or Cloud)

## 🏁 Getting Started

### 1. Clone the Repository
```bash
git clone <repository-url>
cd ChatSphere
```

### 2. Backend Setup

Navigate to the backend directory:
```bash
cd backend
```

Create and activate a virtual environment:
```bash
# Windows
python -m venv venv
venv\Scripts\activate

# macOS/Linux
python3 -m venv venv
source venv/bin/activate
```

Install dependencies:
```bash
pip install -e .
```

Configure Environment Variables:
Create a `.env` file in the `backend` directory (copy from `.env.example`):
```bash
cp .env.example .env
```
Update `.env` with your credentials:
```ini
ENVIRONMENT=development
DEBUG=true
API_VERSION=v1

# Database
MONGO_URI=mongodb://localhost:27017
MONGODB_NAME=chatsphere
REDIS_HOST=localhost
REDIS_PORT=6379

# Security
JWT_SECRET_KEY=your_super_secret_key_change_this
JWT_ALGORITHM=HS256
ACCESS_TOKEN_EXPIRE_MINUTES=30
```

Run the Backend Server:
```bash
python main.py
```
The API will be available at `http://localhost:8000` (Docs at `/docs`).

### 3. Frontend Setup

Navigate to the frontend directory:
```bash
cd ../frontend
```

Install dependencies:
```bash
npm install
```

Configure Environment Variables:
Create `src/api/config.js` or similar if needed, or ensure the frontend points to `http://localhost:8000`. 
*Note: Check `src/api` or `vite.config.js` for proxy settings if applicable.*

Run the Development Server:
```bash
npm run dev
```
The application will be accessible at `http://localhost:5173` (default Vite port).

## 📂 Project Structure

```
ChatSphere/
├── backend/
│   ├── app/
│   │   ├── models/       # Pydantic models & DB schemas
│   │   ├── routes/       # API endpoints (Auth, Users, Chats)
│   │   ├── services/     # Business logic & DB interactions
│   │   ├── utils/        # Helper functions
│   │   ├── config.py     # Configuration settings
│   │   ├── database.py   # DB connection logic
│   │   └── sio.py        # Socket.IO event handlers
│   ├── main.py           # Application entry point
│   ├── pyproject.toml    # Python dependencies
│   └── .env.example      # Environment variables template
│
└── frontend/
    ├── src/
    │   ├── components/   # Reusable UI components
    │   ├── context/      # React Context (Auth, Global State)
    │   ├── pages/        # Application pages (Login, Chat)
    │   ├── socket/       # Socket.IO client logic
    │   └── index.css     # Global styles
    ├── index.html        # Entry HTML
    └── vite.config.js    # Vite configuration
```

## 🤝 Contributing

Contributions are welcome! Please fork the repository and submit a pull request.

## 📄 License

This project is licensed under the MIT License.
