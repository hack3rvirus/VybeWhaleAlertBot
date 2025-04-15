# My VybeWhaleAlertBot 🐳

I’m thrilled to share my Telegram bot, VybeWhaleAlertBot, which I created for the Vybe Telegram Bot Challenge. This bot delivers real-time on-chain crypto analytics using Vybe APIs, and I’ve worked hard to make it a powerful tool for the crypto community. It tracks whale transactions, token metrics, and wallet activity, featuring interactive inline keyboards and links to AlphaVybe for deeper insights. Let me walk you through what I’ve built!

## Features
Here’s what I’ve included in my bot:
- **Whale Alerts 🐋**: I’ve set it up so you can choose a custom threshold and get real-time alerts for large transactions. It checks periodically every 120 seconds (I adjusted this from 60 seconds to avoid API issues).
- **Token Metrics 📈**: You can check token prices, 24h price changes, and trend indicators (upward, downward, or stable) for tokens like SOL, USDC, and USDT.
- **Wallet Tracking 🔍**: It monitors Solana wallet activity and displays the last 3 transactions.
- **Interactive Inline Keyboards**: I added buttons to make navigation seamless, such as "Check Again" or "Set New Threshold."
- **Input Validation**: I made sure it only accepts valid token symbols and wallet addresses to prevent errors.
- **AlphaVybe Integration**: Every response includes a link to [AlphaVybe](https://vybe.fyi/) for deeper analytics.
- **Error Handling**: I’ve included actionable buttons to retry or get help whenever errors occur.

## Getting Started

### Prerequisites
Here’s what I used to build and test the bot:
- Python 3.13+ (I tested it with 3.13.2)
- A Telegram bot token (I got mine from [BotFather](https://t.me/BotFather))
- A Vybe API key (I reached out to @ericvybes on Telegram to get one)

### Installation
I’ll guide you through setting it up on your machine:
1. **Clone the Repository**:
   ```bash
   git clone https://github.com/hack3rvirus/VybeWhaleAlertBot.git
   cd vybe-whale-alert-bot
2. **Set Up a Virtual Environment**:
   ```bash
   python -m venv .venv
   .venv\Scripts\activate 
3. **Install Dependencies**:
   ```bash
   pip install -r requirements.txt
4. **Set Up Environment Variables**:
- I created a .env file in the project root with these variables:
   ```text
  TELEGRAM_TOKEN=your_telegram_bot_token
  VYBE_API_KEY=your_vybe_api_key

## Deployment
I decided to host my bot using both Railway and Render to keep it running 24/7. Here’s how I did it.

### Deployment on Railway
1. **Sign Up for Railway**:
I went to railway.app and signed up with my GitHub account.

2. **Push My Code to GitHub**:
Since I hadn’t committed anything yet, I ran these commands to push my code
   ```bash
    git init
    git add .
    git commit -m "Initial commit: Vybe Whale Alert Bot with working features"
    git remote add origin https://github.com/hack3rvirus/VybeWhaleAlertBot.git
    git branch -M main
    git push -u origin main
   
3. **Deploy on Railway**:
- I logged into Railway, clicked "New Project" > "Deploy from GitHub Repo," selected my vybe-whale-alert-bot repo, and clicked "Deploy."
- I went to the "Variables" tab and added:
  - TELEGRAM_TOKEN: My Telegram bot token
  - VYBE_API_KEY: My Vybe API key
- In the "Settings" tab, I set the "Start Command" to:
  ```text
  python bot.py
- Railway deployed my bot, and I checked the "Logs" tab to ensure it was running smoothly.
    
### Deployment on Render
1. **Sign Up for Render**:
- I also deployed to Render by signing up with my GitHub account.
2. **Deploy on Render**:
- I clicked "New" > "Background Worker," connected my GitHub account, and selected my vybe-whale-alert-bot repo.
- I configured the app with:
  - Build Command: pip install -r requirements.txt
  - Start Command: python bot.py
- I added the following environment variables:
  - TELEGRAM_TOKEN: My Telegram bot token
  - VYBE_API_KEY: My Vybe API key
- I deployed the bot and monitored the logs to confirm it started successfully.
3. **Test It**:
- I opened Telegram and tested my bot at @vybe_realtime_crypto_bot. It’s working perfectly on both platforms! Since I can’t have two instances running at once (they’d both respond to the same token), I kept the Railway deployment active and paused the Render one for now.

## My Development Updates
I faced a few challenges while building this bot, but I’m proud of how it turned out. Initially, the /token command wasn’t working because I was using the wrong Vybe API endpoint. I tried /tokens to fetch a list of tokens, but the response wasn’t a list, causing errors like "API response is not a list of tokens." After diving into the Vybe API docs, I found the correct endpoint: /token/{mintAddress}, which returns stats for a specific token (like SOL). Switching to that endpoint fixed the issue, and now commands like /token sol and /token usdc work flawlessly, showing the price, 24h change, and trend.

I also adjusted the whale alert scheduler from 60 seconds to 120 seconds to avoid hitting API rate limits, ensuring the bot runs smoothly. Finally, I successfully pushed my code to GitHub and deployed it to both Railway and Render. Seeing the bot live and responding to commands in Telegram feels so rewarding!

## Usage Examples
Here’s how I use my bot on Telegram:

- **Set a Threshold**:
    - I type /start or click "Set Threshold 🐋."
    - I enter a threshold (e.g., 10000) to get alerts for transactions above $10,000.
- **Check Whale Alerts**:
  - I type /check or click "Check Whale Alerts 📊."
  - It notifies me of large transactions with buttons to "Check Again" or "Set New Threshold."
- **Token Metrics**:
  - I type /token or click "Token Stats 📈."
  - I enter a token symbol (e.g., SOL) to see its price, 24h change, and trend indicator (e.g., 📈 Upward Trend).
- **Wallet Tracking**:
  - I type /wallet or click "Wallet Tracker 🔍."
  - I enter a Solana wallet address (e.g., 5oNDL...) to see its recent activity.
- **Help**:
  - I type /help or click "Help ℹ️" to see all features and actions.

## Metrics Provided
  Here’s what my bot shows:
- Whale Alerts: Transaction amount in USD, with a link to AlphaVybe.
- Token Metrics: Price in USD, 24h price change percentage, and a trend indicator (upward/downward/stable).
- Wallet Activity: Last 3 transactions with amounts in USD, linked to AlphaVybe.

## License
I’ve licensed this project under the MIT License—see the  file for details.

## Contributing
I’d love for others to contribute to my bot! Please feel free to open an issue or submit a pull request on GitHub.

   

