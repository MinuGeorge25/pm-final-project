# Experimentation Plan (Module 5)

## Get your documents ready
- **From M3, your hypothesis sentence:** Based on N-07 (“I could not see in one place what I owe on the card and what I owe on my normal pay later orders”) and on cohort activity falling from 77.6% in month 0 to 51.0% in month 2 for the Month 1 cohort, I believe that giving Lena, a heavy BNPL user, one balance, one due date and a plain reason whenever a payment fails will keep her using the card after her first month. I will measure this as an 8-point (about 15%) rise in month-2 activity, from a baseline of about 54% to 62%. I will protect partner merchant share of card volume at or above 58.8%, and I will make a go/no-go decision once two consecutive cohorts of at least 150 activated cards have been observed through month 2.
- **From M3, your primary success metric & guardrail metric:** primary success metric and guardrail
	Metric	Baseline	Target
Primary	Month-2 activity of newly activated cards	51.0% (Month 1 cohort, 98 cards) and 57.1% (Month 2 cohort, 133 cards), about 54% on average	62% in two consecutive cohorts of at least 150 activated cards
Guardrail	Partner merchant share of card volume	63.1% in Month 4 (56.8%, 63.0% and 58.8% in Months 1 to 3)	Stays at or above 58.8%

The 62% target, the 58.8% floor and the 150-card minimum are my assumptions, not from the data pack. Only one pilot cohort (Month 3, 161 cards) reached 150.
- **From M4, the feature you scoped in your PRD this is what you're testing:** B3, one balance view for card and regular pay later orders. It is the top Now quick win, scored value 5 and effort 2.

Four must-haves:
One view showing “Card” and “Pay later orders”.
One headline total that equals the sum of both.
No total if either part fails to load.
A single place to see it.
Out of scope:
Changing due dates.
Payments and B4.
Other providers’ obligations.
Budgeting tools.
Decline reasons (B1) and the combined reminder (B8).

## Define your experiment parameters
- **Feature under test pull from your M4 PRD:** B3, one balance view for card and regular pay later orders. An engineer could build the variant from this spec:

Placement: a “What you owe” section on the app home screen, visible without scrolling.
Content: a “Total owed” figure, a row “Card” and a row “Pay later orders”. Amounts are euro cents formatted like 412,50 €, and the total equals Card plus Pay later orders to the cent.
Rules:
The total exists on the page only when both parts have loaded.
A failed part shows “Couldn’t load”, and the other part still shows its amount.
Placeholders show until both parts settle.
A part not loaded after 10 seconds counts as failed.
A negative or non-numeric amount counts as failed.
Both amounts must match the existing screens exactly.
Not in the variant: due dates, payment buttons, decline reasons (B1) and the combined reminder (B8). I’d also drop the read-only “How this adds up” screen from the test, since it adds nothing beyond the sum and keeps the variant to one component.
Control: today’s experience, with the card balance and pay later orders on two separate screens and no combined total. No other change ships to either arm during the test.
Assignment and logging: assign each card at activation, 50/50 and sticky by card ID. Log the assignment (card ID, arm, time) and each time the view renders, including whether both parts loaded. The PRD listed event tracking as a Should, and this test promotes it to a must.
- **Persona pull your M2 persona:** Lena, 32, Cologne, a salaried heavy BNPL user with no real cushion. She wants money to leave her account only after she has decided to keep an item, and to know what she owes in one place (N-01, N-07). Heavy users make 5.82 purchases per active month, with instalments at 25.4% of purchases (segments.csv).
- **Expected outcome the behaviour change you expect, from your M3 hypothesis:** Lena stops treating the card as one more thing to check before payday (N-02), so more newly activated cards still make a purchase two months after activation. This is a hypothesis: the cohort decay could be novelty fading (N-12) as easily as tracking friction.
- **Primary success metric the one number that defines success, from M3:** Month-2 activity of newly activated cards: the share of cards activated in a month that make at least one purchase two months later, as defined in cohort_activity.csv. It is measured per card, by assigned arm.
- **Baseline rate today's rate of your primary metric, from your M3 data:** About 54%: 51.0% for the Month 1 cohort (98 cards) and 57.1% for the Month 2 cohort (133 cards). The card-weighted figure is 54.5%, and using either cohort’s rate changes the sample size by only a few cards.
- **Guardrail metric & boundary what must not break, and how far it can move before you investigate:** Metric: partner merchant share of card volume, weighted by euros.
Baseline: 63.1% in Month 4 (56.8%, 63.0% and 58.8% in Months 1 to 3).
Boundary: it must stay at or above 58.8%. Investigate if the variant arm falls below 58.8% in any calendar month, or runs more than 3 points below control in the same month. Stop if it runs more than 5 points below control for two consecutive months.
Assumptions: the floor and both gaps are mine. The pilot moved by up to 6.2 points between months, so I compare the two arms within the same month.
- **Minimum Detectable Effect (MDE) the smallest improvement worth shipping, your floor:** +8 points, from 54% to 62%. This matches the M3 target. A smaller floor isn’t affordable: +5 points would need 1,543 cards per arm, against 597 for +8. The risk is that B3 delivers only one of the hypothesis’s three fixes, so the real effect may be smaller than 8 points and this test may miss it.
- **Sample size per arm use the calculator in the builder, baseline + MDE:** About 597 activated cards per arm, 1,194 in total. I calculated it with the standard two-proportion formula at 5% significance (two-sided) and 80% power. I can’t run the builder’s calculator here, so check the figure in it. Raising power to 90% would need 798 per arm.MDE	Cards per arm	Months of enrolment at pilot pace (about 108 activations a month)
+5 points	1,543	28.6
+6 points	1,068	19.8
+8 points	597	11.1
+10 points	379	7.0
- **Traffic split & test duration 50/50 standard · cover ≥ 2 weekly cycles:** Split: 50/50, randomised per card at activation and sticky.
Duration: enrolment until each arm has about 597 cards, plus about 2 to 3 months so the last card can be observed through month 2. Enrolment will span many weekly cycles, so the two-cycle rule is not the constraint here.
Problem: at the pilot’s pace of about 108 activations a month, enrolment alone takes about 11 months. A rollout of about 300 activations a month would take about 4 months of enrolment and 6 to 7 months in total. Ask for the planned activation volume before committing.
- **Significance threshold p < 0.05 is standard, explain any deviation:** p < 0.05, two-sided, with no deviation. Two-sided because the view could also lower activity. Fix the sample size and the analysis date in advance, with no early peeking, and name month-2 activity as the single primary metric. The guardrail is monitored against its boundary, not significance-tested. Treat any heavy-user cut as exploratory.

## Define your control and variant
- **Control (A) the current experience, reference your M2 moment of misery and M3 funnel/workflow data:** What Lena sees today: two separate screens, one for the card balance and one for her regular pay later orders, with no combined total. Participants ask which total is real (N-07, T-103). Statement dates and pay later due dates differ, so two reminders for different amounts can arrive in the same week (T-104). That is why she calls a card “one more thing to check before payday” (N-02).

Where the control sits in the funnel (M3):

431 cards are activated.
350 (81.2%) make a first purchase in the activation month.
253 (58.7% of activated, my calc) make three or more.
Month-2 activity is 51.0% for the Month 1 cohort and 57.1% for the Month 2 cohort, the baseline of about 54%.

Control spec: the current app with no change. It logs the same assignment event as the variant, so measurement is symmetrical.

Check before launch: I’ve described the control from the tickets and notes, not from the live app. Have engineering confirm the exact screens, entry points and reminder rules, because I don’t know whether any summary already exists on the home screen.
- **Variant (B) your single change, copy the relevant screens & functional requirements from your M4 PRD:** The single change: a “What you owe” section on the app home screen. It differs from the PRD doc, which lists a separate screen and a “How this adds up” screen. This variant puts the view inline and leaves “How this adds up” out of the test.

UI elements:

A heading, “What you owe”.
A “Total owed” figure.
A row “Card” and a row “Pay later orders”, each with an amount.
Grey placeholders while loading.
A “Couldn’t load” state per row.

Rules, copied from the PRD’s functional requirements and updated for the inline placement:

The section sits above the fold at 375 × 667 px. Rows are labelled exactly “Card” and “Pay later orders”, with amounts formatted like 412,50 €.
The total sits above the rows and equals Card plus Pay later orders in integer cents.
Both amounts equal the figures on the existing screens, character for character.
The total exists on the page only when both parts have loaded. Check this in the DOM, not with CSS.
A failed part shows its label and “Couldn’t load”, and the other part still shows its amount.
With no open pay later orders, the row shows 0,00 € and the total equals the card amount.
Placeholders show until both parts settle. A part not loaded after 10 seconds, or returning a negative or non-numeric amount, counts as failed.
Amounts of 100.000,00 € or more wrap and are never cut off, and nothing clips at 200% text size.

The PRD’s old rule that one tap opens the view is dropped, because the section is now visible on arrival.

Logging: assignment (card ID, arm, time) and each render of the section, including whether both parts loaded.
- **Isolation check, what has NOT changed? list everything identical between arms (app version, eligibility rules, notifications, onboarding). If something changed inadvertently, your test is compromised.:** Identical in both arms:

App build and release: both arms run the same build, with the variant behind a flag set per card. Nothing else ships during the test.
Eligibility and onboarding: the same rules for newly activated cards, the same approval and credit policy, and the same identity check (T-106) and wallet flow (B2 not shipped).
Reminders and dates: the same reminders, timing and amounts (T-104, B8 not shipped), and unchanged statement and due dates.
Decline handling: the same messages (B1 not shipped).
Commercial terms: the same pricing, interest, limits, partner acceptance, offers and cashback.
Comms and support: the same marketing messages, help content and support scripts.
Timing and measurement: both arms run concurrently over the same weeks. The metric definition, the data source and the analysis date are identical.

Where the arms differ by design: only the “What you owe” section and its render events.

Contamination and balance risks to check:

Load time. The variant fetches both balances on the home screen. If that slows the home screen for variant users, the test measures speed as well, so log load time in both arms.
Social leakage. The pilot is friends and family, so participants may compare screens. Randomise per card, and watch for shared accounts.
Arm balance. Run a check that the arms are close to 50/50 and similar on activation timing, employee versus other customers, BNPL usage and age band before reading any result. If they aren’t, the test is compromised, so stop and fix the assignment.

## Formalize your hypothesis & shipping criteria
- **Your hypothesis (filled in):** I believe that putting a “What you owe” view, one total across the card balance and pay later orders, on the home screen for newly activated card holders like Lena, a heavy BNPL user, will result in more of them still making a purchase two months after activation, as measured by an 8 percentage point (about 15% relative) rise in month-2 activity, from about 54% to 62%, within about 6 to 7 months. That is about 4 months of enrolment to reach 597 cards per arm, plus 2 to 3 months of follow-up. We will protect partner merchant share of card volume (63.1% in Month 4, floor 58.8%) throughout the test.
- **Your shipping criteria (filled in):** SHIP if month-2 activity improves by at least 8 percentage points (about 54% to 62% or more) at p < 0.05, two-sided, and partner merchant share of card volume does not reach its boundary after about 6 to 7 months. The boundary is below 58.8% in any calendar month, or more than 3 points below control in the same month. “Improves by at least 8 points” means the observed lift, not just its confidence interval.

ITERATE if the direction is positive but the lift is below 8 points, meaning between +2 and +8 points. That means a new test with a new read date, not shipping.

KILL if the primary metric shows no improvement or moves negatively, meaning a lift below +2 points.

Read date: fixed at the end of the test duration, which is the month-2 follow-up of the 1,194th enrolled card. The calendar date is set once enrolment pace is known after the first 2 weeks. Pace is not outcome data.

Four rules I’d commit to now:

Sealed primary metric. Month-2 activity is not looked at before the read date. The only early checks are the guardrail, arm balance (close to 50/50) and exposure, which are safety checks and not results.
Guardrail overrides lift. If the guardrail boundary is reached, do not ship, whatever the lift. Early breaches trigger investigation, and a stop if the variant runs more than 5 points below control for two consecutive months.
Void tests. If the arms are not balanced or the variant failed to render for a large share of cards, the test is void and is not read.
No peeking and no slicing. Heavy-user cuts are exploratory and can’t change the decision.
- **Hardest parameter to define, and did it change your hypothesis? quick debrief:** The hardest was the minimum detectable effect, because it is tied to sample size and test duration. The 8 points I’d want to ship needs 597 cards per arm. The pilot activated only about 108 cards a month, which would mean about 11 months of enrolment before a single read. Setting a smaller floor would have been easy to justify on value, but +5 points needs 1,543 per arm. I had to choose between a floor I can afford to detect and a floor I would actually want.

Yes, it narrowed the hypothesis in three ways:

One feature instead of three. The M3 hypothesis bundled one balance, one due date and a failure reason. The test covers only B3, so the effect I’m asking it to deliver is probably smaller than 8 points.
A fixed read date. I swapped “two consecutive cohorts of at least 150 cards” for a fixed sample and a sealed read date, so I can’t stop when the numbers look good.
Randomised cards. The unit changed from calendar cohorts to randomised cards, which removes cohort-mix effects.

What to flag:

My assumptions: the 300 activations a month behind the 6 to 7 months, the +2 kill line, and the 3-point and 5-point guardrail gaps are mine.
Underpowered risk: if B3 alone really delivers 4 or 5 points, this test will most likely land in ITERATE.
Open question: the planned activation volume for the real rollout. Without it the duration is a guess.
