# GTM Launch Plan, Riverty BU Pay & Credit, First Consumer Card

| Field | Value |
|---|---|
| Feature | B3, the “What you owe” section on the app home screen, with Card, Pay later orders and one Total owed. The total shows only when both parts load. |
| Goal | Engagement |
| Launch tier | S, Minimal |

## Goal & Audience
- **Goal:** Engagement, the card’s problem is use after activation, not awareness or conversion. In the pilot, 81.2% of activated cards made a first purchase and 58.7% reached three or more. Month-2 activity was only 51.0% and 57.1% (funnel.csv, cohort_activity.csv). The goal is to keep people who already hold the card using it, and it matches the primary metric from the experiment.
- **Target audience:** Lena, 32, Cologne, a salaried heavy BNPL user who holds the card. In the pilot she is the heavy segment: 138 of 431 activated cards (segments.csv). The reachable audience is card holders, who are far fewer than the assumed 1,000,000 BNPL users in the Module 6 pack.

## Launch Tier
- **S, Minimal**, Reach: the card is not publicly launched, and the pilot had 431 activated cards.
Revenue impact: indirect, through retention. The pack has no interchange or interest figures.
Risk of silence: low. The section is visible on arrival. The real risk is a user not noticing it, or a support agent being surprised by it.
Over-investing: press or paid media would promise a card that isn’t on general sale, and would add noise to a read that depends on a clean control.

## Channels
1. **Owned: In-app: the section itself plus a one-time “New” notice.Lena shops almost entirely on her phone, and the app is where the problem lives. The assumed monthly app audience is 350,000 of the BNPL base.**
2. **Owned: Push notification, one message.Reaches opted-in card holders who haven’t opened the app. The assumed push audience is 250,000.**
3. **Owned: Short email to card holders.The widest assumed reach (400,000), but the weakest fit for a phone-first user. It is a backup, sent after the in-app and push messages.**

## Enablement & Assets
Support and CS: a one-page briefing and macro that answers three questions: What does Total owed include? Why does a row say “Couldn’t load”? Does it match my Card and Pay later screens? Plus an escalation path for any wrong-total report.
Assets to build: two lines of in-app copy, one push message, one short email, a help article and a release note. Keep to amounts only, with no claims about due dates or credit score.
Sales and merchants: no outreach, since merchants (N-08, N-09) care about conversion and offers, not this.

## Ownership, Budget & Timeline
- **Ownership & budget:** Activity	Owner (role)
Launch plan and the go/no-go call	PM [Minu George]
Build, flag and rollout	Engineering lead 
Copy and in-app message	Designer 
Push and email	Lifecycle or CRM owner 
Help article, macro and briefing	CS lead 
Copy review for financial wording	Compliance reviewer 

Budget and gaps: I assume no extra spend, because every channel is owned and the work fits the assumed squad of about 5. The gaps are the help article and email template, which don’t exist yet, and whether compliance must approve wording about balances. Confirm that last point, because approval can take months (N-11).
- **Timeline:** Phase 1, beta: the A/B test, about 6 to 7 months at my assumed 300 activations a month. Send no announcements to either arm, because that would break the isolation check. In the last four weeks, build the assets and brief CS.
Phase 2, launch moment: only after a SHIP decision. Roll out in stages (10%, 50%, 100%) over two weeks while watching the guardrail. Send the in-app notice from day 1, one push at 100% and the email a week later.
Phase 3, post-launch: a 30-day check on support and errors, and a 90-day read of month-2 activity.

## Success Metrics
- **Metrics:** Month-2 activity of newly activated cards: baseline about 54%, target 62%.
30-day view rate: the share of active card holders who open the section at least once. Target at least 60% (my assumption).
Repeat viewers: the share of viewers who come back at least once more in the next 30 days. Target at least 40% (my assumption). It separates a habit from curiosity.
- **Bad signal to watch for:** a high view rate with flat month-2 activity, meaning people look but don’t buy, so the view isn’t the lever. Also watch for a spike in tickets saying “which total is real” or “wrong total”, a high “Couldn’t load” rate, or a fall in partner merchant share below 58.8%.
- **Likely post-launch decision:** iterate. Keep the section live, since it is cheap and low risk, then add the combined reminder (B8) and per-part due dates, and judge on 90-day cohorts. My power calculation says the test itself will most often land inconclusive, so this plan assumes a SHIP and could be replaced by a re-test.
