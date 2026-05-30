# 🎯 Smart Bright Quiz Bot

Production-ready Telegram Quiz Bot using native Quiz Polls with global leaderboards, group rankings, PDF reports, and anti-cheat protection.

## ✨ Features

### Core Features
- ✅ **Telegram Native Quiz Polls Only** - No text-based questions
- ✅ **Quiz Creation** - Easy quiz building with native polls
- ✅ **Multi-Platform** - Works in private chats, groups, supergroups, channels
- ✅ **Timer System** - Configurable per-question time limits (5-300 seconds)
- ✅ **Negative Marking** - Optional negative marking per wrong answer
- ✅ **Instant Sharing** - Share quizzes via deep links

### Advanced Features
- 🏆 **Global Leaderboard** - Real-time player rankings
- 👥 **Group vs Group** - Competitive group leaderboards
- 📊 **Quiz Analytics** - Detailed performance metrics
- 📄 **PDF Reports** - Download quiz results as PDF
- 🛡️ **Anti-Cheat System** - Prevent duplicate answers & cheating
- 🚫 **Anti-Spam** - Rate limiting and abuse prevention
- 💾 **Data Persistence** - Firestore + Local JSON backup
- 🔄 **Auto-Recovery** - 15-minute watchdog for quota recovery
- 🌐 **Multi-Language** - Hindi & English support

## 🚀 Quick Start

### Prerequisites
- Node.js 18+
- Telegram Bot Token (from @BotFather)
- Firebase Project (for Firestore)

### Installation

```bash
git clone https://github.com/gyan565/telegram-quiz-bot.git
cd telegram-quiz-bot
npm install
cp .env.example .env
# Edit .env with your credentials
npm start
```

## 📋 Commands

```
/start           - Start bot & see main menu
/createquiz      - Create new quiz
/myquizzes       - View your saved quizzes
/editquiz        - Edit existing quiz
/deletequiz      - Delete quiz
/duplicatequiz   - Clone a quiz
/leaderboard     - View global rankings
/help            - Help & guidelines
```

## 🎮 Quiz Flow

### Creation
1. `/createquiz` → Enter quiz name
2. Add questions using Telegram native poll creator
3. Insert media/messages if needed (optional)
4. `/done` → Set timer & negative marking
5. Preview & confirm

### Playing
1. Start quiz (private or group)
2. Answer each poll question
3. Auto-timer advances to next question
4. View final score & leaderboard
5. Download PDF report (optional)

## 🏗️ Project Structure

```
telegram-quiz-bot/
├── src/
│   ├── index.js                 # Main bot entry
│   ├── config/
│   │   ├── firebase.js          # Firebase initialization
│   │   └── constants.js         # Constants & configs
│   ├── handlers/
│   │   ├── commands.js          # Command handlers
│   │   ├── callbacks.js         # Button callbacks
│   │   ├── poll.js              # Poll handling
│   │   └── messages.js          # Message handlers
│   ├── services/
│   │   ├── quiz.js              # Quiz logic
│   │   ├── leaderboard.js       # Leaderboard system
│   │   ├── user.js              # User management
│   │   └── data.js              # Data layer
│   └── utils/
│       ├── validators.js        # Input validation
│       ├── recovery.js          # Auto-recovery watchdog
│       └── logger.js            # Logging
├── data/
│   ├── quizzes.json             # Quiz storage
│   ├── users.json               # User profiles
│   ├── leaderboard.json         # Global rankings
│   └── groupStats.json          # Group statistics
├── .env.example
├── .gitignore
├── package.json
└── README.md
```

## 📊 Data Storage

### Firestore Collections
- **quizzes/** - All quiz data
- **users/** - User profiles
- **leaderboard/** - Global rankings
- **groupStats/** - Group statistics
- **quizHistory/** - Quiz play history

### Local Backup
- **/data/** - JSON backups (fallback when Firestore unavailable)
- **/backup/** - Timestamped backups

## 🌐 Deployment

### Railway (Recommended)
1. Push code to GitHub
2. Connect Railway to GitHub repo
3. Add environment variables in Railway dashboard
4. Railway auto-deploys on push

### VPS (Ubuntu/Debian)
```bash
ssh root@your_vps_ip
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt-get install -y nodejs

git clone https://github.com/gyan565/telegram-quiz-bot.git
cd telegram-quiz-bot
npm install

# Create .env file
nano .env

# Start with PM2
npm install -g pm2
pm2 start src/index.js --name "quiz-bot"
pm2 startup
pm2 save
```

### Docker
```bash
docker-compose up -d
```

## 🔐 Security

- ✅ Rate limiting on all commands
- ✅ User validation & authentication
- ✅ Anti-cheat detection
- ✅ Anti-spam protection
- ✅ Input sanitization
- ✅ Firebase security rules
- ✅ Secure backup system

## 📝 Environment Variables

Create `.env` file from `.env.example`:

```
BOT_TOKEN=your_telegram_bot_token
FIREBASE_PROJECT_ID=your_firebase_project_id
FIREBASE_PRIVATE_KEY=your_firebase_private_key
FIREBASE_CLIENT_EMAIL=your_firebase_client_email
NODE_ENV=production
PORT=3000
```

## 🐛 Troubleshooting

### Bot not responding
- Check BOT_TOKEN in .env
- Verify bot is not running elsewhere
- Check logs for errors

### Data not persisting
- Verify Firebase credentials
- Check Firestore quota
- Review backup files in /data

### Firestore quota exceeded
- Bot automatically falls back to local JSON
- Data is safe in /data directory
- Watchdog auto-recovers when quota resets

## 📄 License

MIT License - See LICENSE file

## 🤝 Support

For issues or questions:
1. Check README & documentation
2. Review GitHub issues
3. Contact maintainer

## 🎯 Roadmap

- [ ] Channel quizzes
- [ ] Custom reward system
- [ ] Daily challenges
- [ ] Web dashboard
- [ ] Mobile app

---

**Made with ❤️ by Quiz Bright**