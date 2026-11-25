# FD & DPS Calculator — Bangladesh

A single-page, offline-friendly calculator for Bangladeshi Fixed Deposits (FD) and Deposit Pension Schemes (DPS). Compare real bank rates, see maturity value, total interest and after-tax interest — all in your browser, no data sent anywhere.

## What it does

- **Fixed Deposit mode** — deposit amount, tenure (months/years), annual rate and compounding (monthly / quarterly / annually) → maturity value, total interest, TDS deducted and after-tax interest, with the formula shown.
- **DPS mode** — monthly deposit, tenure and rate → maturity value (annuity with monthly compounding, instalment at the start of each month), total deposited, total interest, after-tax interest, plus a monthly balance-growth chart drawn on canvas (no external chart library).
- **Compare banks** — enter a deposit and tenure once and see maturity values side by side across verified banks, sorted best-first, for FD or DPS.
- **Saved calculations** — history stored in `localStorage` (key `fdbd_history`), with reload and delete. Nothing leaves your device.
- **Tax** — shows TDS at the real Bangladesh rule: **10% with e-TIN, 15% without**.

## How to use

Open `index.html` in any modern browser (or host it on GitHub Pages). Pick a tab, enter your numbers, tap **Calculate**. Tap a bank rate in the table below the calculator to use it, or type your own rate. Use **Save this calculation** to keep a result in history.

## Data sources (rates — indicative, Nov 2026)

| Bank | FD rate (p.a.) | DPS rate (p.a.) |
|---|---|---|
| Islami Bank Bangladesh | 10.00% | — |
| IFIC Bank | 8.50% | — |
| Dutch-Bangla Bank (DBBL) | 7.20% | 8.50% |
| BRAC Bank | 7.50% | 7.00% |
| Sonali Bank | 7.10% | — |
| ONE Bank | — | 10.00% |

Sources: BRAC Bank ALCO Circular 2026/11 (effective 15 Oct 2026); DBBL official term-deposit page; IFIC Islamic deposit rates (16 Aug 2026); Bangladesh Bank announced deposit-rate chart, Oct 2026; ONE Bank DPS schedule (3 Nov 2026). "—" means no rate for that product could be verified from an official source — it is not zero. IFIC's FD is an 8.25–8.75% range; the 8.50% midpoint is used. Islamic banks pay an expected Mudaraba profit rate, which can vary.

**Rates change often — confirm the current rate with the bank before investing. All results are estimates, not financial advice.**

## Maths

- FD: `Maturity = P × (1 + r/n)^(n×t)` — P = principal, r = annual rate, n = compounding periods per year, t = years.
- DPS: `Maturity = P × [((1 + r/12)^n − 1) / (r/12)] × (1 + r/12)` — P = monthly instalment, n = months. The extra `(1 + r/12)` factor is because the instalment is paid at the start of each month, as in standard BD DPS practice.

## Tech

Single `index.html` — all CSS and JavaScript inline, no dependencies, no build step. Amounts use Bangladesh-style grouping (৳1,00,000). Works offline once loaded.

Built by Nafiz Bin Azad.
