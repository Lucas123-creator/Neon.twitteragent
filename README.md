# TwitterAgent v2.0.0 - Enhanced Autonomous System

> **The most advanced autonomous Twitter management system with A/B testing, influencer detection, and contingency control.**

[![Version](https://img.shields.io/badge/version-2.0.0-blue.svg)](https://github.com/neonhub/twitter-agent-v2)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![Node.js](https://img.shields.io/badge/node-%3E%3D18.0.0-brightgreen.svg)](https://nodejs.org/)

## 🚀 Features

### Core Capabilities
- **🤖 Autonomous Twitter Management** - AI-powered tweet generation and posting
- **🧪 A/B Testing System** - Multi-variant testing with engagement scoring
- **👑 Influencer Detection** - Real-time identification of high-priority mentions
- **🛡️ Contingency Control** - Emergency pause/resume and safety systems
- **📡 Real-time Stream Listening** - Live mention tracking and response
- **🔐 OAuth 2.0 Authentication** - Secure token management and refresh
- **🛡️ Brand Safety** - Content moderation and filtering
- **🎨 Media Generation** - AI-powered visual content creation
- **📊 Metrics Sync** - Performance tracking and vector learning
- **🎭 Persona Management** - Brand voice and context awareness

### Advanced Systems
- **Vector Learning** - Embedding-based content optimization
- **Scheduling Engine** - Intelligent tweet timing and automation
- **Context Awareness** - Campaign-specific persona management
- **Performance Analytics** - Engagement scoring and insights
- **Safety Auditing** - Comprehensive content safety checks

## 📦 Installation

```bash
npm install @neon/twitter-agent-v2
```

### Prerequisites
- Node.js >= 18.0.0
- Twitter API v2 credentials
- OpenAI API key (for AI features)

## 🔧 Quick Start

### 1. Basic Usage

```typescript
import { TwitterAgent } from '@neon/twitter-agent-v2';

// Initialize agent
const agent = new TwitterAgent('my-agent', 'My Twitter Agent');

// Generate and post tweet
const tweet = await agent.generateTweet('campaign-123');
const response = await agent.postTweet(tweet);

console.log(`Posted tweet: ${response.tweetId}`);
```

### 2. A/B Testing

```typescript
import { runABTest } from '@neon/twitter-agent-v2';

const variants = [
  { text: 'Check out our new product!', hashtags: ['#innovation'] },
  { text: 'Discover what\'s new today', hashtags: ['#discovery'] },
  { text: 'Exciting news ahead!', hashtags: ['#excitement'] }
];

// Run A/B test with 2-hour evaluation period
const winner = await runABTest(variants, 'campaign-123', {
  evaluationHours: 2,
  spacingMinutes: 30
});

console.log(`Winner: ${winner.text}`);
```

### 3. Influencer Detection

```typescript
import { 
  startTwitterStreamListener, 
  getInfluencerMentions 
} from '@neon/twitter-agent-v2';

// Start listening for mentions
await startTwitterStreamListener();

// Get high-priority mentions (10K+ followers or verified)
const influencers = await getInfluencerMentions();
console.log(`Found ${influencers.length} influencer mentions`);
```

### 4. Contingency Control

```typescript
import { 
  pauseAgent, 
  resumeAgent, 
  isAgentPaused 
} from '@neon/twitter-agent-v2';

// Pause agent for maintenance
await pauseAgent('TwitterAgent', 'Scheduled maintenance');

// Check status
const paused = await isAgentPaused('TwitterAgent');
console.log(`Agent paused: ${paused}`);

// Resume when ready
await resumeAgent('TwitterAgent');
```

## 🏗️ Architecture

```
twitter-agent-v2/
├── src/
│   ├── agents/           # Core agent implementations
│   │   ├── TwitterAgent.ts      # Main Twitter agent
│   │   ├── twitterABTest.ts     # A/B testing system
│   │   └── contextManager.ts    # Persona & context management
│   ├── utils/            # Utility systems
│   │   ├── agentControl.ts      # Contingency control
│   │   ├── filters.ts           # Brand safety & moderation
│   │   └── mediaGenerator.ts    # Visual content generation
│   ├── core/             # Core systems
│   │   ├── metricsSync.ts       # Performance tracking
│   │   └── scheduler.ts         # Task scheduling
│   ├── listeners/        # Real-time systems
│   │   └── streamListener.ts    # Twitter stream listening
│   ├── auth/             # Authentication
│   │   └── twitterOAuth.ts      # OAuth 2.0 implementation
│   ├── base-agent.ts     # Base agent framework
│   ├── types.ts          # TypeScript interfaces
│   ├── logger.ts         # Logging system
│   └── index.ts          # Main exports
```

## 🔌 Configuration

### Environment Variables

```bash
# Twitter API v2
TWITTER_BEARER_TOKEN=your_bearer_token
TWITTER_API_KEY=your_api_key
TWITTER_API_SECRET=your_api_secret
TWITTER_ACCESS_TOKEN=your_access_token
TWITTER_ACCESS_TOKEN_SECRET=your_access_token_secret

# OpenAI (for AI features)
OPENAI_API_KEY=your_openai_key

# Brand configuration
TWITTER_BRAND_HANDLE=@YourBrand
```

### Agent Configuration

```typescript
import { TwitterAgent } from '@neon/twitter-agent-v2';

const config = {
  maxTweetLength: 280,
  enableAutoResponses: true,
  enableTrendScanning: true,
  enableContentOptimization: true,
  rateLimitDelay: 1000
};

const agent = new TwitterAgent('my-agent', 'My Agent', config);
```

## 📊 A/B Testing Configuration

```typescript
import { runABTest } from '@neon/twitter-agent-v2';

const config = {
  maxVariants: 3,           // Maximum variants to test
  spacingMinutes: 30,       // Time between posts
  evaluationHours: 2,       // Evaluation period
  engagementThreshold: 0.02 // 2% engagement rate threshold
};

const winner = await runABTest(variants, 'campaign-123', config);
```

## 🛡️ Safety & Control

### Contingency Control

```typescript
import { 
  agentControl, 
  emergencyStopAll 
} from '@neon/twitter-agent-v2';

// Emergency stop all agents
await emergencyStopAll('System maintenance');

// Get agent status
const status = await agentControl.getAgentStatusSummary();
console.log(status);
// { TwitterAgent: false, ContentAgent: false, ... }
```

### Brand Safety

```typescript
import { brandSafetyFilter } from '@neon/twitter-agent-v2';

const result = await brandSafetyFilter.checkBrandSafety(
  'Your tweet content here',
  'campaign-123'
);

if (!result.isSafe) {
  console.log(`Blocked: ${result.auditLog.reason}`);
}
```

## 📈 Performance & Analytics

### Metrics Tracking

```typescript
import { metricsSync } from '@neon/twitter-agent-v2';

// Get performance data
const performance = await metricsSync.fetchTweetPerformance('campaign-123', 30);

// Get optimization insights
const insights = await metricsSync.getOptimizationInsights('campaign-123', 'tweet text');
```

### Vector Learning

```typescript
import { metricsSync } from '@neon/twitter-agent-v2';

// Vectorize tweet performance for similarity search
const vectorized = await metricsSync.vectorizeTweetPerformance(performanceRecord);
```

## 🎨 Media Generation

```typescript
import { mediaGenerator } from '@neon/twitter-agent-v2';

const request = {
  type: 'meme',
  content: 'Your meme text',
  style: 'modern',
  template: 'success'
};

const media = await mediaGenerator.generateMedia(request);
console.log(`Generated: ${media.url}`);
```

## 🔄 Real-time Stream Listening

```typescript
import { 
  startTwitterStreamListener,
  streamEvents 
} from '@neon/twitter-agent-v2';

// Start listener
await startTwitterStreamListener();

// Listen for events
streamEvents.on('mention', (mention) => {
  console.log(`New mention from ${mention.userHandle}`);
});

streamEvents.on('influencer', (influencer) => {
  console.log(`Influencer mention: ${influencer.followerCount} followers`);
});
```

## 🔐 OAuth Authentication

```typescript
import { 
  twitterOAuth, 
  getAuthenticatedClient 
} from '@neon/twitter-agent-v2';

// Initialize OAuth
const oauth = new twitterOAuth({
  clientId: 'your_client_id',
  clientSecret: 'your_client_secret',
  redirectUri: 'your_redirect_uri'
});

// Get authenticated client
const client = await getAuthenticatedClient('user_id');
```

## 🧪 Testing

```bash
# Run tests
npm test

# Run with coverage
npm run test:coverage

# Run specific test
npm test -- --testNamePattern="A/B Testing"
```

## 📝 API Reference

### Core Classes

- **TwitterAgent** - Main Twitter automation agent
- **TwitterABTest** - A/B testing system
- **AgentControl** - Contingency control system
- **MetricsSync** - Performance tracking and analytics
- **TwitterOAuth** - OAuth 2.0 authentication

### Key Methods

#### TwitterAgent
- `generateTweet(campaignId)` - Generate AI-powered tweet
- `postTweet(content)` - Post tweet to Twitter
- `respondToMention(id, context)` - Respond to mention
- `scanTrends()` - Analyze trending topics
- `optimizeContent(previousResults)` - Optimize based on performance

#### A/B Testing
- `runABTest(variants, campaignId, config)` - Run A/B test
- `getTestResults(testId)` - Get test results
- `cancelTest(testId)` - Cancel running test

#### Contingency Control
- `pauseAgent(name, reason)` - Pause agent
- `resumeAgent(name)` - Resume agent
- `emergencyStopAll(reason)` - Stop all agents
- `isAgentPaused(name)` - Check pause status

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🆘 Support

- **Documentation**: [GitHub Wiki](https://github.com/neonhub/twitter-agent-v2/wiki)
- **Issues**: [GitHub Issues](https://github.com/neonhub/twitter-agent-v2/issues)
- **Discussions**: [GitHub Discussions](https://github.com/neonhub/twitter-agent-v2/discussions)

## 🔄 Changelog

### v2.0.0
- ✨ **NEW**: A/B Testing System
- ✨ **NEW**: Influencer Detection
- ✨ **NEW**: Contingency Control
- ✨ **NEW**: Real-time Stream Listening
- ✨ **NEW**: OAuth 2.0 Authentication
- ✨ **NEW**: Media Generation
- ✨ **NEW**: Vector Learning
- ✨ **NEW**: Persona Management
- 🛡️ **ENHANCED**: Brand Safety
- 📊 **ENHANCED**: Metrics & Analytics
- 🔧 **IMPROVED**: Type Safety
- 🚀 **IMPROVED**: Performance

---

**Built with ❤️ by the NeonHub Team** 