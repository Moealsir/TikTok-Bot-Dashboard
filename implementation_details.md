# TikTok Bot Dashboard - Implementation Details

## Technology Stack

### Frontend
- Framework: React.js with TypeScript
- State Management: Redux or Context API
- UI Components: Material-UI or Tailwind CSS
- Charts/Visualization: Chart.js or D3.js
- WebSocket Client: Socket.io-client

### Backend
- Server: Node.js with Express
- Database: MongoDB (for flexibility with account data and settings)
- Authentication: JWT (JSON Web Tokens)
- Browser Automation: Puppeteer
- WebSocket Server: Socket.io
- Logging: Winston or Pino

### Development Tools
- Version Control: Git
- Package Manager: npm or yarn
- Testing: Jest, React Testing Library, Supertest
- CI/CD: GitHub Actions or Jenkins
- Code Quality: ESLint, Prettier

## Database Schema

### Account Collection
```
{
  _id: ObjectId,
  username: String,
  email: String,
  password: String (hashed),
  createdAt: Date,
  updatedAt: Date,
  settings: {
    watchFullVideo: Boolean,
    interactionSettings: {
      like: Boolean,
      comment: Boolean
    },
    maxVideoAge: Number (months)
  },
  sessions: [
    {
      cookies: Object,
      userAgent: String,
      createdAt: Date,
      lastUsed: Date
    }
  ]
}
```

### Hashtag Collection
```
{
  _id: ObjectId,
  accountId: ObjectId (reference to Account),
  tag: String,
  createdAt: Date,
  updatedAt: Date
}
```

### Comment Collection
```
{
  _id: ObjectId,
  accountId: ObjectId (reference to Account),
  text: String,
  createdAt: Date,
  updatedAt: Date
}
```

### Interaction Log Collection
```
{
  _id: ObjectId,
  accountId: ObjectId (reference to Account),
  videoId: String,
  hashtag: String,
  actions: {
    watched: Boolean,
    liked: Boolean,
    commented: Boolean
  },
  commentText: String,
  success: Boolean,
  errorMessage: String,
  timestamp: Date
}
```

## API Endpoints

### Account Management
- `POST /api/accounts` - Create new account
- `GET /api/accounts` - Get all accounts
- `GET /api/accounts/:id` - Get specific account
- `PUT /api/accounts/:id` - Update account
- `DELETE /api/accounts/:id` - Delete account
- `POST /api/accounts/:id/session` - Save session for account
- `GET /api/accounts/:id/session` - Get session for account

### Hashtag Management
- `POST /api/hashtags` - Create new hashtag
- `GET /api/hashtags?accountId=:accountId` - Get hashtags for account
- `PUT /api/hashtags/:id` - Update hashtag
- `DELETE /api/hashtags/:id` - Delete hashtag

### Comment Management
- `POST /api/comments` - Create new comment
- `GET /api/comments?accountId=:accountId` - Get comments for account
- `PUT /api/comments/:id` - Update comment
- `DELETE /api/comments/:id` - Delete comment

### Bot Management
- `POST /api/bots/start/:accountId` - Start bot for account
- `POST /api/bots/stop/:accountId` - Stop bot for account
- `GET /api/bots/status/:accountId` - Get bot status for account
- `POST /api/bots/startAll` - Start all bots
- `POST /api/bots/stopAll` - Stop all bots

### Analytics
- `GET /api/analytics/accounts/:accountId` - Get analytics for account
- `GET /api/analytics/summary` - Get summary analytics for all accounts

## Bot Execution Flow

1. **Initialization**
   - Load account settings and session data
   - Initialize Puppeteer browser
   - Set up error handlers

2. **Login Process**
   - Load TikTok website
   - Apply session cookies
   - Verify login status
   - Handle login failures

3. **Hashtag Selection**
   - Fetch hashtags from database
   - Randomly select hashtag
   - Navigate to hashtag search page

4. **Video Selection**
   - Scan videos on hashtag page
   - Filter by age (if applicable)
   - Select random video
   - Open video

5. **Video Interaction**
   - Watch video (full or partial based on settings)
   - Determine interaction type (like, comment, both)
   - Perform interactions
   - Log results

6. **Error Handling**
   - Detect login issues
   - Handle comment failures
   - Manage rate limiting
   - Implement retry mechanisms

7. **Cycle Completion**
   - Log completion
   - Wait configured time
   - Return to hashtag selection or select new hashtag
