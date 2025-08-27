# RedLead - AI-Powered Reddit Lead Generation Platform

![RedLead Logo](frontend/public/redlead.png)

> **Revolutionize your lead generation with RedLead's AI-driven platform, leveraging Reddit's vast community to find warm prospects and automate outreach.**

[![Live Demo](https://img.shields.io/badge/Live%20Demo-redlead.net-orange)](https://www.redlead.net)
[![License](https://img.shields.io/badge/License-ISC-blue.svg)](LICENSE)
[![Node.js](https://img.shields.io/badge/Node.js-18+-green.svg)](https://nodejs.org/)
[![Next.js](https://img.shields.io/badge/Next.js-15.3.5-black.svg)](https://nextjs.org/)

## 🚀 Overview

RedLead is a comprehensive AI-powered platform that transforms Reddit into your personal lead generation engine. By intelligently analyzing Reddit posts and comments, RedLead identifies potential customers discussing problems your product can solve, then helps you engage with them naturally and effectively.

### Key Features

- 🤖 **AI-Powered Lead Discovery**: Automatically finds relevant prospects across Reddit using advanced keyword matching and intent analysis
- 💬 **Smart Reply Generation**: Creates natural, helpful responses using OpenAI GPT-4, Google Gemini, and Perplexity AI
- 📊 **Campaign Management**: Organize leads by campaigns with custom targeting and filtering
- 🎯 **Intent Analysis**: Classifies leads by intent (pain points, solution seeking, brand comparison)
- 📈 **Performance Analytics**: Track engagement metrics, reply performance, and lead conversion
- 🔗 **Reddit Integration**: Seamless OAuth integration with Reddit for authentic engagement
- 🪝 **Webhook Support**: Real-time notifications for new leads and engagement events
- 📧 **Email Notifications**: Stay updated on new opportunities and campaign performance
- 🔍 **Market Insights**: Discover competitors and market trends from Reddit discussions

## 🏗️ Architecture

RedLead follows a modern full-stack architecture:

```
┌─────────────────┐    ┌──────────────────┐    ┌─────────────────┐
│   Next.js       │    │   Express.js     │    │   PostgreSQL    │
│   Frontend      │◄──►│   Backend API    │◄──►│   Database      │
│   (React 19)    │    │   (Node.js)      │    │   (Prisma ORM)  │
└─────────────────┘    └──────────────────┘    └─────────────────┘
         │                        │                        │
         ▼                        ▼                        ▼
┌─────────────────┐    ┌──────────────────┐    ┌─────────────────┐
│   Clerk Auth    │    │   AI Services    │    │   Reddit API    │
│   Authentication│    │   (GPT-4, Gemini)│    │   Integration   │
└─────────────────┘    └──────────────────┘    └─────────────────┘
```

### Tech Stack

**Frontend:**
- Next.js 15.3.5 with App Router
- React 19 with TypeScript
- Tailwind CSS with Radix UI components
- Framer Motion for animations
- Clerk for authentication

**Backend:**
- Node.js with Express.js
- TypeScript for type safety
- Prisma ORM with PostgreSQL
- Multiple AI providers (OpenAI, Google Gemini, Perplexity)
- Reddit API integration (snoowrap)

**Infrastructure:**
- Vercel for frontend deployment
- PostgreSQL database
- Cron jobs for automated lead discovery
- Webhook system for real-time notifications

## 🚀 Quick Start

### Prerequisites

- Node.js 18+ and npm
- PostgreSQL database
- Reddit API credentials
- AI API keys (OpenAI, Google Gemini, or Perplexity)
- Clerk authentication setup

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-username/redlead.git
   cd redlead
   ```

2. **Install backend dependencies**
   ```bash
   npm install
   ```

3. **Install frontend dependencies**
   ```bash
   cd frontend
   npm install
   cd ..
   ```

4. **Set up environment variables**

   Create `.env` in the root directory:
   ```env
   # Database
   DATABASE_URL="postgresql://username:password@localhost:5432/redlead"
   
   # Reddit API
   REDDIT_CLIENT_ID="your_reddit_client_id"
   REDDIT_CLIENT_SECRET="your_reddit_client_secret"
   REDDIT_USER_AGENT="RedLead/1.0"
   
   # AI Services (at least one required)
   OPENAI_API_KEY="your_openai_key"
   GEMINI_API_KEY="your_gemini_key"
   PERPLEXITY_API_KEY="your_perplexity_key"
   
   # Authentication
   CLERK_PUBLISHABLE_KEY="your_clerk_publishable_key"
   CLERK_SECRET_KEY="your_clerk_secret_key"
   CLERK_WEBHOOK_SECRET="your_clerk_webhook_secret"
   
   # Email (optional)
   RESEND_API_KEY="your_resend_key"
   
   # Application
   PORT=5000
   NODE_ENV=development
   ```

   Create `frontend/.env.local`:
   ```env
   NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY="your_clerk_publishable_key"
   CLERK_SECRET_KEY="your_clerk_secret_key"
   NEXT_PUBLIC_API_URL="http://localhost:5000"
   ```

5. **Set up the database**
   ```bash
   npx prisma migrate dev
   npx prisma generate
   ```

6. **Start the development servers**

   Backend (Terminal 1):
   ```bash
   npm run dev
   ```

   Frontend (Terminal 2):
   ```bash
   cd frontend
   npm run dev
   ```

7. **Access the application**
   - Frontend: http://localhost:3000
   - Backend API: http://localhost:5000

## 📖 Usage Guide

### 1. Account Setup

1. Visit the application and sign up with Clerk authentication
2. Complete the onboarding process:
   - Connect your Reddit account
   - Analyze your business URL
   - Set up your first campaign

### 2. Campaign Creation

1. **Analyze Your Business**: Provide your website URL for AI analysis
2. **Generate Keywords**: AI automatically generates relevant search keywords
3. **Target Subreddits**: Select subreddits where your audience is active
4. **Configure Filters**: Set negative keywords and subreddit blacklists

### 3. Lead Discovery

RedLead offers multiple discovery methods:

- **Automatic Discovery**: Scheduled jobs find leads based on your campaigns
- **Manual Discovery**: On-demand search for immediate results
- **Global Search**: Comprehensive Reddit-wide search with advanced filters

### 4. Lead Engagement

1. **Review Leads**: Browse discovered leads with AI-generated summaries
2. **Generate Replies**: Use AI to create natural, helpful responses
3. **Customize Responses**: Refine replies based on subreddit culture and rules
4. **Track Performance**: Monitor reply engagement and lead progression

### 5. Analytics & Insights

- **Performance Metrics**: Track lead discovery rates and engagement
- **Market Insights**: Discover competitors mentioned in discussions
- **Campaign Analytics**: Monitor individual campaign effectiveness
- **AI Usage Tracking**: Keep track of AI API usage by plan limits

## 🔧 Configuration

### AI Provider Setup

RedLead supports multiple AI providers with automatic fallback:

1. **OpenAI GPT-4**: Primary provider for reply generation
2. **Google Gemini**: Secondary provider with JSON mode support
3. **Perplexity AI**: Specialized for research and analysis

### Reddit API Configuration

1. Create a Reddit application at https://www.reddit.com/prefs/apps
2. Set the redirect URI to your domain + `/api/reddit/callback`
3. Use the client ID and secret in your environment variables

### Webhook Configuration

Set up webhooks for real-time notifications:

```javascript
// Example webhook payload for new leads
{
  "event": "lead.discovered",
  "data": {
    "leadId": "lead_123",
    "title": "Looking for a web developer",
    "subreddit": "forhire",
    "opportunityScore": 85
  }
}
```

## 🚀 Deployment

### Frontend (Vercel)

1. Connect your GitHub repository to Vercel
2. Set environment variables in Vercel dashboard
3. Deploy automatically on push to main branch

### Backend (Railway/Heroku)

1. **Railway Deployment**:
   ```bash
   railway login
   railway init
   railway add postgresql
   railway deploy
   ```

2. **Environment Variables**: Set all required environment variables in your hosting platform

3. **Database Migration**:
   ```bash
   railway run npx prisma migrate deploy
   ```

### Lead Generator Service

The Python lead generator can be deployed separately:

```bash
cd lead-generator
pip install -r requirements.txt
python main.py
```

## 🔒 Security & Privacy

- **Authentication**: Clerk handles secure user authentication
- **API Security**: All endpoints protected with user authorization
- **Data Privacy**: User data isolated by user ID in all database queries
- **Reddit Compliance**: Respects Reddit's API rate limits and terms of service
- **AI Safety**: Content filtering to ensure appropriate responses

## 📊 Database Schema

Key models in the Prisma schema:

- **User**: User accounts with subscription and Reddit connection status
- **Campaign**: Lead generation campaigns with targeting parameters
- **Lead**: Discovered Reddit posts with scoring and analysis
- **ScheduledReply**: Generated replies with posting status
- **MarketInsight**: Competitor mentions and market intelligence
- **Webhook**: User-configured webhook endpoints

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/amazing-feature`
3. Commit changes: `git commit -m 'Add amazing feature'`
4. Push to branch: `git push origin feature/amazing-feature`
5. Open a Pull Request

### Development Guidelines

- Use TypeScript for all new code
- Follow existing code style and conventions
- Add tests for new features
- Update documentation for API changes

## 📝 API Documentation

### Authentication

All API endpoints require Clerk authentication headers:

```javascript
headers: {
  'Authorization': 'Bearer <clerk_token>'
}
```

### Key Endpoints

- `GET /api/campaigns` - List user campaigns
- `POST /api/campaigns` - Create new campaign
- `GET /api/leads` - Get leads for campaign
- `POST /api/leads/generate-reply` - Generate AI reply
- `POST /api/webhooks` - Create webhook
- `GET /api/analytics/performance` - Get performance metrics

## 🐛 Troubleshooting

### Common Issues

1. **Reddit API Rate Limits**
   - Solution: Implement proper rate limiting and retry logic
   - Check Reddit API status

2. **AI API Quota Exceeded**
   - Solution: Configure multiple AI providers
   - Monitor usage in dashboard

3. **Database Connection Issues**
   - Solution: Check DATABASE_URL format
   - Ensure database is accessible

4. **Authentication Problems**
   - Solution: Verify Clerk configuration
   - Check environment variables

## 📈 Roadmap

- [ ] Advanced lead scoring with machine learning
- [ ] Multi-language support for international markets
- [ ] Integration with CRM platforms
- [ ] Advanced analytics and reporting
- [ ] Mobile application
- [ ] Bulk reply operations
- [ ] A/B testing for reply variations

## 📄 License

This project is licensed under the ISC License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- Reddit API for providing access to community data
- OpenAI, Google, and Perplexity for AI capabilities
- Clerk for authentication services
- Vercel for hosting and deployment
- The open-source community for various packages and tools

## 📞 Support

- **Website**: [redlead.net](https://www.redlead.net)
- **Documentation**: [docs.redlead.net](https://docs.redlead.net)
- **Issues**: [GitHub Issues](https://github.com/your-username/redlead/issues)
- **Email**: support@redlead.net

---

**Made with ❤️ for the Reddit community and growth-focused businesses**
