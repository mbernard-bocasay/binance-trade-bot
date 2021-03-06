# binance-trade-bot
>Automated cryptocurrency trading bot

## Why
This script was inspired by the observation that all cryptocurrencies pretty much behave in the same way. When one spikes, they all spike, and when one takes a dive, they all do. *Pretty much*. Moreover, all coins follow Bitcoin's lead; the difference is their phase offset. 

So, if coins are basically oscillating with respect to each other, it seems smart to trade the rising coin for the falling coin, and then trade back when the ratio is reversed. 

## How
The way the bot takes advantage of this behaviour is to always downgrade from the "strong" coin to the "weak" coin, under the assumption that at some point the tables will turn. It will then return to the original coin, ultimately holding more of it than it did originally. This is done while taking into consideration the trading fees. 

The trading is done in the Binance market platform, which of course does not have markets for every altcoin pair. The workaround for this is to use Tether (USDT), which is stable by design, as a bridge currency. 
<p align="center">
  Coin A -> USDT -> Coin B
</p>

The bot jumps between a configured set of coins on condition that it does not return to a coin unless it is profitable in   respect to the amount held last. This means that we will never end up having less of a certain coin. The risk is that one of the coins may freefall relative to the others all of a sudden, attracting our reverse greedy algorithm. 

## Binance Setup
* [Create a Binance account.](https://www.binance.com/hw_register.html)
* Enable Two-factor Authentication.
* Create a new API key.
* Get a cryptocurrency. if its symbol is not in the default list, add it.

## Tool Setup
### Install deps
`pip install -r requirments.txt`

### Create user configuration
Create a .ini file named `user.cfg` based off `.user.cfg.example`, then add your API keys and current coin.

### Run
`./crypto_trading.py`

<p align="center">
  <img src = "https://usercontent2.hubstatic.com/6061829.jpg">
</p>
