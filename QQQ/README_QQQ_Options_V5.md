# QQQ Options V5 — Clean Supply/Demand Guide

> **Purpose:** This README explains how to read and use the `QQQ Options V5 - Clean` TradingView indicator in a simple, repeatable way.
>
> **Important:** This indicator is a decision-support tool, not a guarantee of profit. Options are leveraged products and can lose value quickly. Always define risk before entering a trade, and paper-trade the system before using meaningful capital.

---

## 1. What the Indicator Does

The indicator is designed for **QQQ on the 5-minute chart**.

It combines:

- QQQ price trend
- EMA 9 / EMA 21 / EMA 50
- VWAP
- RSI and MACD momentum
- ADX trend strength
- Relative volume
- AMD confirmation
- SOXX confirmation
- Additional large-cap / semiconductor leadership
- VIX effect
- Supply zones
- Demand zones
- Entry, stop, and target references

The goal is to answer three questions:

1. **What direction is QQQ leaning?**
2. **Is the broader market confirming that direction?**
3. **Is QQQ in a good location to enter the trade?**

The third question is important. A bullish signal directly under supply can be a poor CALL entry. A bearish signal directly above demand can be a poor PUT entry.

---

## 2. Recommended Chart Setup

Use:

- **Symbol:** QQQ
- **Timeframe:** 5 minutes
- **Candles:** Standard candles
- **Indicator:** QQQ Options V5 - Clean

The script already displays:

- EMA 9
- EMA 21
- EMA 50
- VWAP
- Supply zones
- Demand zones
- Latest CALL / PUT signal
- Dashboard

For the cleanest chart, remove or hide other EMA, VWAP, supply/demand, and signal indicators that duplicate what this script already displays.

---

## 3. The Basic Trading Workflow

Do not trade from one dashboard number alone.

Read the indicator in this order:

```text
1. MARKET STATUS
        ↓
2. CONFIDENCE
        ↓
3. AMD + SOXX
        ↓
4. VWAP + EMA
        ↓
5. ADX + VOLUME
        ↓
6. SUPPLY / DEMAND LOCATION
        ↓
7. ENTRY / STOP / TARGETS
```

Think of it as:

```text
DIRECTION → CONFIRMATION → LOCATION → RISK
```

---

## 4. Market Status

### STRONG CALL
Strong bullish alignment. Do not automatically buy a CALL just because this appears. Check supply/demand first.

### CALL
Bullish conditions are aligned enough to qualify as a CALL setup.

### CALL WATCH
The model is leaning bullish, but the complete CALL requirements are not satisfied yet.

Treat this as:

```text
PAY ATTENTION — DO NOT ENTER YET
```

### STRONG PUT
Strong bearish alignment. Before entering, check that QQQ is not sitting directly on demand.

### PUT
Bearish conditions are aligned enough to qualify as a PUT setup.

### PUT WATCH
Bearish pressure exists, but the complete PUT setup is not ready.

### WAIT
There is not enough alignment to justify a directional trade.

---

## 5. Confidence

Confidence converts the model's directional score into a 0–100 scale.

| Reading | Meaning |
|---|---|
| 88%+ | STRONG CALL territory |
| 75%+ | CALL territory |
| 60–74.9% | CALL WATCH area |
| 40–60% | Neutral / mixed |
| 25–40% | PUT WATCH area |
| 25% or lower | PUT territory |
| 12% or lower | STRONG PUT territory |

Confidence measures **alignment**, not a guaranteed probability of profit.

An 88% confidence reading does **not** mean the trade has an 88% chance of winning.

---

## 6. Trend

The Trend score ranges approximately from -100 to +100.

| Trend | Meaning |
|---:|---|
| +70 to +100 | Strong bullish trend |
| +20 to +69 | Bullish |
| -19 to +19 | Mixed / neutral |
| -20 to -69 | Bearish |
| -70 to -100 | Strong bearish trend |

The trend engine uses:

- EMA 9 vs EMA 21
- price vs EMA 50
- EMA 50 direction
- price vs VWAP

---

## 7. Momentum

Momentum measures how strongly price is currently moving.

It includes:

- RSI
- MACD histogram
- recent price movement

Positive numbers favor CALLs. Negative numbers favor PUTs.

---

## 8. Leadership

Leadership asks whether important QQQ and semiconductor-related symbols agree with the direction.

The model checks:

- AMD
- NVDA
- SOXX
- AVGO
- TSM
- MSFT
- AAPL
- AMZN
- META
- SPY
- VIX effect

AMD receives the largest individual model weight.

A positive Leadership score supports CALLs. A negative Leadership score supports PUTs.

---

## 9. AMD and SOXX

For a CALL, the default setup expects:

```text
AMD = BULLISH
SOXX = BULLISH
```

For a PUT:

```text
AMD = BEARISH
SOXX = BEARISH
```

If QQQ points one way but AMD or SOXX strongly disagree, the setup is weaker.

---

## 10. VWAP

For CALLs:

```text
VWAP = ABOVE
```

For PUTs:

```text
VWAP = BELOW
```

VWAP helps identify whether QQQ is trading on the stronger or weaker side of the session.

---

## 11. EMA Alignment

### Bullish EMA
- EMA 9 above EMA 21
- price above EMA 9
- price above EMA 50

### Bearish EMA
- EMA 9 below EMA 21
- price below EMA 9
- price below EMA 50

### Mixed
The moving averages and price are not aligned enough for a clean directional setup.

---

## 12. ADX

ADX measures trend strength, not direction.

Default requirement:

```text
ADX >= 18
```

Examples:

```text
ADX 24.5 OK
ADX 14.2 LOW
```

Low ADX can indicate choppy conditions.

---

## 13. Relative Volume

Examples:

```text
0.55x → relatively quiet
1.00x → around average
1.50x → elevated
2.00x+ → significantly elevated
```

Volume confirmation is optional by default, but higher participation can improve the quality of a directional move.

---

## 14. Supply Zones

A red box is a **SUPPLY ZONE**.

Think of it as an area where sellers previously became strong enough to create a confirmed swing high.

```text
                 SUPPLY ZONE
        ┌────────────────────────┐
        │                        │
        └────────────────────────┘
                     ↑
              possible resistance
```

Supply is an area, not an exact price and not a guaranteed reversal point.

---

## 15. Demand Zones

A green box is a **DEMAND ZONE**.

```text
              possible support
                     ↓
        ┌────────────────────────┐
        │                        │
        └────────────────────────┘
                 DEMAND ZONE
```

Demand is also an area rather than a guaranteed reversal point.

---

## 16. Zone Status

### AT SUPPLY
QQQ is currently inside active supply.

Be cautious with new CALLs. The script intentionally prevents a normal CALL confirmation while price is inside supply.

### AT DEMAND
QQQ is currently inside active demand.

Be cautious with new PUTs. The script intentionally prevents a normal PUT confirmation while price is inside demand.

### BETWEEN ZONES
QQQ is not inside the tracked supply or demand zones.

This can be tradable, but you must check how much room remains to the next opposing zone.

---

## 17. Nearest Supply and Demand

Example:

```text
QQQ              723.50
Nearest Supply   725.10
```

Approximate bullish room:

```text
725.10 - 723.50 = $1.60
```

For PUTs, compare current price with Nearest Demand in the same way.

A trade with only a few cents of room before an opposing zone may have poor location even when the directional model is strong.

---

## 18. Good CALL Setup

```text
MARKET STATUS      CALL / STRONG CALL
CONFIDENCE         75%+
Trend              BULLISH
Momentum           BULLISH
Leadership         BULLISH
AMD                BULLISH
SOXX               BULLISH
VWAP               ABOVE
EMA                BULLISH
ADX                OK
Zone               AT DEMAND or BETWEEN ZONES
Nearest Supply     Enough room above
```

A strong location is often a bullish confirmation after QQQ holds or rejects demand.

---

## 19. Good PUT Setup

```text
MARKET STATUS      PUT / STRONG PUT
CONFIDENCE         25% or lower
Trend              BEARISH
Momentum           BEARISH
Leadership         BEARISH
AMD                BEARISH
SOXX               BEARISH
VWAP               BELOW
EMA                BEARISH
ADX                OK
Zone               AT SUPPLY or BETWEEN ZONES
Nearest Demand     Enough room below
```

A strong location is often a bearish rejection from supply.

---

## 20. When NOT to Buy a CALL

Avoid or reconsider a CALL when:

- QQQ is already inside supply
- supply is extremely close overhead
- AMD is bearish
- SOXX is bearish
- QQQ is below VWAP
- EMA is bearish or mixed
- ADX is weak
- confidence is only CALL WATCH
- the candle has not closed
- the move already looks extended
- the reward does not justify the risk

Example:

```text
STRONG CALL
Confidence         91%
QQQ                725.00
Nearest Supply     725.08
```

The direction may be bullish while the entry location is poor.

---

## 21. When NOT to Buy a PUT

Avoid or reconsider a PUT when:

- QQQ is already inside demand
- demand is extremely close below
- AMD is bullish
- SOXX is bullish
- QQQ is above VWAP
- EMA is bullish or mixed
- ADX is weak
- confidence is only PUT WATCH
- the move is already heavily extended

Example:

```text
STRONG PUT
Confidence         10%
QQQ                723.60
Nearest Demand     723.49
```

There may be too little downside room for a fresh entry.

---

## 22. Entry, Stop, Targets

The dashboard Entry, Stop, Target 1, and Target 2 are based on **QQQ price**, not option premium.

### Stop
Bullish:

```text
Stop = Entry - ATR × Stop Multiplier
```

Bearish:

```text
Stop = Entry + ATR × Stop Multiplier
```

### Targets
Default:

```text
Target 1 = 1.5 ATR
Target 2 = 2.5 ATR
```

Use these as reference levels for the underlying QQQ trade thesis.

---

## 23. R / R

R / R means reward-to-risk ratio.

Example:

```text
R / R = 2.50 : 1
```

This means Target 2 is approximately 2.5 times farther from entry than the stop.

It does not guarantee profit.

---

## 24. Closed-Candle Rule

The indicator confirms signals on closed candles.

On a 5-minute chart, wait for the 5-minute candle to finish before treating a CALL or PUT as confirmed.

Avoid acting on temporary intrabar conditions.

---

## 25. Latest Signal Label

The chart keeps only the most recent qualifying trade label.

When a new CALL or PUT occurs, the previous label is deleted.

This is intentional to keep the chart clean.

---

## 26. CALL Checklist

- [ ] QQQ is on the 5-minute chart
- [ ] Candle has closed
- [ ] Status is CALL or STRONG CALL
- [ ] Confidence is at least 75%
- [ ] AMD is bullish
- [ ] SOXX is bullish
- [ ] VWAP says ABOVE
- [ ] EMA says BULLISH
- [ ] ADX is OK
- [ ] QQQ is not inside supply
- [ ] There is reasonable room to nearest supply
- [ ] Stop level is known before entry
- [ ] Position size is based on acceptable loss
- [ ] Reward justifies the risk

---

## 27. PUT Checklist

- [ ] QQQ is on the 5-minute chart
- [ ] Candle has closed
- [ ] Status is PUT or STRONG PUT
- [ ] Confidence is 25% or lower
- [ ] AMD is bearish
- [ ] SOXX is bearish
- [ ] VWAP says BELOW
- [ ] EMA says BEARISH
- [ ] ADX is OK
- [ ] QQQ is not inside demand
- [ ] There is reasonable room to nearest demand
- [ ] Stop level is known before entry
- [ ] Position size is based on acceptable loss
- [ ] Reward justifies the risk

---

## 28. CALL WATCH / PUT WATCH

A WATCH condition is not a trade.

Use:

```text
CALL WATCH
```

as a reason to prepare for a possible bullish setup.

Use:

```text
PUT WATCH
```

as a reason to prepare for a possible bearish setup.

Workflow:

```text
WATCH
  ↓
wait for confirmation
  ↓
CALL / PUT
  ↓
check location
  ↓
decide whether the trade is worth taking
```

---

## 29. Options Contract Selection

The indicator analyzes **QQQ**, not the option contract itself.

When selecting an option, separately consider:

- expiration
- strike
- delta
- bid/ask spread
- liquidity
- implied volatility
- time decay
- contract cost

A good QQQ directional setup can still produce a poor options trade if the contract is badly selected.

---

## 30. Position Sizing

The indicator does not decide how much money you should risk.

Before entering, define:

```text
Maximum acceptable loss per trade
```

Then size the position so a losing trade does not create an unacceptable portfolio loss.

Do not increase position size simply because the dashboard says STRONG CALL or STRONG PUT.

---

## 31. Alerts

Available alert conditions include:

```text
QQQ CALL
QQQ PUT
QQQ ENTERED SUPPLY
QQQ ENTERED DEMAND
```

When appropriate, configure TradingView alerts for **Once Per Bar Close** so alert behavior matches the closed-candle signal logic.

---

## 32. Track Your Results

Do not judge the indicator from a few trades.

Track at least:

```text
Date
Time
CALL / PUT
Confidence
AMD
SOXX
VWAP
EMA
ADX
Volume
Entry
Stop
Target 1
Target 2
Supply
Demand
Result
Maximum favorable move
Maximum adverse move
```

Paper-trading 50–100 setups can provide much better evidence than judging a few signals visually.

---

## 33. Measure Expectancy

Do not optimize only for win rate.

```text
Expectancy =
(Win Rate × Average Win)
-
(Loss Rate × Average Loss)
```

A strategy can be profitable without winning every trade, and a high win-rate strategy can still lose money if losses are much larger than winners.

---

## 34. Quick Reference

### CALL

```text
STATUS      CALL / STRONG CALL
CONFIDENCE  75%+
AMD         BULLISH
SOXX        BULLISH
VWAP        ABOVE
EMA         BULLISH
ADX         OK
LOCATION    NOT AT SUPPLY
TARGET      toward next supply
```

### PUT

```text
STATUS      PUT / STRONG PUT
CONFIDENCE  25% or lower
AMD         BEARISH
SOXX        BEARISH
VWAP        BELOW
EMA         BEARISH
ADX         OK
LOCATION    NOT AT DEMAND
TARGET      toward next demand
```

### SKIP

```text
CALL WATCH
PUT WATCH
WAIT
Low ADX
Mixed EMA
CALL directly into supply
PUT directly into demand
Poor reward/risk
Unconfirmed candle
```

---

## 35. The Most Important Principle

The dashboard answers:

```text
WHAT DIRECTION?
```

Supply and demand answer:

```text
WHERE SHOULD I CARE?
```

Risk management answers:

```text
HOW MUCH CAN I AFFORD TO BE WRONG?
```

A complete trade requires all three.

```text
DIRECTION
    +
LOCATION
    +
RISK CONTROL
    =
A TRADE WORTH EVALUATING
```

---

## 36. Risk Disclosure

Options involve risk and are not suitable for all investors. Options can provide leverage, which can amplify both gains and losses. Long options can lose value as expiration approaches, and option pricing is affected by factors beyond the movement of QQQ.

Before trading exchange-listed options, traders should review the Options Clearing Corporation's **Characteristics and Risks of Standardized Options** and their broker's options disclosures and approval requirements.

This project and indicator are provided for educational and research purposes only. They do not constitute personalized investment advice, a recommendation to buy or sell any security, or a guarantee of trading results.
