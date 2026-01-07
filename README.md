💬 Real-Time Chat Application
A full-stack, production-ready real-time chat application with user authentication, database persistence, and Socket.io for instant messaging.
✨ Features
Core Features

✅ User registration and authentication with JWT
✅ Real-time messaging with Socket.io
✅ Image sharing with automatic compression
✅ Message delivery and read receipts
✅ Typing indicators
✅ Online/offline user status
✅ Unread message counts
✅ Message history with pagination
✅ Search users and conversations
✅ Delete messages (for self or everyone)
✅ Responsive design (mobile, tablet, desktop)

Security

✅ Password hashing with bcrypt
✅ JWT-based authentication
✅ Input validation and sanitization
✅ Rate limiting on API endpoints
✅ XSS protection
✅ CORS configuration
✅ File upload validation

🛠 Tech Stack
Backend

Node.js - Runtime environment
Express.js - Web framework
PostgreSQL - Database
Sequelize - ORM
Socket.io - Real-time communication
JWT - Authentication
Bcrypt - Password hashing
Multer - File uploads
Sharp - Image processing

Frontend

React - UI library
React Router - Navigation
Axios - HTTP client
Socket.io-client - WebSocket client
Tailwind CSS - Styling
date-fns - Date formatting
browser-image-compression - Image compression

📋 Prerequisites
Before you begin, ensure you have the following installed:

Node.js (v16 or higher) - Download
PostgreSQL (v12 or higher) - Download
npm or yarn - Comes with Node.js
Git - Download

🚀 Installation & Setup
1. Clone the Repository
bashgit clone https://github.com/yourusername/chatapp.git
cd chatapp
2. Database Setup
Create PostgreSQL Database
bash# Login to PostgreSQL
psql -U postgres

# Create database
CREATE DATABASE chatapp;

# Exit psql
\q
Alternatively, you can use pgAdmin or any PostgreSQL GUI tool to create the database.
3. Backend Setup
bash# Navigate to server directory
cd server

# Install dependencies
npm install

# Create .env file
cp .env.example .env

# Edit .env file with your configuration
# Use your favorite text editor (nano, vim, or VS Code)
nano .env
Configure Environment Variables
Edit the .env file with your settings:
envPORT=5000
NODE_ENV=development

# Database Configuration
DB_HOST=localhost
DB_PORT=5432
DB_NAME=chatapp
DB_USER=postgres
DB_PASSWORD=your_postgres_password

# JWT Configuration
JWT_SECRET=your-super-secret-jwt-key-change-this
JWT_EXPIRES_IN=7d

# Client URL
CLIENT_URL=http://localhost:3000
Run Database Migrations
bash# Run migrations to create tables
npm run migrate
Start Backend Server
bash# Development mode with auto-reload
npm run dev

# Or production mode
npm start
The backend server should now be running on http://localhost:5000
4. Frontend Setup
Open a new terminal window:
bash# Navigate to client directory
cd client

# Install dependencies
npm install

# Create .env file
cp .env.example .env

# Edit .env file
nano .env
Configure Frontend Environment
Edit the .env file:
envREACT_APP_API_URL=http://localhost:5000/api
REACT_APP_SOCKET_URL=http://localhost:5000
Start Frontend Application
bash# Development mode
npm run dev

# Or build for production
npm run build
npm run preview
The frontend application should now be running on http://localhost:3000
📁 Project Structure
chatapp/
├── server/                  # Backend
│   ├── models/             # Database models
│   │   └── index.js        # User, Message, Conversation models
│   ├── routes/             # API routes
│   │   ├── auth.js         # Authentication routes
│   │   ├── users.js        # User management routes
│   │   ├── messages.js     # Message routes
│   │   └── conversations.js # Conversation routes
│   ├── middleware/         # Custom middleware
│   │   └── auth.js         # JWT authentication
│   ├── socket/             # Socket.io handlers
│   │   └── socketHandler.js
│   ├── uploads/            # Uploaded files
│   │   ├── images/         # Chat images
│   │   └── avatars/        # User avatars
│   ├── .env                # Environment variables
│   ├── .env.example        # Environment template
│   ├── server.js           # Main server file
│   └── package.json        # Dependencies
│
├── client/                 # Frontend
│   ├── src/
│   │   ├── components/     # React components
│   │   │   ├── Auth/       # Login & Register
│   │   │   └── Dashboard/  # Main app components
│   │   ├── App.jsx         # Main app component
│   │   ├── App.css         # Global styles
│   │   └── main.jsx        # Entry point
│   ├── public/             # Static files
│   ├── .env                # Environment variables
│   ├── .env.example        # Environment template
│   └── package.json        # Dependencies
│
└── README.md               # This file
🔧 API Endpoints
Authentication

POST /api/auth/register - Register new user
POST /api/auth/login - Login user
POST /api/auth/logout - Logout user
GET /api/auth/verify - Verify JWT token

Users

GET /api/users - Get all users (with search)
GET /api/users/:userId - Get user profile
PUT /api/users/profile - Update profile
POST /api/users/avatar - Upload avatar
PUT /api/users/change-password - Change password
POST /api/users/block/:userId - Block user
DELETE /api/users/block/:userId - Unblock user

Messages

POST /api/messages/send - Send text message
POST /api/messages/send-image - Send image
GET /api/messages/:userId - Get messages with user
PUT /api/messages/mark-read/:userId - Mark messages as read
DELETE /api/messages/:messageId - Delete message

Conversations

GET /api/conversations - Get all conversations
GET /api/conversations/unread-count - Get unread count
DELETE /api/conversations/:userId - Delete conversation

🔌 Socket.io Events
Client → Server

send-message - Send text message
send-image - Send image message
typing-start - User started typing
typing-stop - User stopped typing
message-read - Mark messages as read
delete-message - Delete message

Server → Client

receive-message - Receive text message
receive-image - Receive image
message-delivered - Message delivered
messages-read - Messages read by recipient
user-typing - User typing status
user-status-change - User online/offline
message-deleted - Message deleted

🧪 Testing
Test User Registration

Go to http://localhost:3000/register
Create an account with:

Username: testuser1
Email: test1@example.com
Password: Test1234



Test Real-Time Chat

Open two browser windows (or use incognito mode)
Register two different users
Login with both users
Start chatting between them
Test features:

Send text messages
Send images
See typing indicators
Check read receipts
Test online/offline status



🐛 Troubleshooting
Database Connection Issues
bash# Check if PostgreSQL is running
sudo service postgresql status

# Restart PostgreSQL
sudo service postgresql restart

# Verify database exists
psql -U postgres -l
Port Already in Use
bash# Find process using port 5000
lsof -i :5000

# Kill the process (replace PID with actual process ID)
kill -9 PID
Module Not Found Errors
bash# Clear npm cache and reinstall
rm -rf node_modules package-lock.json
npm install
Socket Connection Failed

Verify backend is running on port 5000
Check CORS configuration in server.js
Ensure frontend .env has correct SOCKET_URL

📦 Deployment
Backend Deployment (Heroku)
bash# Install Heroku CLI
# https://devcenter.heroku.com/articles/heroku-cli

# Login to Heroku
heroku login

# Create app
heroku create your-chatapp-backend

# Add PostgreSQL addon
heroku addons:create heroku-postgresql:hobby-dev

# Set environment variables
heroku config:set JWT_SECRET=your-secret-key
heroku config:set NODE_ENV=production

# Deploy
git subtree push --prefix server heroku main

# Run migrations
heroku run npm run migrate
Frontend Deployment (Vercel)
bash# Install Vercel CLI
npm i -g vercel

# Deploy
cd client
vercel

# Set environment variables in Vercel dashboard
# REACT_APP_API_URL=https://your-backend.herokuapp.com/api
# REACT_APP_SOCKET_URL=https://your-backend.herokuapp.com
🔐 Security Best Practices

Change Default Secrets: Update JWT_SECRET in production
Use HTTPS: Enable SSL certificates in production
Rate Limiting: Already configured for API endpoints
Input Validation: All inputs are validated
SQL Injection: Protected by Sequelize ORM
XSS Protection: React sanitizes output by default
File Upload: Size and type restrictions enforced

📄 License
MIT License - feel free to use this project for learning or commercial purposes.
👨‍💻 Author
Created with ❤️ by PRINCE RAUNIYAR
🤝 Contributing
Contributions, issues, and feature requests are welcome!
⭐ Show Your Support
Give a ⭐️ if this project helped you!

Happy Chatting! 🎉
