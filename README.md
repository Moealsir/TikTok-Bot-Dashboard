# TikTok Bot Dashboard

## Overview

The TikTok Bot Dashboard is an advanced automation system that enables users to manage multiple TikTok accounts, automate interactions, and track performance seamlessly. It features a web-based dashboard to control bot operations, store session data, and customize settings for each account.

![TikTok Bot Dashboard](https://placeholder-for-dashboard-screenshot.png)

## Features

### Account Management
- Add, edit, and delete TikTok accounts via the dashboard
- Individual settings for each account (hashtags, comments, interaction preferences)
- Session storage (local and database) for seamless login
- Manual login via visible browser with session saving

### Hashtag & Comment Management
- Add, edit, and delete hashtags per account
- Add, edit, and delete comments per account
- Support for unique sets of hashtags and comments per account
- Import/export functionality for hashtags and comments

### Bot Execution
- Session-based login to TikTok
- Random hashtag selection from account's database
- Video search with configurable age filtering
- Full video watching before interaction
- Random interaction (like, comment, or both)
- Comment posting from account's predefined list
- Comprehensive action logging
- Configurable wait timing between interactions

### Parallel Execution
- Run bots for multiple accounts simultaneously
- Configure number of parallel executions
- Efficient resource allocation to prevent system overload
- Execution queue system for managing multiple accounts

### Error Handling & Recovery
- Account block/logout detection
- Comment failure logging
- Comprehensive error notification system
- Automatic retry functionality
- Detailed error reporting

### Analytics & Dashboard
- Comment success rate tracking
- Video engagement statistics
- Real-time bot activity monitoring
- Data visualization components
- Reporting and export functionality

## Technology Stack

### Frontend
- React.js with TypeScript
- Redux for state management
- Material-UI for components
- Chart.js for data visualization
- Socket.io for real-time updates

### Backend
- Node.js with Express
- MongoDB for database
- Puppeteer for TikTok automation
- JWT for authentication
- Socket.io for WebSocket communication
- Winston for logging

## Installation

### Prerequisites
- Node.js (v14 or higher)
- MongoDB (v4.4 or higher)
- npm or yarn

### Setup Instructions

1. Clone the repository
```bash
git clone https://github.com/yourusername/tiktok-bot-dashboard.git
cd tiktok-bot-dashboard
```

2. Install dependencies
```bash
# Install backend dependencies
cd server
npm install

# Install frontend dependencies
cd ../client
npm install
```

3. Configure environment variables
```bash
# In the server directory, create a .env file
cp .env.example .env

# Edit the .env file with your MongoDB connection string and other settings
```

4. Start the development servers
```bash
# Start backend server (from server directory)
npm run dev

# Start frontend server (from client directory)
npm start
```

5. Access the dashboard
```
Open your browser and navigate to http://localhost:3000
```

## Usage Guide

### Setting Up Accounts
1. Navigate to the "Accounts" section
2. Click "Add New Account"
3. Click "Open Browser" to log in to TikTok manually
4. After successful login, click "Save Session"
5. Configure account settings (hashtags, comments, interaction preferences)

### Managing Hashtags and Comments
1. Navigate to the "Hashtags & Comments" section
2. Select an account from the dropdown
3. Add, edit, or delete hashtags and comments for the selected account
4. Use the import/export functionality for bulk operations

### Running Bots
1. Navigate to the "Bot Control" section
2. Select accounts to run bots for
3. Configure execution settings (parallel instances, interaction frequency)
4. Click "Start Bots" to begin automation
5. Monitor bot activity in real-time on the dashboard

### Viewing Analytics
1. Navigate to the "Analytics" section
2. Select an account or view aggregated data
3. Explore engagement statistics, success rates, and performance metrics
4. Export reports as needed

## Project Structure

```
tiktok-bot-dashboard/
├── client/                 # Frontend React application
│   ├── public/             # Static files
│   ├── src/                # Source code
│   │   ├── components/     # UI components
│   │   ├── pages/          # Page components
│   │   ├── services/       # API services
│   │   ├── store/          # Redux store
│   │   └── utils/          # Utility functions
│   └── package.json        # Frontend dependencies
├── server/                 # Backend Node.js application
│   ├── src/                # Source code
│   │   ├── controllers/    # API controllers
│   │   ├── models/         # Database models
│   │   ├── routes/         # API routes
│   │   ├── services/       # Business logic
│   │   ├── utils/          # Utility functions
│   │   └── bot/            # Bot automation code
│   └── package.json        # Backend dependencies
├── docs/                   # Documentation
└── README.md               # Project overview
```

## Development Roadmap

See [timeline_and_priorities.md](./timeline_and_priorities.md) for the detailed development roadmap.

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Disclaimer

This tool is for educational purposes only. Use of this tool to violate TikTok's Terms of Service is not recommended. The developers are not responsible for any account bans or other consequences resulting from the use of this tool.

## Contact

Project Link: [https://github.com/yourusername/tiktok-bot-dashboard](https://github.com/yourusername/tiktok-bot-dashboard)
