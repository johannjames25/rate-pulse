# Citation Ledger — RatePulse

One row per factual claim the tool or its documentation makes. All links were opened and checked on 2026-07-08.

| # | Claim | Source | Source type | One-line paraphrase |
|---|---|---|---|---|
| 1 | The tool's "today's rate" and "past rate" calls hit `api.frankfurter.dev/v1/latest?base=..&symbols=..` and `api.frankfurter.dev/v1/{date}?base=..&symbols=..` | https://frankfurter.dev/v1/ | API doc | This is the exact, documented request shape for fetching a live rate and a historical rate for a specific currency pair — I matched my code to it, not the other way round. |
| 2 | The rates behind the v1 endpoint originate from the European Central Bank, not from Frankfurter itself | https://frankfurter.dev/v1/ | API doc | Frankfurter's own v1 documentation states plainly that this version serves ECB currency data; the project is a free redistribution layer, not a primary source. |
| 3 | ECB reference rates are published once daily, around 16:00 CET, only on days the TARGET payment system is open (no weekends, no major EU holidays) | https://www.ecb.europa.eu/stats/policy_and_exchange_rates/euro_reference_exchange_rates/html/index.en.html | official data source (central bank) | The ECB itself states the rates update roughly once a day, on business days only — which is why a "30 days ago" query can't return a Saturday's rate and why the tool always shows the actual date it used. |
| 4 | Every ECB reference rate is quoted against the euro as the base currency — a pair like USD→INR is not published directly, it's a derived cross-rate | https://www.ecb.europa.eu/stats/policy_and_exchange_rates/euro_reference_exchange_rates/html/index.en.html | official data source (central bank) | The ECB's own rate table lists every currency's value in euros; anything not involving EUR (like USD to INR) has to be computed by dividing one euro rate by another, which is what the API — and by extension this tool — is doing behind the scenes. |
| 5 | Frankfurter requires no API key and has no request quota, only abuse-prevention rate limiting | https://frankfurter.dev/ | API doc | The project's own FAQ confirms it's free with no registration and no hard call limits, which is why this tool can run entirely client-side with nothing to hide or leak. |

**Note on paraphrasing:** every description above is written in my own words after reading the linked pages directly; nothing is copied from the source text.

**Why this matters for what the tool shows:** because of claim #4, the number the tool displays for a pair like USD→INR is a triangulated cross-rate (USD→EUR, then EUR→INR, divided out), not a rate the ECB publishes directly. The tool's footer says this explicitly so nobody mistakes it for a directly-quoted market rate.
