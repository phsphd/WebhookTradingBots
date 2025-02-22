# Webhook-Based Trading Bot

## Overview
This trading bot automatically places your trading orders by receiving signals (alerts) from **TradingView** via webhooks. It works with three brokers—**Tradier, Alpaca, and Tradovate**—to execute trades based on the details provided in your TradingView alerts.

---

## How It Works

1. **Receiving Alerts**  
   - When you set up an alert on TradingView, a message (in JSON format) is sent to the bot.
   - The message includes all essential details such as which broker to use, whether to buy or sell, which stock (ticker) to trade, and how many shares.

2. **Checking the Details**  
   - The bot ensures all required information is present.
   - It verifies if the market is open (based on EST) unless running in testing mode.

3. **Placing Orders**  
   - **Tradier:** Formats your order into a proper HTTP request and sends it to Tradier’s system, canceling any previous orders for that stock before placing a new one.
   - **Alpaca:** Uses Alpaca’s API to place your order while ensuring any conflicting orders are canceled before execution.
   - **Tradovate:** Uses Tradovate’s API to automate trading of futures on demo (paper) accounts using TradingView signals.

4. **Logging and Notifications**  
   - The bot sends updates and error messages to **Discord** using webhooks.
   - You receive confirmations when trading signals are processed, along with error notifications if needed.

5. **Extra Features**  
   - The bot can **automatically close or liquidate positions** when required.
   - **Supports after-hours trading** for extended flexibility.

---

## Setting Up Your TradingView Alerts

Use this **webhook URL** for your TradingView alerts:

```
https://webhooknextjs.vercel.app/api/webhook
```

Modify at least two JSON signals—one for **buy** and one for **sell**. Replace the account ID and token with your own **Account ID** and **Access Token**, then paste the appropriate JSON into the TradingView alert message box.

---

## JSON Examples

### 📌 For Tradier Orders

#### **Buy Signal for Tradier**
```json
{
  "Broker": "Tradier",
  "Action": "buy",
  "Ticker": "{{ticker}}",
  "Quantity": "10",
  "LimitPrice": "{{close}}",
  "Tradier_Account_ID": "VA712334962",
  "TradierAccessToken": "YOUR_TRADIER_ACCESS_TOKEN"
}
```

#### **Sell Signal for Tradier**
```json
{
  "Broker": "Tradier",
  "Action": "sell",
  "Ticker": "{{ticker}}",
  "Quantity": "10",
  "LimitPrice": "{{close}}",
  "Tradier_Account_ID": "VA712334962",
  "TradierAccessToken": "YOUR_TRADIER_ACCESS_TOKEN"
}
```

---

### 📌 For Alpaca Orders

#### **Buy Signal for Alpaca**
```json
{
  "Broker": "Alpaca",
  "Action": "buy",
  "Ticker": "{{ticker}}",
  "Quantity": "100",
  "LimitPrice": "{{close}}",
  "API_KEY": "YOUR_ALPACA_API_KEY",
  "API_SECRET": "YOUR_ALPACA_API_SECRET"
}
```

#### **Sell Signal for Alpaca**
```json
{
  "Broker": "Alpaca",
  "Action": "sell",
  "Ticker": "{{ticker}}",
  "Quantity": "100",
  "LimitPrice": "{{close}}",
  "API_KEY": "YOUR_ALPACA_API_KEY",
  "API_SECRET": "YOUR_ALPACA_API_SECRET"
}
```

---

### 📌 For Future Trading on Tradovate

#### **Buy Signal for Tradovate**
```json
{
  "Broker": "Tradovate",
  "Action": "buy",
  "Ticker": "{{ticker}}",
  "Quantity": "1",
  "TakeProfitPoints": "5",
  "StopLossPoints": "4",
  "LimitPrice": "{{close}}",
  "Username": "JohnDoe",
  "Password": "YOUR_PASSWORD",
  "AppId": "Sample App",
  "DeviceId": "5678",
  "API_KEY": "YOUR_TRADOVATE_API_KEY",
  "API_SECRET": "YOUR_TRADOVATE_API_SECRET"
}
```

#### **Sell Signal for Tradovate**
```json
{
  "Broker": "Tradovate",
  "Action": "sell",
  "Ticker": "{{ticker}}",
  "Quantity": "1",
  "TakeProfitPoints": "5",
  "StopLossPoints": "4",
  "LimitPrice": "{{close}}",
  "Username": "JohnDoe",
  "Password": "YOUR_PASSWORD",
  "AppId": "Sample App",
  "DeviceId": "5678",
  "API_KEY": "YOUR_TRADOVATE_API_KEY",
  "API_SECRET": "YOUR_TRADOVATE_API_SECRET"
}
```

---

## Additional Information

### 🔹 Important Notice on Tradovate Futures Trading
- Currently, **Tradovate futures trading** is available only through **demo (paper) accounts**.
- Signals include sensitive credentials. If you need **enhanced security for live trading**, consider our **private webhook server**.

### 🔹 Private Webhook Server Options
- **Lifetime License:** Set up a dedicated webhook server on **Vercel**, **AWS**, **Heroku**, **DigitalOcean**, or **Azure**.
- **Monthly Subscription:** Supports up to **4,000 JSON signals per month**.

### 🔹 Windows Version of the Bot
- A **Windows version** is available for users who prefer **local credential storage**.

---

## ⚠️ Disclosure and Disclaimer
- **All trading involves risk.** The signals provided are for informational purposes only.
- No guarantee is made regarding trade performance. Users must conduct **thorough research** before trading.
- The service is provided on an **"as-is" basis**, and we disclaim liability for **any trading losses incurred**.

---

## Summary
✅ This system eliminates the stress of manual trading.  
✅ Simply set up TradingView alerts and let the bot **automatically execute trades**.  
✅ **Stay informed** via **Discord notifications**.  
✅ Customize the JSON signals to **match your trading strategy**.  

Enjoy **seamless, automated trading** with our Webhook-Based Trading Bot! 🚀

