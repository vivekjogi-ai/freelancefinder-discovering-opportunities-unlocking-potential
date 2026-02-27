# Freelancing Platform

A full-stack web application that connects clients with freelancers, enabling project posting, bidding, and collaboration. Built with React, Node.js, Express, MongoDB, and Socket.io for real-time communication.

## 📋 Project Overview

This platform provides a complete freelancing marketplace with three main user roles:

- **Admin**: Manage users, projects, and applications
- **Client**: Post projects and manage freelancer applications
- **Freelancer**: Browse projects, submit bids, and complete work

## 🏗️ Architecture

The project is organized into two main directories:

```
code/
├── client/          # React Frontend
│   ├── src/
│   │   ├── components/     # Reusable components (Login, Register, Navbar)
│   │   ├── pages/          # Page components organized by user roles
│   │   ├── context/        # React Context for state management
│   │   ├── styles/         # CSS stylesheets
│   │   ├── images/         # Image assets
│   │   └── App.js          # Main app component with routing
│   └── public/            # Static files
│
└── server/          # Node.js Backend
    ├── index.js          # Express server & API endpoints
    ├── Schema.js         # MongoDB schemas
    ├── SocketHandler.js  # Socket.io event handlers
    └── package.json
```

## 🛠️ Tech Stack

### Frontend
- **React** 18.2.0 - UI library
- **React Router DOM** 6.19.0 - Client-side routing
- **Axios** 1.5.1 - HTTP client for API calls
- **Socket.io Client** 4.7.2 - Real-time communication
- **React Icons** 4.11.0 - Icon library
- **UUID** 9.0.1 - ID generation

### Backend
- **Express.js** 4.18.2 - Web framework
- **Mongoose** 7.6.1 - MongoDB ODM
- **Socket.io** 4.7.2 - Real-time bidirectional communication
- **Bcrypt** 5.1.1 - Password hashing
- **CORS** 2.8.5 - Cross-Origin Resource Sharing
- **Body Parser** 1.20.2 - Request body parsing

## 📁 Key Features

### User Management
- User registration and login (Admin, Client, Freelancer)
- Password encryption with bcrypt
- Role-based access control

### Project Management (Client)
- Create and post new projects
- View project applications from freelancers
- Monitor ongoing projects
- Track project completion and submissions

### Freelancer Features
- Browse all available projects
- Submit bids on projects
- Track applications and current projects
- View completed projects
- Manage skills and profile
- Real-time notifications

### Admin Dashboard
- View all users
- Monitor all projects
- Review applications
- System statistics

### Real-time Communication
- Socket.io integration for instant updates
- Live chat functionality
- Real-time notifications for bids and applications

## 📦 Database Models

### User
```
- username
- email
- password (hashed)
- usertype (admin/client/freelancer)
```

### Freelancer
```
- userId
- skills
- description
- currentProjects
- completedProjects
- applications
- funds
```

### Project
```
- clientId, clientName, clientEmail
- title, description
- budget, skills, deadline
- bids, bidAmounts
- status (Available/In Progress/Completed)
- freelancerId (assigned freelancer)
- submission details & links
```

### Application
```
- projectId
- clientId, clientName, clientEmail
- freelancerId, freelancerName
- bidAmount
- status
```

### Chat
```
- Participants
- Messages
- Timestamps
```

## 🚀 Getting Started

### Prerequisites
- Node.js (v14 or higher)
- npm or yarn
- MongoDB (running locally on port 27017)

### Installation

#### 1. Clone and navigate to project
```bash
cd code
```

#### 2. Setup Backend Server
```bash
cd server
npm install
# Server will run on http://localhost:6001
```

#### 3. Setup Frontend Client
```bash
cd ../client
npm install
# Client will run on http://localhost:3000
```

### Running the Application

#### Start MongoDB
Ensure MongoDB is running locally:
```bash
mongod
# or if using MongoDB Atlas, update the connection string in server/index.js
```

#### Start the Server (Terminal 1)
```bash
cd server
npm start
# or node index.js
```

The server will start on **http://localhost:6001**

#### Start the Client (Terminal 2)
```bash
cd client
npm start
```

The client will automatically open at **http://localhost:3000**

## 🔗 API Endpoints

### Authentication
- `POST /register` - Register a new user
- `POST /login` - User login

### Projects
- `GET /projects` - Get all projects
- `POST /projects` - Create new project (Client)
- `GET /projects/:id` - Get project details
- `PUT /projects/:id` - Update project

### Freelancers
- `GET /freelancers` - Get all freelancers
- `GET /freelancers/:id` - Get freelancer profile

### Applications/Bids
- `POST /applications` - Submit bid/application
- `GET /applications` - Get applications
- `PUT /applications/:id` - Update application status

### Admin
- `GET /admin/users` - Get all users
- `GET /admin/projects` - Get all projects
- `GET /admin/applications` - Get all applications

## 🔄 Real-time Features (Socket.io)

The application uses Socket.io for:
- **Live bidding notifications** - Clients notified when freelancers bid
- **Real-time chat** - Instant messaging between users
- **Status updates** - Project status changes reflected in real-time
- **Notification system** - Application updates and messages

## 📝 User Flows

### Freelancer Flow
1. Register as Freelancer
2. Complete profile with skills
3. Browse available projects
4. Submit bids on interesting projects
5. Receive notifications on bid acceptance
6. Start working on assigned projects
7. Submit completed work
8. Track earnings and completed projects

### Client Flow
1. Register as Client
2. Create and post new projects with budget
3. Specify required skills
4. Review incoming bids from freelancers
5. Select freelancer(s) for project
6. Communicate and monitor progress
7. Review and approve submissions
8. Complete project

### Admin Flow
1. Login as Admin
2. Access dashboard
3. View all users, projects, and applications
4. Monitor platform activity
5. Manage disputes or issues

## 🎨 Frontend Pages

- **Landing** - Home page
- **Authenticate** - Login/Register page
- **Freelancer Dashboard** - Overview of freelancer
- **All Projects** - Browse projects
- **My Projects** - Active/completed projects
- **My Applications** - Submitted bids
- **Project Details** - Detailed project view
- **Client Dashboard** - Client overview
- **New Project** - Create project form
- **Project Applications** - View received bids
- **Admin Dashboard** - System overview
- **Admin Projects** - All projects
- **All Applications** - All bids
- **All Users** - User management

## 🔐 Security Features

- Password encryption with bcrypt (salt rounds: 10)
- CORS enabled for controlled access
- Input validation
- User authentication for protected routes
- Role-based access control (RBAC)

## 📱 Responsive Design

The application is designed with responsive CSS and mobile-friendly interface.

## 🛠️ Development

### Adding New Features
1. Create components in `client/src/components/`
2. Create pages in `client/src/pages/`
3. Add styles in `client/src/styles/`
4. Add API endpoints in `server/index.js`
5. Update database schemas in `server/Schema.js` if needed
6. Add Socket.io handlers in `server/SocketHandler.js`

### Code Structure
- **Components**: Reusable UI components
- **Pages**: Full page components
- **Context**: Global state management
- **Styles**: Page and component specific CSS
- **API**: Backend endpoints for data operations

## 🐛 Troubleshooting

### MongoDB Connection Error
- Ensure MongoDB is running locally on port 27017
- Or update connection string in `server/index.js` to use MongoDB Atlas

### Port Already in Use
- Server runs on port 6001 - change PORT variable in `server/index.js` if needed
- Client runs on port 3000 - React will ask to use another port if unavailable

### Missing Dependencies
```bash
# In client or server directory
npm install
npm install --save package-name  # For new packages
```

### Socket.io Connection Issues
- Check if server is running on correct port
- Verify CORS settings match client URL

## 📚 Additional Resources

- [React Documentation](https://react.dev)
- [Express.js Guide](https://expressjs.com)
- [MongoDB Documentation](https://docs.mongodb.com)
- [Socket.io Guide](https://socket.io/docs)
- [Mongoose Documentation](https://mongoosejs.com)

## 📄 License

ISC License

## 👤 Authors

Built as a freelancing platform project.

## 🤝 Contributing

Feel free to fork, create feature branches, and submit pull requests for improvements.

---

**Last Updated**: February 27, 2026
