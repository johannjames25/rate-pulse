# Rate Drift — One Pager

**Option picked: Option 1 — API Tool + Chat/Form**

## What this is
Rate Drift is a small web tool that answers one question in plain English: "how has this currency pair actually moved?" A person types an amount and picks two currencies, and the tool converts the amount at today's rate, compares it to the rate from a chosen point in the past, and states clearly whether the currency has strengthened, weakened, or stayed flat, with the number to back it up. For pairs the European Central Bank doesn't quote directly (anything not involving EUR), it also shows the actual euro-based cross-rate math behind the number, instead of just presenting a figure and asking you to trust it.

## The problem it addresses
Currency data is easy to find but hard to interpret and easy to mis-trust. A raw exchange-rate number (e.g. "1 USD = 83.12 INR") doesn't tell a non-expert whether that's good, bad, or different from last month — and most tools that show a number for a pair like USD/INR don't mention that no central bank actually publishes that number directly; it's a derived cross-rate. Rate Drift states the movement in a plain sentence and, for derived pairs, shows the actual arithmetic that produced the figure.

## Who would care, and why
- Someone planning to send money abroad or receive foreign payments, deciding whether to act now or wait.
- A small business owner pricing goods in a foreign currency.
- A student or early-career analyst who wants a quick, sourced reference for "is currency X trending up or down" without opening a Bloomberg terminal.

## One thing I'd build next with another week
Add a small historical chart (last 90 days, daily) beneath the headline result, so the trend is visible at a glance instead of only stated as a single percentage — and let the user save/share a specific query as a link.
