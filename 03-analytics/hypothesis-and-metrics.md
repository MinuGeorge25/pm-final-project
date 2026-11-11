# Hypothesis & Success Metrics (Module 3)

## Pre-work · Hypothesis check
- **Role , who you are solving for (from M2):** _(not filled in)_
- **Goal , what this user is ultimately trying to achieve:** _(not filled in)_
- **Friction / moment of misery , the specific pain blocking their goal:** _(not filled in)_
- **Current workaround , the external tool or manual process they rely on (M2):** _(not filled in)_
- **Problem Hook , your one-sentence framing of the business crisis (M1):** _(not filled in)_
- **Value Proposition , the outcome your initiative promised to deliver (M1):** _(not filled in)_

## Read the evidence in your case
- **Where does your case say people stall or leave? Does that match the friction you wrote in Module 2?:** Where people stall

Invited to applied: 484 of 1,200 never applied (59.7% applied). It is the biggest loss, but the test was invite-only, so it measures interest and not product friction.
Approved to activated: 155 of 586 never activated (73.5%). Of the steps after application, this has the lowest rate.
Activated to 3+ purchases: 81 activated cards made no purchase in the activation month (81.2% made one). Of the 350 who bought once, 97 stopped short of three (72.3%). Only 253 of 431 activated cards (58.7%, my calc) reached three or more.
Identity check: 88 people were lost at this step (87.7% completed). T-106 (repeated document photo) is the only ticket that matches a funnel step. Does it match my Module 2 friction? Only partly. My friction (two screens, two reminders, an unexplained decline) happens after first use. The funnel’s biggest stalls come before or at activation, and the only steps where my friction could plausibly bite are the 97 who stopped between one purchase and three. The funnel can’t attribute reasons, so it neither confirms nor refutes the tracking pain. Signals pointing in different directions

First purchase is healthy (81.2%), but activation (73.5%) and repeat use (72.3%) are weak.
The top of the funnel is flattering. test_launch_rates.csv says the 93.3% approval rate may run high because invitees are mostly employees.
Identity check loss (T-106) isn’t in my persona’s friction at all, so my map misses a real stall.
- **What got better or worse in the case, and does that support the workaround your persona uses?:** Better

Volume rose from EUR 15,207 in Month 1 to EUR 61,086 in Month 4, and average spend per active card from EUR 200.09 to EUR 233.15.
The in-store decline rate fell from 12.1% to 8.7%, though it was 6.4% in Month 3.
Partner merchant share of volume rose from 56.8% to 63.1%, which fits the merchant-first positioning. It dipped to 58.8% in Month 3.

Worse

Active cards fell from 278 to 262 in Month 4, and the overall decline rate rose from 2.2% (Month 2) to 3.5%.
Every cohort loses activity. The Month 1 cohort went from 77.6% in month 0 to 51.0% in month 2, and Month 2 went from 82.0% to 57.1%.
Only 39 cards were activated in Month 4, against 161 in Month 3, and the data doesn’t say why.
Does it support the workaround? It is consistent with it, but it doesn’t support it. Falling back to a debit card would look like the activity decay, but so would novelty fading (N-12). Nothing in the data measures duplicate payments, app checking or reasons for going inactive.

Signals pointing in different directions

Average spend per active card rose while active cards fell, so the remaining users may just be the heavier ones.
The Month 1 cohort rebounded from 51.0% to 55.1% by month 3, but on 98 cards that is about 4 cards.
In-store share stayed flat at 15.4–17.7%, so there is no sign it is growing.
In-store declines are small in absolute terms. Back-calculating from the monthly rates gives about 48 across four months (my calc), which matches T-101, and about 18 in Month 4.
- **Which user in the case is carrying the pain, and is that the person your Module 2 persona describes?:** Who carries the pain? The CSVs show usage, not pain, so I can’t answer this directly. The best proxy is exposure.

Heavy BNPL users have the most to track: 5.82 purchases per active month, EUR 320.88 a month, and instalments at 25.4% of purchases (light is 6.0%, regular 12.7%). They also activate best, at 82.6% of approved (138 of 167).
The in-store decline half fits the heavy segment less. Their in-store share is the lowest, at 12.1% (light is 24.5%). In absolute terms the segments are similar, at about 0.70, 0.76 and 0.60 in-store purchases per active month for heavy, regular and light (my calc).
Lena’s profile fits on usage. 25–34 is the largest age band (453 invited), with the highest average spend (EUR 235.75) and the lowest in-store share (14.8%).

Is that my Module 2 persona? Partly. The tracking friction fits heavy users, but the decline friction fits them less than I assumed.

Signals pointing in different directions

N-02 (a heavy BNPL interviewee) says a third card is one more thing to check, yet the heavy segment activates and uses the card most. Attitude and behaviour disagree.
Ages 45–54 activate best (81.2%, but only 65 of 80), which doesn’t match Lena’s 25–34 profile.
Employees were approved at 55.1% (352 of 639), against 41.7% for friends and family (234 of 561, my calc), which fits N-10’s warning that employees flatter the results. They also make up 253 of the 431 activated cards.

## Step 2 · Craft your hypothesis
- **Qualitative evidence (from M2) , quote the specific friction / moment of misery for your persona:** “I could not see in one place what I owe on the card and what I owe on my normal pay later orders.” (N-07). Supporting: two reminders for different amounts arrived in one week (T-104), and a third card is “one more thing to check before payday” (N-02). Secondary friction: the card was declined at a bakery and “the app did not say why” (N-06).
- **Quantitative evidence (from M3) , name the metric or data point that confirms the pain; cite the number:** No metric measures the tracking pain directly. The closest signal is the activity decay in cohort_activity.csv. The Month 1 cohort fell from 77.6% active in month 0 to 51.0% in month 2, and the Month 2 cohort from 82.0% to 57.1%. Exposure is highest among heavy BNPL users, who make 5.82 purchases per active month and put 25.4% of purchases on instalments (segments.csv). This confirms a retention gap and who is exposed, not why people leave.
- **Persona , role, goal, and the friction you confirmed in the reconciliation steps:** Lena, 32, Cologne, a salaried heavy BNPL user. She wants money to leave her account only after she has decided to keep an item (N-01), and to see what she owes and when. Reconciliation confirmed the tracking friction on exposure (heavy segment, 25–34 band). It weakened the decline half, because heavy users have the lowest in-store share (12.1%, against 24.5% for light), so the decline is now secondary. Lena is a composite, and 253 of 431 activated cards belong to employees.
- **Problem you are solving , one sentence describing the specific friction this initiative removes:** Heavy BNPL users like Lena cannot see in one place what they owe on the card and on pay later orders, or when it is due, so the card becomes one more thing to check.
- **Strategic outcome , what behaviour change do you expect, and how does it map to retention / revenue / churn?:** Behaviour change: Lena keeps using the card after her first month instead of reverting to her bank card. Retention: higher month-2 activity. Revenue: more active cards, but I can’t size it because the pack has no interchange or interest figures. Churn: annual churn isn’t measurable in four months (test_launch_rates.csv), so cohort activity is the proxy.
- **Primary success metric (initiative signal) , the leading indicator that tells you the gap is closing:** Month-2 activity of newly activated cards, the share making at least one purchase two months after activation. Baseline: 51.0% (Month 1 cohort) and 57.1% (Month 2 cohort). Target (my assumption): at least 62% in two consecutive cohorts.
- **Guardrail metric (product signal) , the metric that must NOT drop; it protects your existing base:** Partner merchant share of card volume must not fall below 58.8% (the Month 3 low, my assumption). It was 63.1% in Month 4 and 56.8% in Month 1. This protects the merchant-first strategy. The better guardrail would be Riverty checkout BNPL volume among card holders versus non-holders, which the pack doesn’t have, so I’d ask for it.
- **Decision window , how much time or data before you scale, pivot, or kill? minimum threshold to proceed?:** The clock starts when the fixed build ships, not now, because approval takes months (N-11). Minimum to proceed: two consecutive cohorts of at least 150 activated cards each, observed through month 2, which is about 3–4 months after launch. Scale if both cohorts reach 62% or more and the guardrail holds. Pivot if both stay at 51–58%, which would mean clarity wasn’t the main driver. Stop and rethink if either falls below 51%.
- **Draft your full hypothesis sentence , one to three sentences; quote the metric, name the persona, name the outcome:** Based on N-07 (“I could not see in one place what I owe on the card and what I owe on my normal pay later orders”) and on cohort activity falling from 77.6% in month 0 to 51.0% in month 2 for the Month 1 cohort, I believe that giving Lena, a heavy BNPL user, one balance, one due date and a plain reason whenever a payment fails will keep her using the card after her first month. I will measure this as an 8-point (about 15%) rise in month-2 activity, from a baseline of about 54% (the 51.0% and 57.1% cohorts) to 62%. I will protect partner merchant share of card volume at or above 58.8%, and will make a go/no-go decision once two consecutive cohorts of at least 150 activated cards have been observed through month 2. 
Assumptions: The 62% target, the 58.8% floor and the 150-card minimum are mine, not from the data pack. The 58.8% floor is the Month 3 low in monthly_trend.csv, and Month 4 was 63.1%.
Baseline: The 54% is the average of two small cohorts (98 and 133 cards), so treat it as approximate. An 8-point lift on about 150 cards sits close to the noise, which is why the rule needs two cohorts.
Cause: The activity decay could be novelty fading (N-12) as easily as tracking friction. This is a hypothesis to test, not a finding.
Bias: Employees make up 253 of the 431 activated cards (N-10), so real-customer results may be weaker.
