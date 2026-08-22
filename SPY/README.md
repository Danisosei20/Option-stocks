Absolutely — here is the full README content so you can copy and paste it directly into your project as `README.md`.

````markdown
# SPY Options V1 - Clean Supply/Demand Guide

> **Purpose:** This README explains how to read and use the `SPY Options V1 - Clean` TradingView indicator.
>
> **Important:** This is a decision-support indicator, not a guarantee of profit. SPY options can lose value very quickly. Paper-trade and backtest the rules before risking meaningful capital.

---

# 1. What This Indicator Is For

`SPY Options V1 - Clean` is designed primarily for trading **SPY options on the 5-minute chart**.

Instead of looking only at SPY price, it combines SPY's own technical structure with confirmation from the broader U.S. market.

The indicator analyzes:

- SPY EMA 9 / 21 / 50
- SPY VWAP
- RSI
- MACD
- ADX / directional movement
- Relative volume
- Supply and demand zones
- QQQ
- DIA
- IWM
- VIX Effect
- XLK
- XLF
- XLY
- CALL / PUT / WAIT status
- Confidence
- Reference entry, stop, Target 1, and Target 2

The goal is to answer four questions:

1. **What direction is SPY moving?**
2. **Is the broader market confirming that direction?**
3. **Is SPY at a good location for an entry?**
4. **Is there enough room to the next supply or demand zone?**

---

# 2. Recommended Setup

Use:

```text
Symbol:      SPY
Timeframe:   5 minutes
Candles:     Standard candles
Indicator:   SPY Options V1 - Clean
````

The script can display:

* EMA 9
* EMA 21
* EMA 50
* VWAP
* Supply zones
* Demand zones
* Latest CALL / PUT signal
* Dashboard

For a clean chart, remove duplicate EMA, VWAP, MACD, or supply/demand indicators unless you specifically want them for comparison.

---

# 3. How the SPY Model Is Weighted

SPY itself controls most of the final score.

```text
SPY Trend             35%
SPY Momentum          20%
SPY Institutional     20%
External Leadership   25%
```

Therefore:

```text
SPY itself            75%
External confirmation 25%
```

The external symbols confirm the SPY setup. They are not intended to replace SPY's own price action.

---

# 4. External Confirmation Weights

The external leadership model uses:

```text
QQQ         22%
DIA         16%
IWM         16%
VIX Effect  18%
XLK         12%
XLF          8%
XLY          8%
```

## Why these symbols?

### QQQ

QQQ helps confirm technology and growth-stock participation.

If SPY is bullish and QQQ is also bullish, the market has stronger participation from technology and growth names.

### DIA

DIA represents major Dow stocks.

It helps determine whether large-cap industrial and value stocks agree with SPY's direction.

### IWM

IWM represents smaller U.S. companies.

It helps measure market breadth.

A move where SPY, QQQ, DIA, and IWM all agree can be stronger than a move driven by only a small number of mega-cap companies.

### VIX Effect

VIX measures expected market volatility.

The script intentionally reverses the raw VIX directional score when calculating its effect on SPY.

Generally:

```text
Falling / weak VIX
        ↓
More supportive of SPY
        ↓
Bullish VIX Effect
```

and:

```text
Rising / strong VIX
        ↓
More pressure on SPY
        ↓
Bearish VIX Effect
```

### XLK

Technology sector confirmation.

### XLF

Financial sector confirmation.

### XLY

Consumer discretionary sector confirmation.

---

# 5. Read the Dashboard in This Order

Do not make a trade decision from one row.

Read the dashboard from top to bottom:

```text
MARKET STATUS
      ↓
CONFIDENCE
      ↓
TREND
      ↓
MOMENTUM + MACD + RSI
      ↓
MARKET CONFIRMATIONS
      ↓
VWAP + EMA
      ↓
ADX + VOLUME
      ↓
SUPPLY / DEMAND
      ↓
ENTRY + STOP + TARGETS
```

A simple way to remember this is:

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

The dashboard can display:

```text
STRONG CALL
CALL
CALL WATCH
WAIT
PUT WATCH
PUT
STRONG PUT
```

## STRONG CALL

The bullish conditions are highly aligned.

This does **not** mean automatically buy a call.

Before entering, make sure:

* SPY is not inside supply.
* SPY is not immediately below major supply.
* SPY is behaving bullishly around VWAP and EMAs.
* External confirmations still support the move.
* There is sufficient upside available.
* Your stop makes sense.

---

## CALL

The script's bullish requirements are satisfied.

This tells you:

> The environment currently favors CALLs.

You should still look for a good entry rather than chasing an extended candle.

---

## CALL WATCH

The model is leaning bullish, but all CALL requirements have not been satisfied.

Think:

```text
WATCH FOR CALL
NOT CALL ENTRY YET
```

---

## WAIT

The conditions are mixed or incomplete.

This is important.

You do **not** need to trade every SPY movement.

Sometimes the correct decision is:

```text
NO TRADE
```

---

## PUT WATCH

The model is leaning bearish but does not yet have full bearish confirmation.

Think:

```text
WATCH FOR PUT
NOT PUT ENTRY YET
```

---

## PUT

The bearish requirements are satisfied.

The environment favors PUTs.

Before entering, make sure SPY has room to move lower before reaching demand.

---

## STRONG PUT

The bearish conditions are highly aligned.

Again, this does not mean automatically buy a PUT.

Do not chase a PUT directly into demand.

---

# 7. Confidence

The default thresholds are:

|   Confidence | Interpretation        |
| -----------: | --------------------- |
|         85%+ | STRONG CALL territory |
|         72%+ | CALL territory        |
|         60%+ | CALL WATCH territory  |
|       40-60% | Mixed / Neutral       |
| 40% or lower | PUT WATCH territory   |
| 28% or lower | PUT territory         |
| 15% or lower | STRONG PUT territory  |

## Important

Confidence is **not the probability that your trade will win**.

For example:

```text
Confidence = 88%
```

does NOT mean:

```text
88% probability of making money.
```

It means:

> The indicators used by the model are strongly aligned in the bullish direction.

---

# 8. Trend

The SPY Trend score uses:

* EMA 9 vs EMA 21
* Price vs EMA 50
* EMA 50 direction
* Price vs VWAP

General interpretation:

| Trend Score | Meaning        |
| ----------: | -------------- |
| +70 to +100 | Strong Bullish |
|  +20 to +69 | Bullish        |
|  -19 to +19 | Mixed          |
|  -20 to -69 | Bearish        |
| -70 to -100 | Strong Bearish |

For CALLs, you generally want a positive Trend score.

For PUTs, you generally want a negative Trend score.

---

# 9. Momentum

Momentum uses:

* RSI
* MACD
* Current price direction

Example of strong bullish agreement:

```text
Trend       +85
Momentum    +80
MACD        BULLISH
RSI         62
```

That is much stronger than:

```text
Trend       +85
Momentum    -40
MACD        BEARISH
RSI         44
```

In the second example, SPY may still technically be in an uptrend, but short-term momentum is weakening.

---

# 10. MACD

Yes, the SPY indicator includes MACD.

The settings are:

```text
Fast EMA      12
Slow EMA      26
Signal EMA     9
```

The dashboard simplifies MACD into:

```text
BULLISH
BEARISH
MIXED
```

For CALLs, a strong combination is:

```text
Trend      BULLISH
MACD       BULLISH
RSI        > 55
VWAP       ABOVE
EMA        BULLISH
```

For PUTs:

```text
Trend      BEARISH
MACD       BEARISH
RSI        < 45
VWAP       BELOW
EMA        BEARISH
```

Do not use MACD alone as an entry signal.

---

# 11. RSI

The default RSI length is:

```text
14
```

A simple interpretation is:

```text
RSI > 55       Bullish confirmation

RSI 45-55      Mixed / neutral

RSI < 45       Bearish confirmation
```

Do not automatically assume that high RSI means SPY must fall.

Do not automatically assume that low RSI means SPY must rise.

Strong trends can remain overbought or oversold longer than expected.

---

# 12. VWAP

VWAP is especially important for intraday SPY trading.

## CALL Preference

You generally want:

```text
Price > VWAP
```

This suggests buyers have greater intraday control.

## PUT Preference

You generally want:

```text
Price < VWAP
```

This suggests sellers have greater intraday control.

## Be Careful When

SPY repeatedly moves:

```text
Above VWAP
Below VWAP
Above VWAP
Below VWAP
```

That often means the market is choppy.

Choppy markets can produce poor options entries.

---

# 13. EMA 9 / 21 / 50

The indicator uses:

```text
EMA 9
EMA 21
EMA 50
```

## Bullish Structure

Prefer:

```text
Price > EMA 9

EMA 9 > EMA 21

Price > EMA 50
```

Visually:

```text
PRICE
  ↑
EMA 9
  ↑
EMA 21
  ↑
EMA 50
```

## Bearish Structure

Prefer:

```text
Price < EMA 9

EMA 9 < EMA 21

Price < EMA 50
```

---

# 14. ADX

ADX measures **trend strength**, not direction.

The default minimum is:

```text
ADX >= 18
```

When the dashboard says:

```text
ADX 24 OK
```

the trend-strength requirement has been satisfied.

When ADX is weak, SPY may be moving sideways even if some directional indicators appear bullish or bearish.

---

# 15. Relative Volume

The indicator compares current volume with the recent 20-bar average.

Examples:

```text
0.60x
```

means volume is below the recent average.

```text
1.00x
```

means approximately average.

```text
1.50x
```

means stronger participation.

```text
2.00x
```

means very strong relative participation.

The default script displays relative volume but does not require it for every CALL/PUT signal unless:

```text
Require Relative Volume = ON
```

---

# 16. Supply and Demand

Supply and demand are very important parts of the system.

## Supply Zone

The **red zone** represents an area where selling pressure previously appeared.

Think:

```text
SUPPLY
=
POSSIBLE RESISTANCE
=
SELLING AREA
```

Avoid blindly buying CALLs directly into supply.

---

## Demand Zone

The **green zone** represents an area where buying pressure previously appeared.

Think:

```text
DEMAND
=
POSSIBLE SUPPORT
=
BUYING AREA
```

Avoid blindly buying PUTs directly into demand.

---

# 17. How the Zones Work

The script automatically finds pivot highs and lows.

A significant pivot high can create:

```text
SUPPLY ZONE
```

A significant pivot low can create:

```text
DEMAND ZONE
```

The zones extend to the right so you can see where SPY may react later.

The script keeps the chart clean by limiting the number of zones.

A supply zone is removed after SPY confirms a close above the top of that zone.

A demand zone is removed after SPY confirms a close below the bottom of that zone.

---

# 18. Why Supply/Demand Matters for Options

Suppose the dashboard says:

```text
CALL

Confidence     78%
Trend          Bullish
Momentum       Bullish
MACD           Bullish
VWAP           Above
```

That sounds good.

But imagine SPY is here:

```text
====================
    SUPPLY ZONE
====================

       SPY ↑
```

You are buying directly into resistance.

Your upside may be limited.

Instead, you may want to see:

```text
SPY approaches supply
        ↓
breaks supply
        ↓
closes above supply
        ↓
holds/retests
        ↓
bullish confirmation remains
        ↓
CALL setup
```

The opposite concept applies to PUTs and demand.

---

# 19. External Confirmation

The script analyzes:

```text
QQQ
DIA
IWM
VIX Effect
XLK
XLF
XLY
```

The default signal engine requires at least:

```text
4 external confirmations
```

---

# 20. Strong CALL Environment

For a high-quality bullish environment, you might see:

```text
SPY          BULLISH
QQQ          BULLISH
DIA          BULLISH
IWM          BULLISH
VIX EFFECT   BULLISH
XLK          BULLISH
```

Not every symbol has to agree perfectly.

But broad agreement is generally stronger than SPY moving alone.

---

# 21. Strong PUT Environment

For bearish conditions:

```text
SPY          BEARISH
QQQ          BEARISH
DIA          BEARISH
IWM          BEARISH
VIX EFFECT   BEARISH
XLK          BEARISH
```

This tells you weakness is broader than just SPY.

---

# 22. What VIX EFFECT Means

This row can initially be confusing.

The dashboard shows the VIX's **effect on SPY**, rather than simply telling you whether the VIX itself is bullish.

Therefore:

```text
VIX EFFECT = BULLISH
```

means:

> Volatility behavior is supportive of the bullish SPY case.

And:

```text
VIX EFFECT = BEARISH
```

means:

> Volatility behavior supports the bearish SPY case.

So you do not have to mentally reverse VIX every time you read the dashboard.

---

# 23. CALL Checklist

Before considering a CALL:

```text
[ ] Market Status = CALL or STRONG CALL

[ ] Confidence >= 72%

[ ] Trend is bullish

[ ] Momentum is bullish

[ ] MACD is bullish

[ ] RSI preferably > 55

[ ] SPY is above VWAP

[ ] EMA structure is bullish

[ ] ADX is strong enough

[ ] QQQ confirms

[ ] VIX Effect confirms

[ ] At least 4 external markets confirm

[ ] SPY is NOT inside supply

[ ] There is room before the next supply zone

[ ] Entry and stop make sense

[ ] Reward is worth the risk
```

You are looking for **agreement**, not perfection.

---

# 24. PUT Checklist

Before considering a PUT:

```text
[ ] Market Status = PUT or STRONG PUT

[ ] Confidence <= 28%

[ ] Trend is bearish

[ ] Momentum is bearish

[ ] MACD is bearish

[ ] RSI preferably < 45

[ ] SPY is below VWAP

[ ] EMA structure is bearish

[ ] ADX is strong enough

[ ] QQQ confirms bearish direction

[ ] VIX Effect confirms bearish direction

[ ] At least 4 external markets confirm

[ ] SPY is NOT inside demand

[ ] There is room before the next demand zone

[ ] Entry and stop make sense

[ ] Reward is worth the risk
```

---

# 25. Example CALL Setup

Imagine your dashboard reads:

```text
SPY OPTIONS V1

MARKET STATUS      CALL
CONFIDENCE         79%

Trend              +85
Momentum           +75
MACD               BULLISH
RSI                61
Leadership         +70
Institutional      +75

CONFIRMATIONS

QQQ                BULLISH
DIA                BULLISH
IWM                BULLISH
VIX EFFECT         BULLISH
XLK                BULLISH

TECHNICALS

VWAP               ABOVE
EMA                BULLISH
ADX                24 OK
Volume             1.20x

SUPPLY / DEMAND

Status             BETWEEN ZONES
```

This represents a strong bullish environment.

You would then check:

```text
Where is the nearest supply?

Is the current candle extended?

Where does the setup become invalid?

Is there enough reward before resistance?

Which option contract gives me reasonable exposure?
```

---

# 26. Example PUT Setup

Imagine:

```text
SPY OPTIONS V1

MARKET STATUS      PUT
CONFIDENCE         21%

Trend              -90
Momentum           -80
MACD               BEARISH
RSI                39
Leadership         -75
Institutional      -80

CONFIRMATIONS

QQQ                BEARISH
DIA                BEARISH
IWM                BEARISH
VIX EFFECT         BEARISH
XLK                BEARISH

TECHNICALS

VWAP               BELOW
EMA                BEARISH
ADX                27 OK
Volume             1.35x

SUPPLY / DEMAND

Status             BETWEEN ZONES
```

That represents broad bearish agreement.

Before buying the PUT, check where the nearest demand zone is located.

---

# 27. Entry, Stop and Targets

The script calculates reference levels using ATR.

Defaults:

```text
Stop       1.0 ATR

Target 1   1.5 ATR

Target 2   2.5 ATR
```

These are based on the **SPY underlying price**.

They are NOT option-premium prices.

For example:

```text
SPY Entry = $650.00

SPY Stop = $648.80

Target 1 = $651.80

Target 2 = $653.00
```

Those levels refer to SPY.

They do not mean:

```text
Sell my option when the option reaches $648.80.
```

You are monitoring SPY's underlying price.

---

# 28. Reward / Risk

With the default settings:

```text
Risk       1.0 ATR

Target 2   2.5 ATR
```

the reference reward/risk is approximately:

```text
2.5 : 1
```

But remember:

The option contract will not move exactly the same percentage as SPY.

Its value is affected by:

* Delta
* Gamma
* Theta
* Implied volatility
* Strike
* Expiration
* Bid/ask spread
* Time required for SPY to reach the target

Therefore, the dashboard's reward/risk is a **SPY price framework**, not a guaranteed option return.

---

# 29. Choosing an Option Contract

The indicator analyzes SPY.

It does not directly analyze the option contract.

For directional intraday trades, a simple starting framework is to consider contracts that are:

```text
Liquid

Near the money

Have tight bid/ask spreads

Respond reasonably to SPY movement
```

Do not select an option simply because it is cheap.

A very cheap, far-out-of-the-money contract may require a much larger SPY move and can lose value quickly from time decay.

---

# 30. Simple Trading Workflow

Here is the complete workflow.

## Step 1 — Open SPY

Use:

```text
SPY
5-minute chart
```

---

## Step 2 — Check Market Status

Ask:

```text
CALL?

PUT?

WATCH?

WAIT?
```

---

## Step 3 — Check Confidence

For CALL:

```text
Prefer >= 72%
```

For PUT:

```text
Prefer <= 28%
```

---

## Step 4 — Check Trend

For CALL:

```text
Trend positive
```

For PUT:

```text
Trend negative
```

---

## Step 5 — Check Momentum

Confirm:

```text
Momentum
MACD
RSI
```

They should generally agree with your direction.

---

## Step 6 — Check Market Confirmation

Review:

```text
QQQ
DIA
IWM
VIX EFFECT
XLK
```

Broad agreement makes the setup stronger.

---

## Step 7 — Check VWAP

CALL:

```text
SPY above VWAP
```

PUT:

```text
SPY below VWAP
```

---

## Step 8 — Check EMA

CALL:

```text
Bullish EMA structure
```

PUT:

```text
Bearish EMA structure
```

---

## Step 9 — Check ADX

Prefer:

```text
ADX >= 18
```

---

## Step 10 — Check Supply/Demand

For CALL:

```text
Where is supply?
```

For PUT:

```text
Where is demand?
```

Do not blindly trade directly into the opposing zone.

---

## Step 11 — Check Risk

Before entering, know:

```text
ENTRY
STOP
TARGET 1
TARGET 2
```

---

## Step 12 — Select the Option

Choose a liquid SPY contract appropriate for the setup.

---

## Step 13 — Manage the Trade

Do not assume that because the dashboard said CALL or PUT, the trade must work.

Every setup can fail.

---

# 31. Situations to Avoid

Be careful when SPY repeatedly crosses VWAP.

Example:

```text
Above
Below
Above
Below
Above
Below
```

This is often chop.

---

Avoid trading when EMA 9 and EMA 21 are flat and tangled.

Example:

```text
EMA9  ~~~~~~~
EMA21 ~~~~~~~
```

That usually indicates weak direction.

---

Be cautious when:

```text
Trend = Bullish
Momentum = Bearish
```

or:

```text
Trend = Bearish
Momentum = Bullish
```

The market is giving conflicting information.

---

Avoid:

```text
CALL directly into SUPPLY
```

and:

```text
PUT directly into DEMAND
```

---

Also be careful when:

* Price is extremely extended from VWAP.
* Price is extremely extended from EMA 9.
* You missed the original move.
* You are chasing a large candle.
* Option bid/ask spreads are poor.
* Major scheduled news is approaching.
* Volatility suddenly changes.

---

# 32. What the Indicator Does NOT Know

The current script does not directly analyze:

* Option-chain open interest
* Option-chain volume
* Gamma exposure
* Dealer positioning
* Put/call flow
* Dark-pool activity
* Economic-calendar events
* Breaking news
* Exact Greeks for your selected contract
* Your account size
* Your personal risk tolerance

Therefore, do not interpret the dashboard as a complete options-trading system by itself.

---

# 33. Alerts

The script includes alerts for:

```text
SPY CALL

SPY PUT

SPY ENTERED SUPPLY

SPY ENTERED DEMAND
```

CALL and PUT signals use confirmed bars.

That means the signal waits for the candle to close instead of relying entirely on an unfinished candle.

In TradingView:

```text
Create Alert
      ↓
Choose SPY Options V1
      ↓
Select desired condition
```

---

# 34. Recommended Default Settings

For the first version, I recommend starting with:

```text
Chart              SPY 5-minute

CALL               >= 72%
STRONG CALL        >= 85%

PUT                <= 28%
STRONG PUT         <= 15%

Minimum confirms   4

Minimum ADX        18

Volume requirement OFF

Signal cooldown    6 bars

Stop               1.0 ATR

Target 1           1.5 ATR

Target 2           2.5 ATR
```

Do not immediately change the settings after one losing trade.

Collect data first.

Otherwise, you can easily overfit the indicator.

---

# 35. Backtesting Before Live Trading

This is extremely important.

Before relying on the system with real money, record a meaningful number of trades/signals.

Track:

```text
Date

Time

CALL / PUT

Confidence

Trend

Momentum

MACD

RSI

VWAP

EMA

ADX

Relative Volume

QQQ

DIA

IWM

VIX Effect

XLK

Supply/Demand location

Entry

Stop

Target 1 reached?

Target 2 reached?

Maximum favorable movement

Maximum adverse movement

Result

Notes
```

Then analyze the results.

---

# 36. Questions Your Backtest Should Answer

You want to discover things such as:

```text
Do CALLs perform better than PUTs?

Does the system work better in the morning?

Does performance decline around lunchtime?

Do 85%+ signals actually outperform 72% signals?

Does ADX > 25 improve results?

Are trades better when volume > 1.0x?

How often does Target 1 hit?

How often does Target 2 hit?

How often does the stop hit first?

How do trades perform near supply/demand?

How does VIX behavior affect results?
```

Those answers should eventually determine whether you change the default settings.

---

# 37. Quick CALL Reference

```text
SPY CALL CHECKLIST

MARKET STATUS
CALL / STRONG CALL

CONFIDENCE
>= 72%

TREND
Bullish

MOMENTUM
Bullish

MACD
Bullish

RSI
Preferably > 55

QQQ
Bullish

VIX EFFECT
Bullish

VWAP
Above

EMA
Bullish

ADX
OK

SUPPLY
Not directly inside supply

RISK
Defined before entry
```

---

# 38. Quick PUT Reference

```text
SPY PUT CHECKLIST

MARKET STATUS
PUT / STRONG PUT

CONFIDENCE
<= 28%

TREND
Bearish

MOMENTUM
Bearish

MACD
Bearish

RSI
Preferably < 45

QQQ
Bearish

VIX EFFECT
Bearish

VWAP
Below

EMA
Bearish

ADX
OK

DEMAND
Not directly inside demand

RISK
Defined before entry
```

---

# 39. When to WAIT

WAIT when you see:

```text
Mixed confirmations

Weak ADX

SPY chopping around VWAP

EMA 9 / EMA 21 tangled

Trend/Momentum disagreement

CALL directly under supply

PUT directly above demand

Poor reward-to-risk

Late/chased entry
```

Remember:

```text
WAIT
```

does not mean the indicator failed.

It means the system does not currently see enough alignment for its CALL or PUT requirements.

---

# 40. The Core SPY Trading Concept

The system is designed around:

```text
SPY DIRECTION
      +
SPY MOMENTUM
      +
MARKET CONFIRMATION
      +
VWAP / EMA STRUCTURE
      +
SUPPLY / DEMAND LOCATION
      +
RISK MANAGEMENT
```

When those components agree, you have a stronger setup.

When they conflict, you wait.

---

# 41. Simplest Way to Remember Everything

You do not need to memorize the entire indicator.

Remember these four words:

## DIRECTION

What direction is SPY moving?

```text
Trend
EMA
VWAP
```

## CONFIRMATION

Does everything else agree?

```text
Momentum
MACD
RSI
QQQ
DIA
IWM
VIX Effect
Sectors
```

## LOCATION

Where are you entering?

```text
Supply
Demand
VWAP
EMA
```

## RISK

What happens if you are wrong?

```text
Entry
Stop
Target 1
Target 2
Reward / Risk
```

Therefore:

# DIRECTION → CONFIRMATION → LOCATION → RISK

---

# Disclaimer

This indicator and README are for educational and research purposes only and are not financial advice.

No indicator can guarantee profitable trades.

Options involve substantial risk, including the possibility of losing the entire premium paid.

Backtest and paper-trade the indicator before using real capital.

```
```
