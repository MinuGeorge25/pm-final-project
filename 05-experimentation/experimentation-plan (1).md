# A/B Experiment Brief, Riverty BU Pay & Credit, First Consumer Card

## Parameters
| Parameter | Decision |
|---|---|
| Feature under test | B3, a “What you owe” section on the app home screen showing “Card”, “Pay later orders” and one “Total owed”, with the total shown only when both parts load. |
| Persona | Lena, 32, Cologne, a salaried heavy BNPL user with no real cushion. She wants money to leave her account only after she has decided to keep an item (N-01), and to see what she owes in one place (N-07). |
| Expected outcome | More newly activated cards still make a purchase two months after activation, because the card is no longer “one more thing to check before payday” (N-02). |
| Primary success metric | Month-2 activity of newly activated cards: the share making at least one purchase two months after activation (cohort_activity.csv definition), measured per card by assigned arm. |
| Baseline rate | About 54%: 51.0% (Month 1 cohort, 98 cards) and 57.1% (Month 2 cohort, 133 cards). |
| Guardrail metric | Partner merchant share of card volume (euro-weighted). Baseline 63.1% in Month 4. Investigate if the variant is below 58.8% in any calendar month, or more than 3 points below control in the same month. Stop if it runs more than 5 points below control for two consecutive months. |
| Guardrail boundary | · |
| Second guardrail | · |
| Minimum Detectable Effect | +8 percentage points, from 54% to 62%. |
| Sample size per arm | bout 597 activated cards per arm, 1,194 in total (two-proportion formula, p < 0.05 two-sided, 80% power). |
| Traffic split | 50/50, randomised per card at activation and sticky. Enrolment until both arms reach about 597 cards, plus 2 to 3 months so the last card is observed through month 2. About 6 to 7 months at roughly 300 activations a month |
| Test duration | About 6 to 7 months at roughly 300 activations a month |
| Significance threshold | p < 0.05, two-sided, with no deviation. Fix the sample size and read date in advance, with no peeking. |

## Control vs. Variant
- **Control (A):** Today’s experience: the card balance and pay later orders on two separate screens with no combined total (N-07, T-103), and reminders for different amounts in one week (T-104). Funnel context: 431 activated, 350 (81.2%) with a first purchase in month 0, and 253 (58.7%) with three or more. Engineering should confirm the exact screens and entry points, because I’ve described them from tickets, not the live app.
- **Variant (B):** The control plus one inline “What you owe” section on the home screen, above the fold. It has rows labelled exactly “Card” and “Pay later orders”, with amounts like 412,50 €, and a total equal to their sum in integer cents. The amounts must match the existing screens. The total exists only when both parts have loaded. A failed part shows “Couldn’t load” and the other part still shows its amount. Placeholders show until both settle. A part not loaded after 10 seconds, or with a negative amount, counts as failed. The “How this adds up” screen is left out of the test.
- **Held constant (isolation check):** Identical in both arms: app build (variant behind a flag), eligibility and onboarding (no B2, no T-106 fix), reminders and dates (no B8), decline messages (no B1), pricing, interest, limits, offers, cashback, marketing and support content, and the same concurrent weeks, metric definition and data source. Check before reading: arms near 50/50 and balanced on activation timing, employee status, BNPL use and age band, and load time logged in both arms.

## Hypothesis
> I believe that B3, a “What you owe” section on the app home screen showing “Card”, “Pay later orders” and one “Total owed”, with the total shown only when both parts load. for Lena, 32, Cologne, a salaried heavy BNPL user with no real cushion. She wants money to leave her account only after she has decided to keep an item (N-01), and to see what she owes in one place (N-07). will result in More newly activated cards still make a purchase two months after activation, because the card is no longer “one more thing to check before payday” (N-02)., as measured by a +8 percentage points, from 54% to 62%. change in Month-2 activity of newly activated cards: the share making at least one purchase two months after activation (cohort_activity.csv definition), measured per card by assigned arm. within About 6 to 7 months at roughly 300 activations a month. We will protect Partner merchant share of card volume (euro-weighted). Baseline 63.1% in Month 4. Investigate if the variant is below 58.8% in any calendar month, or more than 3 points below control in the same month. Stop if it runs more than 5 points below control for two consecutive months. throughout the test.

## Shipping criteria
> We will **ship** if Month-2 activity of newly activated cards: the share making at least one purchase two months after activation (cohort_activity.csv definition), measured per card by assigned arm. improves by ≥ +8 percentage points, from 54% to 62%. at p < 0.05, two-sided, with no deviation. Fix the sample size and read date in advance, with no peeking. and Partner merchant share of card volume (euro-weighted). Baseline 63.1% in Month 4. Investigate if the variant is below 58.8% in any calendar month, or more than 3 points below control in the same month. Stop if it runs more than 5 points below control for two consecutive months. does not reach _(not filled in)_ after About 6 to 7 months at roughly 300 activations a month.
> We will **iterate** if direction is positive but lift is below the MDE.
> We will **kill** if the primary metric shows no improvement or moves negatively.
> The read date is fixed at the end of About 6 to 7 months at roughly 300 activations a month, no results reviewed before this date.
