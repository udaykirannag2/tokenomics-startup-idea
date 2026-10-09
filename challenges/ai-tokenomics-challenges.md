# AI Tokenomics Challenges — Problem Catalog

Last updated: October 9, 2026.

**Purpose:** list every real problem in AI cost and value before choosing an idea. Nothing here is locked. Each challenge has evidence, the people who feel it, what exists today, and what is still missing. Update the "Validated?" column as interviews come in (see [interviews/interview-guide.md](../interviews/interview-guide.md)).

**Legend**
- **Evidence:** cited source. "Hypothesis" means it's plausible but not yet backed by data. Validate it in interviews.
- **Today's solutions:** rough judgment of how well existing tools cover it (Well covered / Partly / Poorly).
- **Validated?:** ✅ confirmed in 2+ interviews · ➖ mixed · ❌ not a real pain · blank = not yet asked.

## Who feels the pain

| Stakeholder | What they're asked | What keeps them up |
|---|---|---|
| CFO / FP&A | "Is AI paying off? What's next year's AI budget?" | Overruns, unclear ROI, margin hit |
| FinOps | "Who spent what, and why?" | Fragmented bills, allocation, no standards |
| CIO / CTO | "Which AI bets to scale or kill?" | Pilots stalling, board pressure, shadow AI |
| Engineering leaders / developers | "Are coding agents worth it?" | Agent bills, rate limits, pricing churn |
| Platform / AI engineering | "Make it cheaper without breaking quality" | Context bloat, model choice, loops |
| SaaS product and pricing leads | "How do we price AI features profitably?" | Heavy users, flat pricing, outcome pricing |
| Procurement | "Which contracts and commitments?" | Commit sizing, vendor lock-in, seat sprawl |
| CISO / security | "Where is AI running and on what data?" | Shadow AI, unmanaged agents |
| Business unit owners | "Prove my AI use case is worth it" | Attribution, baselines, ownership |

## A. Visibility and measurement

| ID | Challenge | Evidence | Who | Today's solutions | Gap | Validated? |
|---|---|---|---|---|---|---|
| A1 | AI spend is scattered across API providers, clouds, seats and AI features built into SaaS tools | Only 31% have accurate visibility into AI software spend ([Flexera](https://www.flexera.com/blog/ai/ai-spending-trends/)); 42% have only partial visibility ([KPMG via Consulting.us](https://www.consulting.us/news/amp/13628/as-ai-usage-matures-leaders-facing-pressure-to-show-roi)) | FinOps, CFO | Partly (Finout, Vantage, CloudZero, 1Password AI Spend) | AI features embedded in SaaS tools are still invisible | |
| A2 | No standard billing format for AI usage | Practitioners ask for FOCUS to cover AI workloads ([State of FinOps 2026](https://data.finops.org/)); Tokenomics Foundation formed June 2026 ([innobu](https://www.innobu.com/en/articles/ai-token-costs-finops-2026.html)) | FinOps, vendors | Poorly | Open-source converters and reference schemas | |
| A3 | Not enough detail: tokens, requests and GPU use aren't tracked at the level needed | Top requested FinOps tool feature ([Revenium](https://www.revenium.ai/post/the-2026-state-of-finops-report)) | FinOps, platform | Partly (Helicone, Langfuse, Portkey) | Tying the detail to teams, use cases and outcomes | |
| A4 | Tokens are only a small part of total AI cost | Tokens are 10–25% of Total Cost of AI ([FinOps Foundation](https://www.finops.org/insights/ai-spend-budget-busters/)); infrastructure adds 40–60% on top of inference ([DataStorage](https://datastorage.com/articles/ai-token-costs-what-enterprises-need-to-budget-for-in-2026/)) | CFO, CIO | Poorly | Per-use-case Total Cost of AI view | |
| A5 | Loops, retrieval and evals sit outside the token line | ([Finout](https://www.finout.io/blog/finops-tools-guide)) | Platform, FinOps | Poorly | Cost breakdown by agent step | |
| A6 | Shadow AI: unapproved tools, personal accounts, duplicate spend | 68% of employees use AI through personal accounts ([NHIMG](https://nhimg.org/articles/enterprise-ai-hidden-costs-are-reshaping-2026-budget-governance/)); 28% of AI spend is invisible to IT ([CloudNuro](https://www.cloudnuro.ai/blog/shadow-ai-statistics-2026-enterprise-trends-and-governance)) | CIO, CISO, procurement | Partly (SaaS management, security tools) | Combining cost and risk in one view | |

## B. Allocation and accountability

| ID | Challenge | Evidence | Who | Today's solutions | Gap | Validated? |
|---|---|---|---|---|---|---|
| B1 | Splitting shared model and platform costs across teams | #2 AI spend challenge ([State of FinOps 2026](https://data.finops.org/)); shared models have "no clean precedent" ([Opslyft](https://www.opslyft.com/blog/101-finops-statistics)) | FinOps, platform | Partly | Fair chargeback for shared capacity, caches and idle GPUs | |
| B2 | No clear owner for each AI use case | Leading orgs "name an owner before buying a tool" ([Harness](https://www.harness.io/state-of-ai-in-finops-2026)) | CIO, BU owners | Poorly | A registry of use cases with owners and budgets | |
| B3 | Chargeback becoming a board priority | 49% of enterprises call AI chargeback a board priority ([CloudNuro](https://www.cloudnuro.ai/blog/shadow-ai-statistics-2026-ciso-guide)) | CFO, FinOps | Partly | Chargeback that business units accept as fair | |

## C. Value and ROI

| ID | Challenge | Evidence | Who | Today's solutions | Gap | Validated? |
|---|---|---|---|---|---|---|
| C1 | Can't link AI spend to business outcomes | Only 7% have established ROI ([KPMG](https://www.consulting.us/news/amp/13628/as-ai-usage-matures-leaders-facing-pressure-to-show-roi)); 56% of CEOs can't show impact ([PwC via BERI](https://www.beri.net/article/openai-cfo-ai-scorecard-useful-intelligence-per-dollar-enterprise-roi-measurement-2026)) | CFO, CEO, BU owners | Poorly | Connect spend → AI outcome → business KPI | |
| C2 | Value is scattered and hard to attribute | Impact appears "as fragments scattered across budgets, productivity reports and business units" ([CFO Dive](https://www.cfodive.com/news/7-10-firms-report-ai-cost-overruns/825961/)); Deloitte recommends separating attributable from contributory value ([DistilINFO](https://distilinfo.com/2026/08/20/healthcare-cfos-ai-value-measurement/)) | CFO | Poorly | An attribution method finance will accept | |
| C3 | Dashboards show activity, not outcomes | Users and prompts are tracked, while boards want cost per transaction and margin ([BERI](https://www.beri.net/article/5-metrics-cfos-need-to-prove-ai-roi-in-2026)) | CFO, board | Poorly | Outcome-level metrics | |
| C4 | No baselines, so "before vs after" is guesswork | Deloitte's value ledger needs a baseline and a KPI owner ([DistilINFO](https://distilinfo.com/2026/08/20/healthcare-cfos-ai-value-measurement/)) | BU owners | Poorly | Capture baselines automatically | |
| C5 | Spend goes to personal productivity, not business change | 84% of finance AI spend targets individual productivity; 16% targets business outcomes ([RealAI, citing Gartner](https://www.realai.eu/insights/the-cfo-agenda-2026)) | CFO, CIO | Poorly | A portfolio view to move spend toward outcomes | |
| C6 | Pilots die before showing value | 42% abandoned most AI projects ([BERI](https://www.beri.net/article/ai-spending-roi-crisis-governance-2026)); 40% of agentic projects may be cancelled by 2027 ([Nosana, citing Gartner](https://nosana.com/blog/the-real-cost-of-ai-agents/)) | CIO | Poorly | Early kill-or-scale signals that weigh cost against value | |
| C7 | The CEO and CFO disagree on when AI pays off | 72% of CEOs expect returns in 6 months vs 45% of finance leaders ([Open Future Forum](https://openfutureforum.com/blog/why-companies-cant-prove-ai-roi-2026)) | CEO, CFO | Poorly | A shared, agreed value model | |

## D. Predictability and control

| ID | Challenge | Evidence | Who | Today's solutions | Gap | Validated? |
|---|---|---|---|---|---|---|
| D1 | AI budgets overrun | 79% overran ([arXiv](https://arxiv.org/html/2609.31622)); nearly 7 in 10 report cost overruns ([CFO Dive](https://www.cfodive.com/news/7-10-firms-report-ai-cost-overruns/825961/)) | CFO, FinOps | Partly (alerts) | Prevention, not just alerts | |
| D2 | Agent costs are unpredictable | Up to 30x cost variation for the same agent task ([Pickaxe, citing Stanford](https://pickaxe.co/post/ai-agent-cost-token-economics)) | Platform, FinOps | Poorly | Cost distributions and budgets for each agent run | |
| D3 | Runaway loops and retry storms | $47K loop over 11 days ([Coommit](https://coommit.com/blog/ai-agent-costs-2026-bill-shock)); $72K overnight retry loop ([Agenticism](https://www.agenticism.co/post/the-hidden-tax-on-your-ai-agents-how-retry-loops-are-quietly-draining-up-to-60-of-your-ai-budget)) | Platform, eng leaders | Partly (gateway rate limits) | Loop detection that understands agents, plus kill switches | |
| D4 | Tokens per request keep rising | Median tokens per request doubled year over year ([Agenticism, citing Datadog](https://www.agenticism.co/post/the-hidden-tax-on-your-ai-agents-how-retry-loops-are-quietly-draining-up-to-60-of-your-ai-budget)) | Platform | Poorly | Alerts when token use per task creeps up | |
| D5 | Forecasting misses business events | Launches, model retirements, demand spikes and acquisitions blow budgets ([FinOps Foundation](https://www.finops.org/insights/ai-spend-budget-busters/)) | FP&A | Poorly | Forecasting built around business events | |
| D6 | AI has to be paid for with savings found elsewhere | ([State of FinOps 2026](https://data.finops.org/)) | FinOps, CFO | Partly | Tie optimization savings to the AI budget they fund | |

## E. Engineering efficiency (waste)

| ID | Challenge | Evidence | Who | Today's solutions | Gap | Validated? |
|---|---|---|---|---|---|---|
| E1 | Context bloat and tool overhead | A tool call adds 500–2,000 tokens ([MindStudio](https://www.mindstudio.ai/blog/ai-token-cost-crisis-enterprise)); the tool-use system prompt adds 290–800 tokens ([Sakara Digital](https://sakaradigital.com/blog/enterprise-ai-token-consumption-cost/)) | Platform, devs | Partly (memory layers, e.g. Engram) | Waste findings tied to specific steps, with fixes | |
| E2 | Using an expensive model where a cheaper one would do | Tiered setups pay $2.31 vs $18.40 per million tokens ([DataStorage](https://datastorage.com/articles/ai-token-costs-what-enterprises-need-to-budget-for-in-2026/)) | Platform | Well covered for routing (OpenRouter, gateways) | Evidence per workflow that a cheaper model is safe | |
| E3 | Prompt caching underused | Cached input is about 90% cheaper ([Sesame Disk](https://sesamedisk.com/saas-unit-economics-explained/)) | Platform | Partly | Detecting why caching breaks and fixing it | |
| E4 | Retry waste ("token debt") | Passing failure context on retries cuts usage 40–60% ([Agenticism](https://www.agenticism.co/post/the-hidden-tax-on-your-ai-agents-how-retry-loops-are-quietly-draining-up-to-60-of-your-ai-budget)); Prismatics Lite repeats fell from 6/6 to 1/6 questions | Platform | Poorly | Profiler that flags retries | |
| E5 | Cost is checked after launch, not during development | Leading orgs treat AI cost "as a development-time discipline" ([Harness](https://www.harness.io/state-of-ai-in-finops-2026)) | Eng leaders | Poorly | Cost regression checks in CI | |
| E6 | Price drops aren't captured | Blended cost fell 67% in a year ([DataStorage](https://datastorage.com/articles/ai-token-costs-what-enterprises-need-to-budget-for-in-2026/)) | Platform | Poorly | Re-test and migrate when new models ship | |

## F. Coding-agent economics

| ID | Challenge | Evidence | Who | Today's solutions | Gap | Validated? |
|---|---|---|---|---|---|---|
| F1 | Coding-agent spend is a new, fast-growing line item | Separate cost layer ([PointFive](https://www.pointfive.co/guides/finops-tools-for-managing-ai-costs)); ~$13 per developer per active day, up from ~$6 ([CloudZero](https://www.cloudzero.com/blog/ai-coding-tools-cost/)) | Eng leaders, FinOps | Poorly | Cost per merged PR or per feature shipped | |
| F2 | Vendor pricing changes often and limits are opaque | Cursor's 2025 pricing change led to an apology and refunds ([LeadDev](https://leaddev.com/ai/the-great-ai-coding-assistant-bait-and-switch)); Anthropic publishes no numeric limits ([CatDoes](https://catdoes.com/blog/claude-vs-cursor)); Copilot moved to AI Credits in June 2026 ([CloudZero](https://www.cloudzero.com/blog/ai-coding-tools-cost/)) | Devs, procurement | Poorly | Plan comparison and right-sizing across tools | |
| F3 | Same task, very different cost by model | ~$0.50 vs ~$7 per task at similar accuracy ([Developer Tech](https://www.developer-tech.com/news/ai-coding-agents-cursor-anthropic-alibaba-price-floor-2026/)) | Eng leaders | Partly | Matching model to task inside coding tools | |
| F4 | Productivity value per developer unproven | Hypothesis: links to C1 and C3 | Eng leaders, CFO | Partly (developer productivity analytics) | Joining cost data with delivery data | |

## G. Buying, contracts and infrastructure

| ID | Challenge | Evidence | Who | Today's solutions | Gap | Validated? |
|---|---|---|---|---|---|---|
| G1 | Hard to size reserved capacity and commitments (Bedrock Provisioned Throughput, Azure reserved capacity (PTU), enterprise commits) | Hypothesis | Procurement, FinOps | Poorly | Automated commitment advice | |
| G2 | Self-host vs API decision | Crossover often around $300K/month ([Monetizely](https://www.getmonetizely.com/articles/the-economics-of-ai-first-b2b-saas-in-2026-margins-pricing-models-and-profitability)) | CTO | Poorly | Total-cost modeling per workload | |
| G3 | Billing errors and reconciliation | Hypothesis | FinOps | Poorly | Invoice auditing | |
| G4 | Vendor lock-in and switching costs | Hypothesis | CTO, procurement | Partly (gateways) | Estimating what it would cost to switch | |

## H. SaaS vendor monetization (selling AI)

| ID | Challenge | Evidence | Who | Today's solutions | Gap | Validated? |
|---|---|---|---|---|---|---|
| H1 | AI gross margins are compressed | ~52% average margin; inference ~23% of revenue ([B2B Notes](https://b2bnotes.com/blog/the-ai-margin-squeeze-how-surging-inference-costs-are-quietly-rewriting-b2b-saas-pricing-cogs-and-the-rule-of-40-in-2026)) | CFO, product | Partly | Margin by feature and by customer | |
| H2 | Flat pricing with variable costs; heavy users lose money | ([Suhag Al Amin](https://suhag.me/blog/ai-saas-pricing-margin-losing-money)) | Pricing | Partly (billing platforms) | Flag heavy users and simulate price changes | |
| H3 | Outcome-based pricing is hard; partial failures are unsolved | Sierra bills per resolution; Devin per compute unit ([Startup Fortune](https://startupfortune.com/how-to-price-an-ai-agent-when-it-fails-a-task-halfway-through/)) | Pricing, product | Partly | Outcome verification and partial billing | |
| H4 | Customer bill shock hurts trust | Cursor users saw bills jump from ~$100/month to $20–30/day ([LeadDev](https://leaddev.com/ai/the-great-ai-coding-assistant-bait-and-switch)) | Product, support | Poorly | Spend previews and caps visible to customers | |

## I. Governance and risk

| ID | Challenge | Evidence | Who | Today's solutions | Gap | Validated? |
|---|---|---|---|---|---|---|
| I1 | Shadow AI raises breach costs | +$670K average breach cost ([Vectra](https://www.vectra.ai/topics/shadow-ai)) | CISO | Well covered by security vendors | Combining cost and risk | |
| I2 | Agents running without IT oversight | 80% of AI tools run without IT oversight ([The Outpost](https://theoutpost.ai/news-story/shadow-ai-crisis-80-of-enterprise-ai-tools-operate-without-it-oversight-costing-670-k-per-breach-30550/)) | CISO, CIO | Partly | A combined agent inventory, budget and access view | |

## J. Organization and skills

| ID | Challenge | Evidence | Who | Today's solutions | Gap | Validated? |
|---|---|---|---|---|---|---|
| J1 | AI cost management is the #1 skill gap | ([State of FinOps 2026](https://data.finops.org/)) | FinOps | Poorly (courses) | Training plus tooling (your course) | |
| J2 | Finance doesn't lead AI value decisions | Only 26% of CFOs lead value-driver discussions ([CFO.com](https://www.cfo.com/news/myles-corson-ey-survey-says-cfo-need-new-metrics-automation-ai-finance/822453/)) | CFO | Poorly | A shared language between engineering and finance | |
| J3 | Old metrics don't fit AI | 71% say traditional metrics fall short ([CFO.com](https://www.cfo.com/news/myles-corson-ey-survey-says-cfo-need-new-metrics-automation-ai-finance/822453/)) | CFO | Poorly | New AI unit metrics | |

## Patterns across the challenges

1. **Measurement is broken from end to end.** Problems run all along the chain: spend you can't see (A), costs nobody owns (B), and value you can't show (C). Most tools fix one part.
2. **Agents make everything unpredictable** (D2, D3, D4, E4). Cloud-era budgeting assumed steady, predictable usage.
3. **Engineering waste is real but crowded at the routing layer** (E2). The open space is diagnosing waste (E1, E4, E5).
4. **Coding agents are a fresh, underserved spend category** (F1–F4), with frequent pricing churn.
5. **SaaS companies feel the problem twice.** They buy AI (C1) and they sell AI features (H1–H4).
6. **Standards are still forming** (A2), so there's room to shape them.

## Opportunity scoring (initial, to update after interviews)

Score each 1–5. Pain = how much it hurts; WTP = willingness to pay; Open = how uncrowded; Fit = your ability to win; Wedge = can start open-source or self-serve.

| Cluster | Pain | WTP | Open | Fit | Wedge | Total |
|---|---|---|---|---|---|---|
| C. Value and ROI (C1–C7) | 5 | 4 | 4 | 4 | 2 | 19 |
| D. Predictability and control (D1–D6) | 4 | 4 | 3 | 4 | 4 | 19 |
| E. Engineering waste (E1, E3–E6) | 3 | 3 | 3 | 4 | 5 | 18 |
| F. Coding-agent economics (F1–F4) | 4 | 3 | 4 | 4 | 5 | 20 |
| A. Visibility (A1–A6) | 4 | 4 | 2 | 4 | 3 | 17 |
| B. Allocation (B1–B3) | 4 | 4 | 3 | 5 | 2 | 18 |
| H. SaaS monetization (H1–H4) | 4 | 4 | 3 | 3 | 2 | 16 |
| G. Buying and contracts (G1–G4) | 3 | 4 | 4 | 5 | 2 | 18 |
| I. Governance and risk (I1–I2) | 4 | 4 | 1 | 2 | 2 | 13 |
| J. Organization and skills (J1–J3) | 3 | 2 | 3 | 5 | 4 | 17 |

These are first-pass judgments. Re-score after 10–15 interviews.

## From challenges to ideas

See [ideas/ai-tokenomics-startup-ideas.md](../ideas/ai-tokenomics-startup-ideas.md) for the idea list. Candidate links:

| Challenge(s) | Candidate ideas (numbers from the ideas doc) |
|---|---|
| C1–C4, B2 | #10 Cost-per-outcome reporting, #12 Total Cost of AI ledger |
| D2–D4, E1, E4 | #1 Agent cost profiler |
| F1, F3, F4 | #2 Cost per merged PR |
| E3 | #4 Prompt-cache optimizer |
| E5 | #5 Token regression testing in CI |
| E6 | #16 Model migration autopilot |
| A2, A3 | #9 FOCUS-for-AI adapter |
| B1, B3 | #11 Shared-model chargeback engine |
| D5 | #14 Scenario-based budget forecasting |
| G1 | #15 AI commitment optimizer |
| G2 | #17 Self-host vs API advisor |
| H1, H2 | #18 AI margin copilot |
| H3 | #19 Agent billing for partial outcomes |
| G3 | #20 AI invoice auditor |
| F2, H4 | New: cross-tool plan right-sizing and customer-facing spend previews |
| J1–J3 | Course and content as a distribution channel |
