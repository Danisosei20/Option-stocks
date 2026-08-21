# AMD Options V1 — Clean Supply/Demand Guide

> **Purpose:** This README explains how to read and use the `AMD Options V1 - Clean` TradingView indicator.
>
> **Important:** This indicator is a decision-support tool, not a guarantee of profit. AMD options can move quickly and carry significant risk. Paper-trade the system before using meaningful capital.

---

## 1. What This Indicator Is For

This indicator is designed to help trade **AMD on the 5-minute chart**.

It analyzes AMD itself first, then uses the broader market and semiconductor sector as confirmation.

The model combines:

* AMD EMA 9 / 21 / 50
* AMD VWAP
* AMD RSI and MACD momentum
* AMD ADX trend strength
* AMD relative volume
* AMD supply and demand zones
* QQQ confirmation
* SOXX confirmation
* NVDA confirmation
* SMH confirmation
* SPY confirmation
* AVGO confirmation
* TSM confirmation
* Entry, stop, and target references
* CALL / PUT / WAIT status

The goal is to answer:

```text
1. What direction is AMD moving?
2. Is the semiconductor / market environment confirming it?
3. Is AMD in a good location to enter?
4. Is there enough room before supply or demand?
```

---

# 2. Recommended Chart Setup

Use:

```text
Symbol:       AMD
Timeframe:    5 minutes
Candles:      Standard candles
Indicator:    AMD Options V1 - Clean
```

The script already shows:

* EMA 9
* EMA 21
* EMA 50
* VWAP
* Supply zones
* Demand zones
* Latest CALL / PUT label
* Dashboard

For the cleanest chart, remove duplicate EMA, VWAP, or supply/demand indicators.

---

# 3. How the Model Is Weighted

AMD itself controls most of the final decision.

```text
AMD Trend             35%
AMD Momentum          20%
AMD Institutional     20%
External Leadership   25%
```

That means **75% of the model comes from AMD itself**.

The external market is used mainly to confirm AMD, not to override it.

---

# 4. External Confirmation Weights

The external leadership score uses:

```text
QQQ     22%
SOXX    22%
NVDA    18%
SMH     15%
SPY      8%
AVGO     8%
TSM      7%
```

QQQ and SOXX have the largest external influence because they provide broad technology and semiconductor confirmation.

---

# 5. Read the Dashboard in This Order

Use this sequence:

```text
MARKET STATUS
      ↓
CONFIDENCE
      ↓
AMD TREND + MOMENTUM
      ↓
QQQ + SOXX + NVDA + SMH
      ↓
VWAP + EMA
      ↓
ADX + VOLUME
      ↓
SUPPLY / DEMAND
      ↓
ENTRY / STOP / TARGETS
```

Think of it as:

```text
DIRECTION
    ↓
CONFIRMATION
    ↓
LOCATION
    ↓
RISK
```

---

# 6. Market Status

## STRONG CALL

Very strong bullish alignment.

Do **not** automatically enter just because the dashboard says `STRONG CALL`.

Check supply/demand and make sure AMD is not directly under supply.

## CALL

Bullish conditions are strong enough to qualify as a CALL setup.

You still need:

* a good entry location
* room to the next supply zone
* a logical stop
* acceptable reward versus risk

## CALL WATCH

The model is leaning bullish, but the full CALL setup is not ready.

Treat this as:

```text
WATCH — DO NOT ENTER YET
```

## STRONG PUT

Very strong bearish alignment.

Check that AMD is not sitting directly on demand before entering a PUT.

## PUT

Bearish conditions are aligned enough to qualify for a PUT setup.

## PUT WATCH

The model is leaning bearish, but the full setup is not ready.

## WAIT

Conditions are mixed or incomplete.

Doing nothing is a valid decision.

---

# 7. Confidence

The default AMD thresholds are:

| Confidence       | Meaning         |
| ---------------- | --------------- |
| **85%+**         | STRONG CALL     |
| **72%+**         | CALL            |
| **60–71.9%**     | CALL WATCH      |
| **40–60%**       | Neutral / mixed |
| **28–40%**       | PUT WATCH       |
| **28% or lower** | PUT             |
| **15% or lower** | STRONG PUT      |

Confidence measures **model alignment**, not guaranteed win probability.

An 85% confidence reading does **not** mean the trade has an 85% chance of winning.

---

# 8. AMD Trend Score

The Trend score is based on:

* EMA 9 vs EMA 21
* AMD price vs EMA 50
* EMA 50 direction
* AMD price vs VWAP

Interpretation:

| Trend Score | Meaning        |
| ----------: | -------------- |
| +70 to +100 | Strong bullish |
|  +20 to +69 | Bullish        |
|  -19 to +19 | Mixed          |
|  -20 to -69 | Bearish        |
| -70 to -100 | Strong bearish |

---

# 9. AMD Momentum Score

Momentum is based on:

* RSI
* MACD histogram
* recent price direction

Positive values favor CALLs.

Negative values favor PUTs.

For example:

```text
Trend       +85
Momentum    +75
```

is stronger bullish confirmation than:

```text
Trend       +85
Momentum    -40
```

because the second example shows bullish structure but weakening short-term momentum.

---

# 10. Institutional / Participation Score

This score uses:

* AMD position relative to VWAP
* DMI direction
* ADX trend strength
* relative volume
* candle direction

A strong positive score suggests bullish participation.

A strong negative score suggests bearish participation.

---

# 11. QQQ Confirmation

QQQ helps show whether the broader Nasdaq environment supports AMD.

For an AMD CALL, ideally:

```text
QQQ = BULLISH
```

For an AMD PUT:

```text
QQQ = BEARISH
```

QQQ disagreement does not mean AMD cannot move, but it lowers the quality of the setup.

---

# 12. SOXX Confirmation

SOXX is especially important because AMD is a semiconductor stock.

For CALLs:

```text
SOXX = BULLISH
```

For PUTs:

```text
SOXX = BEARISH
```

QQQ and SOXX are both required by default.

---

# 13. NVDA and SMH

NVDA and SMH provide additional semiconductor confirmation.

A strong AMD CALL is more convincing when:

```text
NVDA = BULLISH
SMH  = BULLISH
```

A strong AMD PUT is more convincing when:

```text
NVDA = BEARISH
SMH  = BEARISH
```

They are not individually required by default, but they contribute to the leadership score and confirmation count.

---

# 14. VWAP

For CALLs:

```text
VWAP = ABOVE
```

For PUTs:

```text
VWAP = BELOW
```

VWAP is required by default.

---

# 15. EMA Alignment

### BULLISH

The model expects:

```text
EMA 9 > EMA 21
AMD > EMA 9
AMD > EMA 50
```

### BEARISH

The model expects:

```text
EMA 9 < EMA 21
AMD < EMA 9
AMD < EMA 50
```

### MIXED

The moving averages are not aligned enough for a clean directional setup.

EMA alignment is required by default.

---

# 16. ADX

ADX measures **trend strength**, not bullish or bearish direction.

The default minimum is:

```text
ADX >= 18
```

Dashboard examples:

```text
ADX 24.5 OK
ADX 14.0 LOW
```

A low ADX can indicate choppy conditions.

ADX is required by default.

---

# 17. Relative Volume

Relative volume compares AMD's current volume with its recent average.

Examples:

```text
0.60x → Quiet
1.00x → Average
1.50x → Elevated
2.00x+ → Strong participation
```

Volume confirmation is optional by default, but it can help judge setup quality.

---

# 18. Supply Zones

A red box is a **SUPPLY ZONE**.

```text
                SUPPLY ZONE
       ┌──────────────────────┐
       │                      │
       │       SELLERS        │
       │                      │
       └──────────────────────┘
                 ↑
          POSSIBLE RESISTANCE

                 AMD
```

Supply is an area where selling pressure previously created a confirmed swing high.

It is **not** a guaranteed reversal point.

---

# 19. Demand Zones

A green box is a **DEMAND ZONE**.

```text
                 AMD

                  ↓
          POSSIBLE SUPPORT

       ┌──────────────────────┐
       │                      │
       │        BUYERS        │
       │                      │
       └──────────────────────┘
                DEMAND ZONE
```

Demand is an area where buying pressure previously created a confirmed swing low.

---

# 20. Zone Status

## AT SUPPLY

AMD is inside an active supply zone.

The script prevents a new CALL confirmation while AMD is inside supply.

Be cautious about chasing bullish moves there.

## AT DEMAND

AMD is inside an active demand zone.

The script prevents a new PUT confirmation while AMD is inside demand.

## BETWEEN ZONES

AMD is not currently inside tracked supply or demand.

Check how much room remains before the next opposing zone.

---

# 21. Good AMD CALL Setup

A high-quality CALL candidate looks like:

```text
AMD OPTIONS V1
─────────────────────────────

MARKET STATUS     CALL
                  or
                  STRONG CALL

CONFIDENCE        72%+

AMD Trend         BULLISH
AMD Momentum      BULLISH
Institutional     BULLISH

QQQ               BULLISH
SOXX              BULLISH
NVDA              BULLISH
SMH               BULLISH

VWAP              ABOVE
EMA               BULLISH
ADX               OK
Volume            Healthy

Zone              AT DEMAND
                  or
                  BETWEEN ZONES

Nearest Supply    Enough room above
```

A strong location is often a bullish confirmation after AMD holds or rejects demand.

---

# 22. Good AMD PUT Setup

```text
AMD OPTIONS V1
─────────────────────────────

MARKET STATUS     PUT
                  or
                  STRONG PUT

CONFIDENCE        28% or lower

AMD Trend         BEARISH
AMD Momentum      BEARISH
Institutional     BEARISH

QQQ               BEARISH
SOXX              BEARISH
NVDA              BEARISH
SMH               BEARISH

VWAP              BELOW
EMA               BEARISH
ADX               OK

Zone              AT SUPPLY
                  or
                  BETWEEN ZONES

Nearest Demand    Enough room below
```

A strong location is often a bearish rejection from supply.

---

# 23. When NOT to Buy an AMD CALL

Avoid or reconsider a CALL when:

* AMD is inside supply
* supply is extremely close above
* QQQ is bearish
* SOXX is bearish
* AMD is below VWAP
* EMA is bearish or mixed
* ADX is low
* confidence is only CALL WATCH
* the candle has not closed
* AMD is already extended after a large move
* reward does not justify risk

For example:

```text
STRONG CALL

Confidence       89%
AMD              $182.00
Nearest Supply   $182.12

Distance         $0.12
```

Even though the model is strongly bullish, AMD has only $0.12 before reaching supply.

The **direction may be good while the entry location is poor**.

---

# 24. When NOT to Buy an AMD PUT

Avoid or reconsider a PUT when:

* AMD is inside demand
* demand is extremely close below
* QQQ is bullish
* SOXX is bullish
* AMD is above VWAP
* EMA is bullish or mixed
* ADX is low
* confidence is only PUT WATCH
* the move is already heavily extended

For example:

```text
STRONG PUT

Confidence       12%
AMD              $178.50
Nearest Demand   $178.38

Distance         $0.12
```

There may be too little downside room for a fresh PUT entry.

---

# 25. Entry

The dashboard `Entry` value is AMD's current reference price.

It is **not the option premium**.

For example:

```text
Entry = $181.25
```

means the underlying AMD reference entry is approximately $181.25.

---

# 26. Stop

The stop is ATR-based.

For a bullish setup:

```text
Stop =
Entry - (ATR × Stop Multiplier)
```

For a bearish setup:

```text
Stop =
Entry + (ATR × Stop Multiplier)
```

The stop is based on **AMD's stock price**, not the option contract price.

---

# 27. Targets

The default targets are:

```text
Target 1 = 1.5 ATR
Target 2 = 2.5 ATR
```

For CALLs, the targets are above entry.

For PUTs, the targets are below entry.

---

# 28. R / R

`R / R` means reward-to-risk ratio.

For example:

```text
R / R = 2.50 : 1
```

This means Target 2 is approximately 2.5 times farther from entry than the stop.

It does **not** guarantee profitability.

---

# 29. Closed-Candle Rule

Signals are confirmed on closed candles.

Since this indicator is designed around the **5-minute chart**, wait for the 5-minute candle to finish before treating a CALL or PUT as confirmed.

For example:

```text
10:30 candle begins
       ↓
signal appears temporarily
       ↓
DO NOT ENTER YET
       ↓
10:35 candle closes
       ↓
signal remains confirmed
       ↓
evaluate the trade
```

This helps prevent acting on temporary intrabar conditions.

---

# 30. Latest Signal Label

The indicator keeps only the latest signal label.

For example:

```text
        PUT
         ↓
     ┌───────┐
     │  PUT  │
     └───────┘
```

When a new qualifying CALL or PUT occurs, the previous signal label is deleted.

This keeps the chart clean.

---

# 31. AMD CALL Checklist

Before considering a CALL:

```text
□ AMD is on the 5-minute chart

□ Candle has closed

□ Status is CALL
  or STRONG CALL

□ Confidence >= 72%

□ AMD Trend is bullish

□ AMD Momentum is bullish

□ QQQ is bullish

□ SOXX is bullish

□ NVDA / SMH are supportive

□ VWAP says ABOVE

□ EMA says BULLISH

□ ADX says OK

□ AMD is NOT inside supply

□ There is reasonable room
  to nearest supply

□ Stop is known before entry

□ Position size is acceptable

□ Reward justifies the risk
```

The more boxes that align, the cleaner the setup.

---

# 32. AMD PUT Checklist

Before considering a PUT:

```text
□ AMD is on the 5-minute chart

□ Candle has closed

□ Status is PUT
  or STRONG PUT

□ Confidence <= 28%

□ AMD Trend is bearish

□ AMD Momentum is bearish

□ QQQ is bearish

□ SOXX is bearish

□ NVDA / SMH are supportive

□ VWAP says BELOW

□ EMA says BEARISH

□ ADX says OK

□ AMD is NOT inside demand

□ There is reasonable room
  to nearest demand

□ Stop is known before entry

□ Position size is acceptable

□ Reward justifies the risk
```

---

# 33. WATCH Means Wait

A WATCH condition is **not a completed setup**.

`CALL WATCH` means bullish conditions are developing.

`PUT WATCH` means bearish conditions are developing.

Use this sequence:

```text
CALL WATCH
     ↓
Wait
     ↓
AMD continues strengthening
     ↓
QQQ / SOXX confirm
     ↓
EMA + VWAP confirm
     ↓
ADX becomes acceptable
     ↓
CALL
     ↓
Check supply
     ↓
Evaluate entry
```

The bearish process is the reverse.

---

# 34. Options Contract Selection

The indicator analyzes **AMD stock**, not the option contract itself.

When selecting an AMD option, separately consider:

* expiration
* strike
* delta
* bid/ask spread
* liquidity
* implied volatility
* time decay
* contract price

A strong AMD directional setup can still produce a poor options trade if the contract is badly selected.

---

# 35. Position Sizing

Before entering, define:

```text
Maximum acceptable loss
per trade
```

Then size the position accordingly.

Do not increase your position simply because the dashboard says:

```text
STRONG CALL
```

or:

```text
STRONG PUT
```

Strong setups can still fail.

---

# 36. Alerts

The indicator provides these TradingView alert conditions:

```text
AMD CALL

AMD PUT

AMD ENTERED SUPPLY

AMD ENTERED DEMAND
```

When appropriate, configure the TradingView alert for:

```text
Once Per Bar Close
```

That keeps the alert behavior consistent with the indicator's closed-candle logic.

---

# 37. Track Your Results

Before deciding that the indicator works well, paper-trade and record the results.

Track:

```text
Date

Time

CALL / PUT

Confidence

AMD Trend

AMD Momentum

QQQ

SOXX

NVDA

SMH

VWAP

EMA

ADX

Relative Volume

Entry

Stop

Target 1

Target 2

Nearest Supply

Nearest Demand

Result

Maximum favorable move

Maximum adverse move
```

Do not judge the strategy from only a handful of trades.

A larger sample gives you much better information.

---

# 38. Measure Expectancy

Do not judge the system only by win rate.

Use:

```text
Expectancy =

(Win Rate × Average Win)

        -

(Loss Rate × Average Loss)
```

For example, a system could have:

```text
Win Rate       55%
Average Win    $200

Loss Rate      45%
Average Loss   $100
```

Then:

```text
(0.55 × $200)
-
(0.45 × $100)

= $110 - $45

= +$65 expectancy
```

The purpose of tracking this is to determine whether the strategy has demonstrated an edge over a meaningful sample.

---

# 39. Quick Reference

## AMD CALL

```text
STATUS
CALL / STRONG CALL

CONFIDENCE
72%+

AMD TREND
BULLISH

MOMENTUM
BULLISH

QQQ
BULLISH

SOXX
BULLISH

VWAP
ABOVE

EMA
BULLISH

ADX
OK

LOCATION
NOT AT SUPPLY

TARGET
Toward next supply
```

## AMD PUT

```text
STATUS
PUT / STRONG PUT

CONFIDENCE
28% or lower

AMD TREND
BEARISH

MOMENTUM
BEARISH

QQQ
BEARISH

SOXX
BEARISH

VWAP
BELOW

EMA
BEARISH

ADX
OK

LOCATION
NOT AT DEMAND

TARGET
Toward next demand
```

## SKIP

```text
CALL WATCH

PUT WATCH

WAIT

ADX LOW

EMA MIXED

QQQ / SOXX disagreement

CALL directly into supply

PUT directly into demand

Poor reward/risk

Unconfirmed candle
```

---

# 40. Core Principle

The AMD model answers:

```text
WHAT IS AMD DOING?
```

QQQ / SOXX / NVDA / SMH answer:

```text
IS THE MARKET
CONFIRMING AMD?
```

Supply and demand answer:

```text
IS THIS A GOOD
LOCATION?
```

Risk management answers:

```text
HOW MUCH CAN I
AFFORD TO BE WRONG?
```

So the complete process is:

```text
       AMD DIRECTION
             +
   MARKET CONFIRMATION
             +
 SUPPLY / DEMAND LOCATION
             +
       RISK CONTROL
             ↓
─────────────────────────
 A TRADE WORTH EVALUATING
─────────────────────────
```

The most important thing is **not to treat CALL/PUT or the confidence percentage as a guarantee**. The dashboard should help you filter and organize information; your results need to be validated through paper trading/backtesting and disciplined risk management.

---

# Risk Disclosure

Options involve significant risk and are not suitable for all investors. Options can amplify both gains and losses, and long options can lose value as expiration approaches.

Before trading exchange-listed options, review the Options Clearing Corporation's **Characteristics and Risks of Standardized Options** and your broker's options disclosures.

This indicator and README are provided for educational and research purposes only. They do not constitute personalized investment advice, a recommendation to buy or sell any security, or a guarantee of trading results.
