# Genesis Sniper Bot

## Overview
Genesis Sniper Bot is an advanced Solana-based cryptocurrency trading bot designed for automated token sniping and trading on the Raydium decentralized exchange. The bot monitors new token pair creations in real-time and executes automated buy/sell orders based on predefined criteria and trading strategies.

## Purpose
- **Automated Token Sniping**: Detects and trades newly created token pairs on Raydium DEX
- **Real-time Monitoring**: Continuously monitors Solana blockchain for new liquidity pool creations
- **Strategic Trading**: Implements limit orders, stop-loss, and take-profit mechanisms
- **Multi-user Support**: Manages trading operations for multiple users with individual configurations

## Operational Flow
1. **Pool Detection**: Monitors Solana blockchain for new Raydium pool creation events
2. **Token Analysis**: Extracts token metadata, liquidity information, and validates trading criteria
3. **Automated Trading**: Executes buy orders for qualifying tokens based on user settings
4. **Position Management**: Tracks trades, implements stop-loss/take-profit strategies
5. **Database Logging**: Records all trading activities, coin data, and user positions

## Project Structure
```
genesis_sniper_bot/
├── database/                    # Database models and functions
│   ├── models.py               # SQLAlchemy models (Coin, Pair, Trade, LimitOrder)
│   ├── ca_functions.py         # Database operations and queries
│   ├── client.py               # Database client configuration
│   └── database.py             # Database connection setup
├── utils/                      # Utility modules and trading logic
│   ├── raydium/               # Raydium DEX integration
│   │   ├── Raydium.py         # Main Raydium trading logic
│   │   ├── buy_swap.py        # Buy transaction implementation
│   │   ├── sell_swap.py       # Sell transaction implementation
│   │   └── volumeGenerator.py # Volume generation utilities
│   ├── solana_metadata/       # Solana token metadata handling
│   ├── sol_swaps.py           # Solana swap operations
│   ├── solana_trade_utils.py  # Solana trading utilities
│   ├── get_pool_keys.py       # Pool key extraction
│   └── layouts.py             # Data structure layouts
├── newPairs.py                # Main sniping script for new pairs
├── op_newPairs.py             # Optimized version with enhanced features
├── requirements.txt           # Project dependencies
└── .env-example              # Environment variables template
```

## Programming Language
**Python 3.x** - The entire project is built using Python with extensive use of async/await patterns for high-performance blockchain interactions.

## Key Tools and Technologies
- **solana-py**: Solana blockchain interaction library
- **SQLAlchemy**: Database ORM for data management
- **MySQL**: Primary database for storing trading data
- **websockets**: Real-time blockchain event monitoring
- **asyncio**: Asynchronous programming for concurrent operations
- **python-dotenv**: Environment variable management
- **Alembic**: Database migration management

## Core Features

### �� Token Sniping
- Real-time detection of new Raydium liquidity pools
- Automated filtering based on liquidity thresholds
- Instant buy execution upon pool creation
- Support for SOL-based trading pairs

### �� Trading Management
- Limit order functionality with customizable parameters
- Stop-loss and take-profit mechanisms
- Trailing stop-loss implementation
- Multi-strategy trading support

### ��️ Database Architecture
- **Coins**: Token contract addresses, metadata, and supply information
- **Pairs**: Trading pair data with liquidity and price information
- **Trades**: Complete transaction history with timestamps and status
- **LimitOrders**: Automated order management with price targets

### ⚡ Performance Features
- Asynchronous blockchain monitoring
- Concurrent trade execution for multiple users
- Optimized transaction confirmation
- Real-time price tracking and analysis

## Installation and Setup

### Prerequisites
- Python 3.8+
- MySQL Server and Workbench
- Solana RPC endpoint access

### Installation Steps
1. **Clone Repository**
   ```bash
   git clone https://github.com/ptechfusion19/genesis_sniper_bot
   cd genesis_sniper_bot
   ```

2. **Install Dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **Database Setup**
   - Create MySQL database: `genesis_sniper_bot`
   - Configure Alembic for migrations
   - Run initial migration to create tables

4. **Environment Configuration**
   - Copy `.env-example` to `.env`
   - Configure Solana RPC endpoints
   - Set trading parameters and private keys
   - Configure database connection strings

### Configuration Parameters
- `SOLANA_RPC`: Solana RPC endpoint URL
- `RAYDIUM_PUBLIC_KEY`: Raydium program public key
- `AMOUNT_PER_SNIPE`: Default SOL amount for sniping
- `MINIMUM_LIQUIDITY`: Minimum liquidity threshold
- `STOP_LOSS` / `TAKE_PROFIT`: Risk management percentages
- `PRIVATE_KEY`: Wallet private key for transactions

## Usage
1. **Start Main Sniping Bot**: `python newPairs.py`
2. **Run Optimized Version**: `python op_newPairs.py`
3. **Monitor Logs**: Check console output for real-time trading activity
4. **Database Monitoring**: Use MySQL Workbench to track trades and positions

## Security Considerations
- Store private keys securely using environment variables
- Use dedicated trading wallets with limited funds
- Implement proper error handling for failed transactions
- Regular backup of trading database
- Monitor for unusual trading patterns

## Development Notes
- Built with modular architecture for easy extension
- Extensive use of async/await for blockchain operations
- Comprehensive error handling and logging
- Database-first approach for trade tracking
- Optimized for high-frequency trading scenarios
