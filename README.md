# Crypto Whale Trade Alert System

## Overview

This project is a Python-based tool that monitors cryptocurrency exchanges for large (or "whale") trades. It leverages the CCXT library to access trade data from various exchanges and checks for trades that exceed a specified USD threshold. When a whale trade is detected, the system logs it locally and optionally sends an email alert.

## Features

- **Real-Time Trade Monitoring**: Continuously monitors trades on configured exchanges and trading pairs.
- **Whale Trade Detection**: Identifies trades above a configurable USD threshold.
- **Email Notifications**: Sends email alerts for detected whale trades.
- **Rate Limit Management**: Automatically handles rate limits to prevent API request overload.
- **Flexible Configuration**: Settings for exchanges, cryptocurrencies, trade size threshold, polling interval, and email options are configurable via a JSON file.

## Requirements

- **Python**: Version 3.6+
- **CCXT**: A cryptocurrency trading library in Python for accessing trade data on supported exchanges.
- **smtplib**: For email alerts.
- **json**: To load and manage configuration settings.
- **datetime**: To manage timestamps and log entries.

## Setup

1. **Clone the Repository**:

2. **Install Dependencies**:
   Install required libraries using pip:
   ```
   pip install ccxt
   ```

3. **Configure Settings**:
   Create a `config.json` file based on the template below. This file will store exchange configurations, cryptocurrency pairs, trade thresholds, polling intervals, and email settings.

   ### Sample `config.json` File
   ```json
   {
       "exchanges": ["binance", "coinbasepro"],
       "cryptocurrencies": ["BTC/USDT", "ETH/USDT"],
       "minimum_trade_size_usd": 100000,
       "polling_interval_seconds": 60,
       "email": {
           "enable_email_alerts": true,
           "smtp_server": "smtp.your-email-provider.com",
           "smtp_port": 465,
           "sender_email": "your-email@example.com",
           "receiver_email": "recipient-email@example.com",
           "sender_password": "your-email-password"
       }
   }
   ```

4. **Run the Script**:
   Start monitoring for whale trades by running:
   ```
   py whale_alert.py
   ```

## Code Explanation

### Main Components

1. **Configuration Loader**: Reads `config.json` to load exchange settings, cryptocurrency pairs, trade size threshold, polling interval, and email settings.
   
2. **Exchange Setup**: Initializes exchanges listed in the configuration, enabling rate limiting to manage API request limits.

3. **Trade Monitoring**:
   - Loops over configured exchanges and cryptocurrency pairs.
   - Fetches recent trades and calculates the trade size in USD.
   - Logs trades that exceed the `MINIMUM_TRADE_SIZE`.

4. **Email Alerts**:
   - If email alerts are enabled, sends an email with trade details when a whale trade is detected.

5. **Logging**: Logs whale trades to a `whale_trades.log` file with timestamps.

## Configuration Options

- **exchanges**: List of exchange IDs (as defined inprint('sacpgh')