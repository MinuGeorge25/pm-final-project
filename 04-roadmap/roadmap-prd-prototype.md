# Roadmap, PRD & Prototype (Module 4)

## Your strategic anchors
- **Persona (M2), who are you solving for?:** Lena, 32, Cologne, a salaried heavy BNPL user on a middling income with no real cushion. She shops almost entirely on her phone and wants money to leave her account only after she has decided to keep an item (N-01), with a clear view of what she owes and when. Heavy users match this profile in the data: 5.82 purchases per active month and instalments at 25.4% of purchases (segments.csv).

Lena is a composite of N-02, an interviewee who never used the card, and N-07, a test participant whose profile isn’t recorded.
- **Primary success metric (M3), your leading indicator:** Month-2 activity of newly activated cards: the share making at least one purchase two months after activation.

Baseline: 51.0% for the Month 1 cohort (98 cards) and 57.1% for the Month 2 cohort (133 cards), about 54% on average (cohort_activity.csv).
Target: 62% in two consecutive cohorts of at least 150 activated cards. The target and the 150-card minimum are my assumptions, not from the data pack.
- **Moment of misery (M2), the specific friction blocking the goal:** “I could not see in one place what I owe on the card and what I owe on my normal pay later orders.” (N-07)

Two reminders for different amounts also arrived in the same week (T-104), so the card becomes “one more thing to check before payday” (N-02). The unexplained decline (N-06, T-101) is secondary: heavy users have the lowest in-store share (12.1%), and there were about 48 declines across four months.
- **Guardrail metric (M3), what must not drop or break:** Partner merchant share of card volume must stay at or above 58.8%, which protects the merchant-first strategy. It was 63.1% in Month 4 (56.8% in Month 1, 58.8% in Month 3, per monthly_trend.csv). The 58.8% floor is my assumption, set at the Month 3 low.

Riverty checkout BNPL volume among card holders versus non-holders would be a better guardrail, but the data pack doesn’t have it, so I’d ask for it.

## Scan the backlog & set a human baseline
- **My instinctive “quick wins” before touching the AI (2 to 3 feature IDs + why):** One balance view, Decline reason and retry hint

## Audit, override & decide
- **Where did you override the AI? (feature + old vs. new score + why):** Where I overrode
Feature	Old → new	Why
B4 Choose pay now or pay later per purchase after paying	Value 3→ 4 (effort 5). Quadrant: Major Project → Next for this initiative	Value 5 means “directly moves month-2 activity”, and nothing links B4 to it. Heavy users’ 25.4% instalment share (segments.csv) shows usage, not retention. The pack has no retention by segment. 
B8 One combined reminder	Effort 2 → 3. moves from  Quick Win - Major project.	The mismatch in T-104 comes from two systems each sending its own reminder. A combined message needs the same card and pay later data join as B3, so it can’t run ahead of B3.
- **Did the AI over-value a Sales/Eng request your M2 interviews don’t support?:** Only B4, and it isn’t really a Sales or Engineering request. It is a differentiator idea. In the interviews it rests on N-04 (one 18–24 interviewee who wants to split the weekly shop) and N-01 (online, after keeping an item). Neither speaks to month-2 activity.

The clearer Sales request, B5 (partner offers), was already low. Consumers never asked for it, and N-08 and N-09 give only conditional merchant interest. Cashback (B6) stays at 2, because N-12 supports a trial, not continued use.
- **Did it underweight something your M3 cohort/funnel data strongly supports?:** Yes, two things.

The pre-activation leak. 285 of 716 applicants (39.8%) were lost before activation: 88 at the identity check, 42 at approval and 155 at activation. Only B2 touches this area, and the pack says it doesn’t gate activation. T-106 is the one ticket tied to a funnel step. I’d add B9: resume the identity check after a failed upload. The 178 activated cards (41.3%) that fell short of three purchases are a different denominator, so the two losses aren’t directly comparable.
Measurability. Only the Month 3 cohort (161) reached 150 activated cards. The others had 98, 133 and 39. So my decision window, two cohorts of at least 150, would not have been met in the pilot’s own four months. I’d ask for the planned invite volume per month before committing to that window.

## Generate your interactive roadmap
- **My “Now” lane (this sprint), the 2 to 3 quick wins I’ll build first:** Decline reason and retry hint shown in the app
Cheap, covers online declines too, and one unexplained decline sent a participant back to debit.
One balance view for card and regular pay later orders
Directly removes the two-screen misery for the heavy users with the most to track.
One combined reminder showing both amounts and both dates (scoped-down B8)
May fix T-104 without changing due dates, if engineering confirms no terms change.
- **What I cut, and the “no” I’m protecting the scope from:** Offers from partner merchants inside the card app, Revisit after merchant discovery, since merchants gave only conditional interest.
Cashback on every purchase, Prompts a trial, not retention (N-12), and spends margin.
Physical card, No evidence anyone asked for it.
- **Prototype/roadmap screenshot link (paste into your deliverables):** https://github.com/MinuGeorge25/pm-final-project/blob/main/04-roadmap/roadmap-pay-credit-visual.html
