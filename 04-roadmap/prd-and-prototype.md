# PRD & Prototype Sprint (Module 4)

## Pick & scope with MoSCoW
- **The “Now” feature I’m scoping (name + one-line core description):** B3, one balance view for card and regular pay later orders.Month-2 activity is the number to move: 51.0% for the Month 1 cohort and 57.1% for the Month 2 cohort, against a 62% target. The bet is that cards stop being “one more thing to check before payday” (N-02) once there is one total to look at, so more users stay active into month 2.
- **My finalized Must-Haves (after overriding the AI):** My finalized Must-Haves (after overriding)
One screen showing the card balance and the open pay later orders, labelled “Card” and “Pay later orders”. This is the feature itself.
One headline total across both. Acceptance criterion: it equals the sum of the figures on the two existing screens, so it never contradicts either.
No partial totals. If either part fails to load, show which one failed and no total. A silently wrong number is worse than today’s two screens, and it would recreate T-103’s “which total is real”. No retry button, custom messaging or auto-refresh in this sprint.
One entry point from the app home. A view nobody can find becomes the third thing to check (N-02).
- **What I demoted from Must → Should/Won’t, and why:** What I demoted, and why
Item	From → to	Why
Labelled breakdown of the total	Must → merged into must 1	The screen showing both parts already is the breakdown, so it isn’t a separate requirement.
“Total equals the existing screens”	Must → acceptance criterion of must 2	It is a test for the total, not a feature.
Plain wording for users with no open pay later orders	Must → Should	Lena holds both, and a zero amount is correct and enough for the first sprint. Nicer wording can wait.
Links from both existing screens to the new view	Must → Should	I have no data on where users start. One home entry makes the view findable.
Redefining what “owed” means (statement balance versus open orders)	New → Won’t	Show amounts exactly as the existing screens define them. Redefining touches terms and invites debate.

What stays at Should: event tracking for views is first in line. The primary metric (month-2 activity) already comes from existing cohort data, so it can be read without these events, but attribution is weaker without them.

## Generate your Simplified PRD
- **One thing my PRD makes explicit that a vague brief would have missed:** What the PRD makes explicit: the total disappears if either part fails to load.

A vague brief like “show one balance for the card and pay later orders” would get built to show whatever loaded, which means a partial total. A partial total quietly recreates the original misery of not knowing which total is real (T-103, N-07). The PRD closes that gap in four places:

FR4: the total exists on the page only when both parts have loaded. It’s checked in the page’s DOM, not hidden with CSS.
Smart Behaviors: it gives the exact outcome for each failure case. The failed row says “Couldn’t load”, the other row still shows its amount, and there is no total and no “How this adds up” link.
Decision Log: it records the rejected alternative, a partial total with an “incomplete” label, and why it lost.
Evals: the target is 0 totals shown while a part is loading or failed, across scenarios 3, 4, 5 and the 10-second timeout.

What to flag: this is a trade-off. When a load fails, Lena sees less than she could. The data pack also has no failure rates, so I can’t say how often this case will occur. That’s worth asking engineering before launch.

## Prompt-to-prototype sprint
- **Where did the prototype reveal a gap in my PRD logic? (what I had to update):** Gap in the PRD	What the build showed	Update needed
One tap to open the view (story 3, FR7)	The view is read-only and small enough to sit on the home page. One tap is still one more thing to do, which cuts against N-02, and you caught it when you asked for it inline.	Reduce the screens to two. Rewrite story 3 so the total is visible on arrival, and drop FR7. The time-on-task eval currently starts at “the first tap”, so it needs a new start point: page shown.
FR3 and “Adds up” can’t be tested in a prototype	Both amounts and the existing-screen figures come from one seed, so parity and the sum check can’t fail. My self-check proves only that the code matches its own seed, not that real amounts will match.	Move FR3 to a build-time integration test against real data. Limit the prototype’s accuracy eval to display logic, and decide whether screen 3 earns its place. It adds no information beyond the equation.
FR8 and FR5 contradict on timing	To show everything together, I withheld the loaded amount until both parts settled. If one part never answers, Lena sees placeholders for 10 seconds with nothing readable.	Choose between showing the loaded part early and shortening the timeout. The 10 seconds is my assumption, not from the data pack.
Negative amounts treated as “Couldn’t load”	A credit or overpayment may be valid, and the label would then claim a load failure that didn’t happen.	Ask finance and risk how credits should display. The data pack doesn’t cover it.
No number format beyond “412,50 €”	I had to pick one for larger amounts, using a thousands dot and a non-breaking space before €.	Add the format to FR1.
- **My prototype: save Claude's HTML as prototype.html in 04-roadmap/, open it in your browser, and add a screenshot:** https://github.com/MinuGeorge25/pm-final-project/blob/main/04-roadmap/prototype.html
