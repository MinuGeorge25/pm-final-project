# Strategic Discovery Map (Module 1)

## Responses
- **Write one feature from the map that, if an engineer asked “why is this a priority for our 12-week roadmap?”, you honestly could not give a strategic answer for.:** Cash-flow control: something a BNPL user would want. The case never mentions it. What it does say is that Lena prefers money to leave her account only after she’s decided to keep the item, and “Pays after keeping” already covers that. I also have no evidence Lena would switch to a card for budgeting tools.
- **Write one feature that looks “correct” for the app but has zero strategic weight, you have no idea if it helps the company make money or whether a single user actually asked for it.:** The feature I couldn’t defend is “Merchant offers”, under MVP features.

It looks correct because it ticks the “merchant-first” box. I added it as my answer to the brief’s question about making the card more valuable to merchants. But I can’t say who would pay for it, whether merchants want to fund offers, or whether Lena would care. She picks whatever BNPL option appears at checkout, and nothing in the case suggests a discount would change that. I also can’t say whether it adds interchange or interest revenue, or whether it just gives margin away.

It would also be expensive for a friends-and-family test. It needs merchant integrations, offer logic and probably extra approval, all on a shared platform with limited capacity. And the test can only tell us whether people use the card, not whether offers were the reason.
- **Compare V3 to your Step 1 baseline. What changed, and is the output objectively better, did the AI get smarter, or did your added PM knowledge (JTBD, effort/impact, retention) force it to be useful?:** Partly. V3 is more useful as a sprint working document because it forces choices and shows where the team might disagree. The tensions are the best addition, especially card vs checkout BNPL, which the baseline never surfaced.

It is not objectively better in every respect. The impact/effort ratings are my guesses, with no user data or engineering estimates behind them, so the ranking looks more rigorous than it is. The baseline claimed less, and so was less likely to mislead. Several V3 leaves, like “Return hassle-free” and “Credit stress”, are plausible inferences, not findings from the case.

Did the AI get smarter?

No. It’s the same model, and nothing was learned between turns. Two things produced the difference:

Your prompt structure. Naming the five lenses, asking for ranking and asking for tensions told me what a useful output looks like. Left to itself, the baseline defaulted to summarising the case. That is the main driver, and it supports your point that PM framing forces usefulness.
Your critique turns. Asking me to find my weakest features pushed me to treat “Cash-flow control” and “Merchant offers” as unproven. V3’s “?” rating and cut features came from that, not from better built-in judgment. Without those turns, V3 would probably have carried the same unsupported items with better formatting.
- **Key takeaway: how does this prove the PM’s role is to think while the AI’s role is to execute?:** The PM owns the questions, the evidence and the decision. The AI generates options and drafts quickly, and it will present guesses with the same confidence as facts unless it’s pushed. So the PM’s role isn’t just thinking while the AI executes. It is deciding what to ask, challenging the answers, and turning “plausible” into “verified” through discovery. A good test is to ask of any AI output who would be accountable if it were wrong, and whether it has been checked against reality.
