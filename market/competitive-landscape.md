# AI Economics Competitive Landscape

Tracker of companies near the idea of **mapping AI spend to revenue, per customer and product, for SaaS and AI companies, and connecting it to finance**. Facts come from each company's own site or docs, read on 2026-10-23. Re-verify before relying on a claim; this market changes monthly.

Legend: ✅ stated on their site · ◐ partial or limited · — not stated (not proof they lack it) · n.a. could not confirm

## Key takeaways

1. **Our idea isn't a single-competitor problem.** At least four companies already show margin per customer: Paid.ai, Revenium, Amberflo and CloudZero. Each comes at it from a different side.
2. **Paid.ai does attribute cost per customer and per agent, but only through its SDK.** Cost traces are tagged with a customer and product ID, and "cost-attributed signals" tie AI calls to agent actions ([Paid docs](https://docs.paid.ai/documentation/getting-started/cost-attributed-signals)). If a call isn't wrapped in Paid's tracing context, it's recorded with no customer attached ([Paid docs](https://docs.paid.ai/documentation/getting-started/cost-traces)). Its docs say nothing about shared infrastructure costs or reconciling to provider invoices.
3. **Ascerta (formerly Pay-i) is now well funded on the internal-enterprise side.** It measures true cost, including discounts and hidden fees, and ROI per use case for CIOs and CFOs, but not revenue per customer. See its profile.
4. **Amberflo is the closest match we hadn't met.** It claims gateway connectors with no code changes, attribution down to customer, tenant, agent and workflow, margin per customer, and credit billing in one product ([Amberflo](https://amberflo.io/platform)).
5. **Every tool starts from a different source of data:**
   - Gateways and observability tools start from requests.
   - Paid, Revenium and Stigg start from an SDK in the app.
   - CloudZero, Vantage and Finout start from the cloud bill.
   - Billing tools start from usage events.

   None of them clearly joins all four into one ledger the finance team signs off on.
6. **Finance and ERP integration is weakest among the AI-economics tools.** The billing tools have it (Orb, Solvimon and Lago all integrate with NetSuite). The AI-cost tools mostly stop at a warehouse export or a dashboard.

## White space to validate

| Gap | Why it may be open | Closest threat |
|---|---|---|
| AI gross margin per customer, reconciled to real invoices and committed discounts | Gateways price requests from list rates; Solo's own docs say spend is an estimate that may not match the invoice. Ascerta handles discounts and hidden fees, but for internal use cases, not customer margin | CloudZero, Revenium, Ascerta |
| Allocating shared AI costs (GPUs, vector DBs, evaluations, embeddings) to tenants | SDK and gateway tools see calls, not shared infrastructure | CloudZero, Finout |
| Credits ↔ cost ↔ revenue in one ledger for SaaS with existing billing (Stripe, Zuora, Chargebee) | Paid and Stigg want to own the billing or runtime; established SaaS companies won't replace billing | Amberflo, Stigg |
| Finance-grade output: AI COGS posted to the GL, credit liability exposure, period close | AI-economics tools serve dashboards to engineering and product | Orb or Solvimon adding cost data |

## Tracking log

| Date | Company | Change or signal | Source |
|---|---|---|---|
| 2026-10 | TrueFoundry, Solo.io, Revenium, Stigg | Met at AI conference; all show AI cost features | Conference |
| 2026-10-23 | All | Initial landscape built | This page |
| 2026-09-30 | Ascerta | Pay-i renamed Ascerta; $18M Series A led by Dell Technologies Capital; expanded from AI cost to enterprise AI value and ROI | [Ascerta press release](https://ascerta.com/resources/press/ascerta-raises-18m-series-a) |

## How the market is layered

| Layer | What it answers | Buyer | Companies |
|---|---|---|---|
| AI gateways | What did each request cost, and can I cap it? | Platform engineering | TrueFoundry, Solo.io, Portkey, LiteLLM, Kong |
| LLM observability | What happened in each call, and what did it cost? | AI engineers | Helicone, Langfuse |
| AI economics | Is each customer, agent or workflow profitable or worth it? | Eng + product + finance | Revenium, Paid.ai, Amberflo, Ascerta (formerly Pay-i) |
| Cloud FinOps extending to AI | Where did the cloud and AI bill go? | FinOps + finance | CloudZero, Vantage, Finout |
| Monetization and billing | How do I charge for usage and credits, and book revenue? | Product, RevOps, finance | Stigg, Metronome, Orb, Solvimon, Lago, Flexprice |

## Capability matrix

Columns map to the idea: capture cost without code changes, attribute it per customer and per agent, connect it to revenue and margin, handle credits and billing, measure outcomes, integrate with finance systems, and reconcile to the real invoice.

| Company | Layer | Met at conference | No-code capture | Per customer / tenant | Per agent / workflow | Revenue & margin | Credits & billing | Outcome / ROI | Finance / ERP | Reconciles to invoice | Threat |
|---|---|---|---|---|---|---|---|---|---|---|---|
| TrueFoundry | AI gateways | Yes | ✅ proxy | ✅ metadata | ◐ | — | — | — | — | — | Low-Medium |
| Solo.io agentgateway | AI gateways | Yes | ✅ proxy | ◐ virtual keys | ◐ | — | — | — | — | — (estimate) | Low |
| Portkey | AI gateways |  | ✅ proxy | ◐ user/metadata | — | — | — | — | — | — | Low-Medium |
| LiteLLM | AI gateways |  | ✅ proxy | ✅ tags/teams | ✅ | — | ◐ chargeback | — | — | — | Low-Medium |
| Kong AI Gateway | AI gateways |  | ✅ proxy | ✅ | ✅ | ◐ | ◐ metering | — | — | — | Low-Medium |
| Helicone | LLM observability |  | ◐ proxy/SDK | ◐ user | — | — | — | — | — | — | Low |
| Langfuse | LLM observability |  | ◐ SDK/OTEL | ◐ user | ◐ traces | — | — | ◐ quality evals | — | — | Low |
| Revenium | AI economics | Yes | ◐ SDK/API | ✅ | ✅ | ✅ | ◐ | ✅ | ◐ warehouse/ERP (Ent.) | ✅ billed vs metered | High |
| Paid.ai | AI economics |  | — SDK required | ✅ | ✅ signals | ✅ | ✅ | ✅ value receipts | ◐ Xero, webhooks | — | High |
| Amberflo | AI economics |  | ✅ gateway connectors | ✅ | ✅ | ✅ | ✅ | ◐ | ◐ rev rec workflows | — | High |
| Ascerta (formerly Pay-i) | AI economics |  | ◐ connectors to AI tools | — (internal use case, team, person) | ✅ per run | — | — | ✅ KPIs | — | ✅ discounts, hidden fees | High (internal) / Medium (SaaS margin) |
| CloudZero | Cloud FinOps extending to AI |  | ✅ billing data | ✅ | ◐ | ✅ | — | ✅ | — | ✅ invoices | Medium-High |
| Vantage | Cloud FinOps extending to AI |  | ✅ billing data | ✅ | — | ◐ unit costs | — | — | ◐ Ramp, warehouse | ◐ bill-based | Medium |
| Finout | Cloud FinOps extending to AI |  | ✅ billing data | ✅ | — | ◐ unit costs | — | ◐ | — | ◐ bill-based | Medium |
| Stigg | Monetization and usage billing | Yes | ◐ SDK wrapper | ✅ | ✅ | ◐ cost-plus | ✅ | — | ◐ Stripe/Zuora/SFDC, warehouse | — | Medium |
| Metronome | Monetization and usage billing |  | — events | ✅ usage | — | ◐ | ✅ | — | ◐ Stripe, CRM/ERP sync | — | Medium |
| Orb | Monetization and usage billing |  | — events | ✅ usage | — | ◐ revenue only | ✅ | — | ✅ NetSuite, rev rec | — | Medium |
| Solvimon | Monetization and usage billing |  | — events | ◐ | ◐ | — | ✅ | ◐ outcome pricing | ✅ NetSuite, Xero, rev rec | — | Medium |
| Lago | Monetization and usage billing |  | — events | ◐ usage | — | — | ✅ | — | ✅ NetSuite, QuickBooks | — | Low |
| Flexprice | Monetization and usage billing |  | — events | ◐ usage | — | — | ✅ | — | ◐ Stripe, HubSpot | — | Low |

## Company profiles

### Layer 1 — AI gateways (control traffic, cost per request)

#### TrueFoundry (met at conference)

- **What they do:** Cloud-agnostic enterprise AI platform with an AI Gateway for model and tool access, governance, observability, and cost tracking, plus deployment and model-serving capabilities on customers’ infrastructure.
- **Buyer:** Enterprise platform engineering and ML platform teams, data science and AI engineering teams, and technology leaders standardizing AI infrastructure.
- **USP (their claim):** TrueFoundry claims to combine an enterprise AI Gateway, governance and observability, and AI deployment across cloud, private, and on-prem environments in one modular platform.
- **Cost attribution:** Calculates per-request costs at the AI Gateway using usage and configured model prices. Attributes spend by user, team, virtual account, model, and custom metadata, including application, environment, customer, or cost center. Metadata can be injected automatically; no application instrumentation is required.
- **Revenue and margin:** not stated
- **Credits and billing:** Supports model usage cost calculation, budget limits, quotas, and cost-data exports. Offers 30,000 free AI Gateway requests per month; invoicing, customer credits, and usage-based billing for a vendor’s customers are not stated.
- **Finance integration:** not stated
- **Outcome / ROI:** Reports cost-saving estimates for prompt caching, semantic caching, and routing, and promotes cost optimization. Per-customer or per-product revenue, margin, and business-outcome measurement is not stated.
- **Pricing:** AI Gateway: free for up to 30,000 requests per month and 3 seats; paid pricing is not stated.
- **Threat to our idea:** Low-Medium
- **Sources:** [truefoundry.com/ai-gateway](https://www.truefoundry.com/ai-gateway), [truefoundry.com/docs/ai-gateway/cost-tracking](https://www.truefoundry.com/docs/ai-gateway/cost-tracking), [truefoundry.com/docs/platform/overview](https://www.truefoundry.com/docs/platform/overview), [truefoundry.com/llm-info](https://www.truefoundry.com/llm-info), [truefoundry.com/model-serving](https://www.truefoundry.com/model-serving)

#### Solo.io agentgateway (met at conference)

- **What they do:** Solo.io agentgateway is an open-source, Rust-based gateway for LLM, MCP, A2A, and inference traffic, providing routing, security, governance, observability, and cost controls. Solo Enterprise adds production features and support.
- **Buyer:** Platform and FinOps teams, plus organizations running production AI and agentic workloads; enterprise buyers seeking secure, governed cloud-native connectivity.
- **USP (their claim):** Solo.io claims agentgateway is purpose-built for AI protocols and stateful agent traffic, combining native MCP/A2A support with a high-performance Rust data plane and vendor-neutral open governance.
- **Cost attribution:** Enterprise cost dashboard estimates spend from token counts and configured per-token prices, using gateway traces. Attributes by provider, model, group, user, virtual key, and custom dimensions; virtual-key metadata supplies fields such as group and user. No cloud-bill ingestion stated.
- **Revenue and margin:** not stated
- **Credits and billing:** Supports token/request-based limits and budgets, with live usage and virtual API keys. No credits, invoicing, outcome pricing, or customer usage billing stated.
- **Finance integration:** not stated
- **Outcome / ROI:** not stated
- **Pricing:** not stated
- **Threat to our idea:** Low
- **Sources:** [docs.solo.io/agentgateway/2026.5.x/about/overview](https://docs.solo.io/agentgateway/2026.5.x/about/overview/), [docs.solo.io/agentgateway/kubernetes/latest/documentation/llm/cost-controls/dashboard](https://docs.solo.io/agentgateway/kubernetes/latest/documentation/llm/cost-controls/dashboard/), [solo.io/products/agentgateway](https://www.solo.io/products/agentgateway)

#### Portkey

- **What they do:** AI production platform combining an AI gateway, observability, guardrails, governance, and prompt management. Provides unified access to LLMs, routing, caching, monitoring, and MCP gateway capabilities.
- **Buyer:** GenAI developers and AI teams building or operating production AI; enterprise organizations needing centralized governance, security, and control.
- **USP (their claim):** Portkey claims to provide a unified, enterprise-ready production stack for AI, combining gateway access, observability, governance, security, and prompt management.
- **Cost attribution:** Tracks costs per use case; supports automatic user attribution and custom metadata. Gateway records request costs, with logs, traces, filters, and dashboards. Attribution is captured through Portkey’s gateway and API integrations.
- **Revenue and margin:** not stated
- **Credits and billing:** Plans have monthly recorded-log or request limits, with published request overages on paid plans. Credits, invoicing, and outcome-based pricing are not stated.
- **Finance integration:** Data export to data lakes is listed for enterprise plans; ERP, accounting, revenue-recognition, CRM, and billing integrations are not stated.
- **Outcome / ROI:** Promotes cost savings from caching and cites customer savings, but dedicated outcome or ROI measurement support is not stated.
- **Pricing:** Free Forever plan; Production is $49/month with $9 per additional 100,000 requests; Enterprise has custom pricing. Enterprise pricing includes custom retention and support.
- **Threat to our idea:** Low-Medium
- **Sources:** [portkey.ai](https://portkey.ai/), [portkey.ai/features/ai-gateway](https://portkey.ai/features/ai-gateway), [portkey.ai/pricing](https://portkey.ai/pricing)

#### LiteLLM

- **What they do:** Open-source, self-hosted AI gateway and Python SDK for routing LLM, agent, and MCP requests through a unified API, with access controls, budgets, cost tracking, and guardrails.
- **Buyer:** Platform and AI infrastructure teams operating AI in production; also developers and regulated companies needing self-hosted or air-gapped deployment.
- **USP (their claim):** LiteLLM claims to combine self-hosted governance and cost controls for models, agents, and MCP in one open-source gateway, with no per-token fee.
- **Cost attribution:** Tracks request costs and usage by key, user, team, organization, model, tool, agent, MCP, and tags; supports enterprise chargeback. Captured through the gateway and SDK cost tracking/callbacks. Billing-data or cloud-bill ingestion is not stated.
- **Revenue and margin:** not stated
- **Credits and billing:** Supports usage limits, budgets, and internal team/business-unit chargeback. No credits, customer invoicing, or outcome-based pricing support is stated.
- **Finance integration:** not stated
- **Outcome / ROI:** Promotes cost optimization and ROI through model routing, caching, and prompt compression; cites AT&T coding-cost reductions, but per-customer or product outcome measurement is not stated.
- **Pricing:** Open-source gateway and SDK are free. Enterprise is an annual license priced by request capacity, installation architecture, and support; never per token. A 30-day trial is offered.
- **Threat to our idea:** Low-Medium
- **Sources:** [docs.litellm.ai/docs](https://docs.litellm.ai/docs/), [litellm.ai](https://www.litellm.ai/), [litellm.ai/about](https://www.litellm.ai/about)

#### Kong AI Gateway

- **What they do:** Kong AI Gateway governs LLM, MCP, and agent-to-agent traffic, providing routing, security, observability, quotas, and token-cost controls through a unified gateway.
- **Buyer:** Not stated; the product is presented for organizations and teams governing AI traffic at enterprise scale.
- **USP (their claim):** Kong’s claimed differentiator is one enterprise-ready gateway for governing API, LLM, MCP, and agent-to-agent traffic.
- **Cost attribution:** Tracks AI consumption, tool usage, and token spend; homepage says costs can be attributed to users, teams, applications, agents, projects, or customers. Gateway traffic and telemetry are described; specific capture integrations are not stated.
- **Revenue and margin:** Kong promotes API and AI monetization and improving business margins, but does not state that it connects spend to revenue or margin per customer or product.
- **Credits and billing:** Supports user, model, and time-bound usage quotas, gateway enforcement, and showback/chargeback. The homepage describes usage-based metering and billing, entitlements, and runtime limits. A $100k credits offer is advertised.
- **Finance integration:** not stated
- **Outcome / ROI:** Supports cost monitoring and optimization; the homepage says it measures savings and identifies optimization opportunities. Specific outcome or ROI measurement is not stated.
- **Pricing:** not stated; the pages advertise an offer of $100k credits and 50% off AI Gateway without specifying standard pricing.
- **Threat to our idea:** Low-Medium
- **Sources:** [konghq.com/products/kong-ai-gateway](https://konghq.com/products/kong-ai-gateway), [konghq.com](https://www.konghq.com/)

### Layer 2 — LLM observability (traces, cost per call)

#### Helicone

- **What they do:** Open-source LLM observability and AI gateway platform for monitoring, routing, debugging, evaluating, experimenting with, and managing prompts for LLM applications.
- **Buyer:** Developers and teams building production LLM applications; the supplied comparison also describes developers and analysts.
- **USP (their claim):** Helicone claims to combine an AI gateway with full LLM observability, including automatic routing and fallbacks, in one open-source platform.
- **Cost attribution:** Tracks request costs and supports breakdowns by user, feature, or custom dimension. Requests can flow through its gateway or be logged via SDK/proxy; pages do not mention OpenTelemetry or cloud-bill ingestion.
- **Revenue and margin:** not stated
- **Credits and billing:** Gateway credits let customers access 100+ providers; Helicone says it charges 0% markup and passes through provider prices. Customers may instead use their own provider keys. Credits are not described as customer-facing usage billing or invoicing.
- **Finance integration:** not stated
- **Outcome / ROI:** Evaluators and experiments assess LLM output quality and measure prompt changes against production evaluators; business ROI or financial outcome measurement is not stated.
- **Pricing:** Platform overview comparison lists 0% markup / $20 per seat; gateway credits are described as having 0% markup. A 2024 blog says the first 10,000 requests per month are free.
- **Threat to our idea:** Low
- **Sources:** [docs.helicone.ai/getting-started/platform-overview](https://docs.helicone.ai/getting-started/platform-overview), [helicone.ai/blog/best-langsmith-alternatives](https://www.helicone.ai/blog/best-langsmith-alternatives), [helicone.ai/blog/introducing-helicone-v2](https://www.helicone.ai/blog/introducing-helicone-v2)

#### Langfuse

- **What they do:** Open-source AI engineering platform for tracing and observing LLM applications, managing prompts, evaluating outputs, running experiments, and monitoring cost, latency, and quality.
- **Buyer:** AI application and agent engineering teams building, debugging, and improving LLM applications.
- **USP (their claim):** Langfuse claims to offer an integrated, open-source platform for the full AI engineering cycle, with OpenTelemetry support, broad integrations, and self-hosting.
- **Cost attribution:** Tracks cost and token usage in traces; users can be identified with userId, and traces can be filtered by user, session, or custom metadata. Data can be captured via native SDKs, OpenTelemetry, integrations, or an LLM gateway. Customer, tenant, product, and team attribution are not stated.
- **Revenue and margin:** not stated
- **Credits and billing:** not stated
- **Finance integration:** not stated
- **Outcome / ROI:** Measures output quality through evaluations, scores, feedback, and experiments; supports monitoring quality alongside cost and latency. Business ROI or financial outcome measurement is not stated.
- **Pricing:** Free tier: 50,000 observations per month with no credit card required; self-hosting is described as free. Paid pricing is not stated.
- **Threat to our idea:** Low
- **Sources:** [langfuse.com](https://langfuse.com/), [langfuse.com/docs](https://langfuse.com/docs), [langfuse.com/docs/observability/overview](https://langfuse.com/docs/observability/overview)

### Layer 3 — AI economics (cost to value, margin, ROI)

#### Revenium (met at conference)

- **What they do:** AI economic control and observability platform that tracks AI transactions, attributes costs, analyzes ROI and margins, and enforces spending limits.
- **Buyer:** Engineering, finance, and product teams at organizations managing AI usage; aimed at engineering and finance leaders.
- **USP (their claim):** Revenium claims to be an economic control system that attributes AI costs to business dimensions and outcomes, then helps teams analyze profitability and enforce limits before losses occur.
- **Cost attribution:** Attributes costs by customer, product, feature, workflow, team, agent, model, and task. Metering uses writes to Revenium’s API (one transaction per tracked event); pages also describe SDK instrumentation, provider support, and connecting LLM providers.
- **Revenue and margin:** Connects AI costs to revenue, customer and product-tier profitability, workflow ROI, and margins. ROI comparisons require reported outcomes and monetization data; margins can be analyzed by customer, feature, workflow, and product tier.
- **Credits and billing:** Supports transaction metering and plan overages; pricing lists 100K free transactions, 350K/month on Growth, and 1M+ on Enterprise. Outcome and ROI measurement is described, but customer credits, invoicing, and outcome-based billing are not stated.
- **Finance integration:** Enterprise integrations include Snowflake, Datadog, Splunk, or ERP. The product also says it connects cost to revenue already billed and to the billing stack; named accounting, CRM, or billing integrations are not stated.
- **Outcome / ROI:** ROI dashboards compare estimated revenue from successful conversions with AI compute costs; reported outcomes feed conversion and cost-avoidance funnels. Also supports ROI and cost-per-unit comparisons, including manual-work baselines and customer/workflow margins.
- **Pricing:** Free Observe: 100K transactions/month. Growth: 350K/month, $750 per 500K-block overage in the comparison table (FAQ states $1.50 per 1,000 transactions). Enterprise: 1M+ transactions/month, custom pricing. Growth price itself is not stated.
- **Threat to our idea:** High
- **Sources:** [docs.revenium.io/track-and-control-costs/analyze-roi-and-unit-economics](https://docs.revenium.io/track-and-control-costs/analyze-roi-and-unit-economics), [revenium.ai](https://www.revenium.ai/), [revenium.ai/post/price-ai-agents-by-outcome](https://www.revenium.ai/post/price-ai-agents-by-outcome), [revenium.ai/pricing](https://www.revenium.ai/pricing)

#### Paid.ai

- **What they do:** AI-agent monetization platform for metering usage, configuring pricing, billing customers, tracking costs and demonstrating delivered value.
- **Buyer:** AI companies and software businesses selling AI-agent products; also businesses tracking costs and margins for internal AI operations.
- **USP (their claim):** Paid positions itself as agent-native monetization infrastructure that connects agent activity and costs to flexible pricing, billing, and auditable customer value.
- **Cost attribution:** Attributes costs to customers and products through external IDs; links costs to agent actions/signals and can track user-level credit use. Captured through SDK auto-instrumentation/tracing, OpenTelemetry-based SDKs, or manual signals.
- **Revenue and margin:** Tracks costs and margins, including real-time margin monitoring and identifying profitable agents. Cost attribution can link AI costs to customer/product signals; explicit realized revenue or profit attribution by customer/product is not stated.
- **Credits and billing:** Supports prepaid credits, credit consumption (including quantities and user-level balances), usage-based and outcome-based pricing, invoicing, payments, and automated billing.
- **Finance integration:** Xero sync, API and billing-event webhooks for sending finalized invoices to an existing accounting or ERP stack. Claims support for ERPs, CRMs, CPQs, and billing systems generally.
- **Outcome / ROI:** Supports value and ROI reporting through customer-facing usage dashboards, value receipts comparing savings with human work, and evidence linking billing line items to underlying events.
- **Pricing:** AI-agent cost tracking is free for the first year via self-serve signup; billing automation requires a custom package through sales.
- **Threat to our idea:** High
- **Sources:** [docs.paid.ai/documentation/getting-started/cost-attributed-signals](https://docs.paid.ai/documentation/getting-started/cost-attributed-signals), [docs.paid.ai/documentation/getting-started/cost-traces](https://docs.paid.ai/documentation/getting-started/cost-traces), [paid.ai](https://paid.ai/), [paid.ai/products/bill](https://paid.ai/products/bill), [preview.paid.ai](https://preview.paid.ai/)

#### Amberflo

- **What they do:** AI cost intelligence, governance, metering, chargebacks, and customer billing in one platform; tracks AI usage and costs and connects them to pricing, invoices, and margin analysis.
- **Buyer:** AI-native product companies and enterprises; relevant teams include FinOps/RevOps, Finance, Engineering, Product, and AI strategy leaders.
- **USP (their claim):** Amberflo claims to unify real-time AI usage and cost governance with customer billing and margin visibility in one platform.
- **Cost attribution:** Attributes usage and cost to customers, tenants, products/features, models, agents, workflows, teams, users, projects, and business units. Captures through gateway connectors with no instrumentation required, and real-time usage/event metering. OTEL, billing-data, and cloud-bill ingestion are not stated.
- **Revenue and margin:** Connects usage, cost, and customer billing to show customer- and feature-level margin, unit economics, and profitability; identifies accounts where costs exceed revenue.
- **Credits and billing:** Supports usage-based, tiered, volume, hybrid, prepaid credit wallets with real-time drawdown, minimum commits and overages, and outcome-based pricing. Generates invoices and billing reports.
- **Finance integration:** Supports chargebacks, showbacks, P&L-level accounting, invoices, and revenue-recognition workflows. Named ERP, accounting, CRM, or third-party billing integrations are not stated.
- **Outcome / ROI:** Supports outcome-based pricing and says usage can be tied to business outcomes; specific outcome measurement or ROI calculation methods are not stated.
- **Pricing:** No prices stated. Pricing is usage-based on event ingestion volume and amount invoiced; Essential and Custom are listed as demo-request plans.
- **Threat to our idea:** High
- **Sources:** [amberflo.io/platform](https://amberflo.io/platform), [amberflo.io/pricing](https://amberflo.io/pricing), [docs.amberflo.io](https://docs.amberflo.io/)

#### Ascerta (formerly Pay-i)

- **What they do:** Enterprise AI Management. Atlas measures AI cost, value, adoption and ROI for each use case, from a single run up to the whole portfolio, and ties each one to a business KPI ([Ascerta Atlas](https://ascerta.com/product/atlas)). The company also sells Forge (coding-agent productivity) and Convoy (for companies that provision their own AI capacity) ([Ascerta press release](https://ascerta.com/resources/press/ascerta-raises-18m-series-a)).
- **Buyer:** CIOs, CFOs and AI leaders at large enterprises measuring their own internal AI use, not SaaS companies selling AI to customers.
- **USP (their claim):** The "true cost" of every agent, run by run, including hidden fees and enterprise discounts that other tools miss or average away; value tied to KPIs; a "Recover the spend producing nothing" view covering failed runs, duplicate use cases and shadow AI ([Ascerta Atlas](https://ascerta.com/product/atlas)).
- **Cost attribution:** Rolls up cost by run, use case, team, business unit and enterprise, plus engagement by person and tool. Connects to homegrown apps, Microsoft Copilot, Amazon Bedrock AgentCore, Salesforce Agentforce, GitHub Copilot, Claude Code and Codex ([Ascerta press release](https://ascerta.com/resources/press/ascerta-raises-18m-series-a)).
- **Revenue and margin:** Not stated. Value is measured as KPIs, dollars earned and time saved, not as revenue or margin per external customer.
- **Credits and billing:** Not stated.
- **Finance integration:** ERP and billing integrations not stated. The earlier Pay-i docs offered a CSV export of reports ([Pay-i docs](https://docs.pay-i.com/docs/custom-reports)).
- **Outcome / ROI:** Core strength. Aligns each use case to KPIs and analyzes workflows against business objectives.
- **Pricing:** Not stated.
- **Funding:** $18M Series A led by Dell Technologies Capital (September 30, 2026), $22.9M raised in total; Bellevue, WA; founded by Microsoft veterans David Tepper, Doron Holan and Erik Winters ([Ascerta press release](https://ascerta.com/resources/press/ascerta-raises-18m-series-a)).
- **Threat to our idea:** High if we target internal enterprise AI ROI. Medium for the SaaS-margin idea, since Ascerta doesn't map spend to customer revenue or credits. It does narrow our "seat-based tools and discounts" gap on the internal side.
- **Sources:** [ascerta.com/product/atlas](https://ascerta.com/product/atlas), [ascerta.com/resources/press/ascerta-raises-18m-series-a](https://ascerta.com/resources/press/ascerta-raises-18m-series-a), [docs.pay-i.com/docs/custom-reports](https://docs.pay-i.com/docs/custom-reports)

### Layer 4 — Cloud FinOps extending to AI (bill-based allocation)

#### CloudZero

- **What they do:** Cloud financial control plane that collects, analyzes, allocates, and monitors cloud and AI spend; supports cost exploration, anomaly alerts, optimization, unit economics, and cost questions through AI.
- **Buyer:** Finance and FinOps teams, with platform/DevOps engineers and engineering and business leaders also using it.
- **USP (their claim):** CloudZero claims its allocation engine connects AI and cloud spend to business outcomes in one model that reconciles to invoices.
- **Cost attribution:** Attributes spend by team, product, feature, environment, customer, service, account, and other defined dimensions; supports cost per customer, transaction, or agent. Captures provider cost and billing data; says it captures spend as work happens and reconciles allocations to invoices. SDK, gateway proxy, and OTEL methods are not stated.
- **Revenue and margin:** Connects cost to customer and product profitability, gross margin impact, and pricing decisions; supports measuring unit economics and margin.
- **Credits and billing:** not stated
- **Finance integration:** not stated
- **Outcome / ROI:** Positions the product around connecting AI and cloud spend to business outcomes and ROI; cites cloud ROI reporting and AI investment returns. Claims an average three-month payback.
- **Pricing:** not stated
- **Threat to our idea:** Medium-High
- **Sources:** [docs.cloudzero.com/docs/cloudzero](https://docs.cloudzero.com/docs/cloudzero), [cloudzero.com/about](https://www.cloudzero.com/about/), [cloudzero.com/solutions/finance](https://www.cloudzero.com/solutions/finance/)

#### Vantage

- **What they do:** FinOps platform for visibility, allocation, reporting, governance, and optimization of cloud, SaaS, and AI costs.
- **Buyer:** FinOps and engineering teams at companies managing significant cloud spend.
- **USP (their claim):** Vantage claims to be a turn-key, enterprise-ready FinOps platform with precise virtual-tagging allocation, fine-grained visibility, and support for more than 40 integrations.
- **Cost attribution:** Virtual tagging supports custom allocation and team/service showback. LLM token allocation uses per-request telemetry in a common schema to attribute spend to teams, customers, and features. Data comes through supported provider integrations; specific capture methods beyond per-request telemetry are not stated.
- **Revenue and margin:** Unit Costs compare spend with business metrics such as cost per customer, unit, or transaction to optimize margin. The homepage also says the platform helps maintain margin; per-customer revenue or profit calculations are not stated.
- **Credits and billing:** Plans have fixed monthly prices and tracked-cloud-spend limits; Enterprise pricing is custom. Usage-based reporting is listed, but credits, customer invoicing, and outcome-based pricing are not stated.
- **Finance integration:** Ramp integration is mentioned. Data can be exported to Snowflake, Databricks, or another system of truth. Other ERP, accounting, or revenue-recognition integrations are not stated.
- **Outcome / ROI:** Provides cost-saving recommendations, waste remediation, savings-plan automation, and unit-cost analysis. Explicit outcome or ROI measurement is not stated.
- **Pricing:** Starter: free; Pro: $30/month; Business: $200/month; Enterprise: custom. Plans have tracked-cloud-spend limits of $2,500, $7,500, $20,000, and unlimited, respectively.
- **Threat to our idea:** Medium
- **Sources:** [vantage.sh](https://www.vantage.sh/), [vantage.sh/features](https://www.vantage.sh/features), [vantage.sh/pricing](https://www.vantage.sh/pricing)

#### Finout

- **What they do:** FinOps platform unifying cloud, Kubernetes, SaaS, and AI spend for visibility, allocation, planning, optimization, anomaly detection, and cost governance.
- **Buyer:** Enterprise FinOps, Finance, DevOps, and Engineering teams managing cloud and AI spend.
- **USP (their claim):** Finout’s claimed differentiator is a unified, allocation-ready data layer and MegaBill for cloud, Kubernetes, SaaS, and AI spend, paired with FinOps agents that detect, investigate, and route actions.
- **Cost attribution:** Allocates spend by team, product, feature, model, endpoint, token, and customer/client unit economics. Captures cloud billing data and service/provider APIs; pages say no code changes or agents are required.
- **Revenue and margin:** Describes profitability and unit economics, including client-level unit economics and comparing cost impact with business growth. No explicit revenue or margin data integration is stated.
- **Credits and billing:** MegaBill normalizes cloud, AI, and SaaS costs into a unified bill and supports allocation of usage-based spend. Credits, customer invoicing, and outcome pricing are not stated.
- **Finance integration:** Financial plans and budgets are supported. ERP, accounting, revenue-recognition, CRM, and billing-system integrations are not stated; operational integrations include Jira, ServiceNow, Slack, and Teams.
- **Outcome / ROI:** AI spend visibility is positioned to help Finance prove ROI and leadership justify budgets. Cost-per-token/request and unit-economics views are described; specific outcome measurement methodology is not stated.
- **Pricing:** Quote-based. The homepage says a flat platform fee based on spend under management; the platform page says a flat yearly fee based on committed cloud-spend tier, fixed for the contract term.
- **Threat to our idea:** Medium
- **Sources:** [docs.finout.io/get-started-with-finout/introduction-to-finouts-suite-of-features](https://docs.finout.io/get-started-with-finout/introduction-to-finouts-suite-of-features), [finout.io](https://www.finout.io/), [finout.io/finops-platform](https://www.finout.io/finops-platform)

### Layer 5 — Monetization and usage billing (credits, invoices, rev rec)

#### Stigg (met at conference)

- **What they do:** Usage runtime and pricing/packaging platform for AI products: metering, entitlements, credits, governance, subscription management, and optional contract management/invoicing. It can enforce access and budgets before a model call or other action.
- **Buyer:** Engineering teams building AI products, with product/GTM teams configuring packaging and pricing; finance teams can use credit-ledger exports for revenue recognition.
- **USP (their claim):** Stigg claims to combine metering, entitlements, credits, and governance in a request-path enforcement layer that checks access and budgets before usage incurs cost.
- **Cost attribution:** Attributes usage and reported gateway cost to customers and optionally agents; governance supports budgets for agents, teams, and users. Captured through the Agent SDK wrapper from provider/gateway responses, or Stigg usage events. Cloud-bill attribution is not stated.
- **Revenue and margin:** Supports usage pricing, actual gateway-cost pass-through, and cost-plus pricing with a margin. Credit grants and consumption can support deferred and recognized revenue calculations; per-customer/product profitability reporting is not stated.
- **Credits and billing:** Supports credit wallets, ledgers, grants, expiry, priority consumption, and usage-based credit drawdown. Supports subscriptions and usage pricing, plus invoicing through Stigg, Stripe, or Airwallex; outcome pricing is not stated.
- **Finance integration:** Billing integrations include Stripe, Zuora, Chargebee, and Airwallex; CRM includes Salesforce and HubSpot. Data can be exported to warehouses including Snowflake, BigQuery, Databricks, and S3. NetSuite/SAP ERP integrations are not native; warehouse export and existing ETL are suggested.
- **Outcome / ROI:** not stated
- **Pricing:** Build is free; Pro is listed as $499/month in the early-preview pricing section and $399/month billed annually elsewhere on the page; Scale and BYOC are custom-priced. BYOC is stated to start at $40K/year.
- **Threat to our idea:** Medium
- **Sources:** [docs.stigg.io/documentation/ai-agents/overview](https://docs.stigg.io/documentation/ai-agents/overview), [docs.stigg.io/documentation/getting-started/welcome-to-stigg](https://docs.stigg.io/documentation/getting-started/welcome-to-stigg), [docs.stigg.io/documentation/modeling-your-pricing-in-stigg/credits/revenue-recognition](https://docs.stigg.io/documentation/modeling-your-pricing-in-stigg/credits/revenue-recognition), [docs.stigg.io/documentation/modeling-your-pricing-in-stigg/overview](https://docs.stigg.io/documentation/modeling-your-pricing-in-stigg/overview), [stigg.io/pricing](https://www.stigg.io/pricing)

#### Metronome

- **What they do:** Usage-based billing and monetization infrastructure that meters raw usage events, calculates metrics, manages pricing, and supports real-time billing and invoicing alongside subscription models.
- **Buyer:** Software companies with usage-based or complex pricing; relevant teams include Product, GTM, Finance, and engineering.
- **USP (their claim):** Metronome claims to unite real-time metering, flexible pricing, billing, and reporting in infrastructure that supports both product-led scale and sales-led complexity.
- **Cost attribution:** Provides usage and spend visibility by customer and pricing dimensions, with customer consumption tracking and margin analysis. Captures raw usage events through an integration and exposes data through APIs, webhooks, and warehouse enrichment. Cloud-bill, agent, team, and user attribution are not stated.
- **Revenue and margin:** Provides data for margin analysis, revenue forecasting, and daily revenue tracking. Explicit per-customer or per-product profitability calculations are not stated.
- **Credits and billing:** Supports usage-based billing, invoices, and configurable credit models and commits. Outcome-based pricing support is not stated.
- **Finance integration:** Describes native integrations with Stripe and cloud marketplaces, plus syncing data to CRM and ERP systems and enriching data warehouses. Specific CRM, ERP, accounting, or revenue-recognition products are not named.
- **Outcome / ROI:** Explicit ROI or outcome measurement is not stated. Usage and spend data can support strategic decisions, customer health monitoring, and upsell timing.
- **Pricing:** not stated
- **Threat to our idea:** Medium
- **Sources:** [metronome.com](https://metronome.com/), [metronome.com/blog/launch-iterate-and-scale](https://metronome.com/blog/launch-iterate-and-scale), [metronome.com/product-overview](https://metronome.com/product-overview)

#### Orb

- **What they do:** Usage-based, seat-based, hybrid, and enterprise-contract billing. Orb meters usage, configures pricing, generates invoices, supports collections and revenue recognition, and recalculates bills by querying stored usage events.
- **Buyer:** Companies monetizing usage, especially AI and infrastructure businesses; relevant teams include Product, Engineering, Finance, Sales, and RevOps.
- **USP (their claim):** Orb claims its query-based architecture preserves raw usage events, enabling flexible pricing changes, historical simulations, backfills, and auditable invoice calculations without re-ingesting usage.
- **Cost attribution:** Not stated for AI/cloud spend attribution. Orb bills from usage events and supports custom SQL metrics and dimensions such as tokens, model, region, customer, and invoice line item; ingestion via SDK, gateway, or OTEL is not stated.
- **Revenue and margin:** Supports accrued-revenue visibility, revenue forecasting, and modeling revenue and customer-level impacts of pricing scenarios. Per-customer or product cost, margin, or profitability attribution is not stated.
- **Credits and billing:** Supports prepaid credits and deterministic drawdown, usage-based and hybrid billing, enterprise commits with overages, and invoicing. Outcome-based pricing is not stated.
- **Finance integration:** Revenue-recognition exports to financial systems; the article also states native NetSuite integration, data warehouse sync, Salesforce and NetSuite integrations, and finance and tax integrations. Payment processor flexibility is noted.
- **Outcome / ROI:** Pricing simulations compare scenarios against historical usage, preview invoices, and model projected revenue and customer impacts. Outcome or ROI measurement is not stated.
- **Pricing:** Custom pricing; Core, Advanced, and Enterprise tiers are described, but no rates are stated.
- **Threat to our idea:** Medium
- **Sources:** [docs.withorb.com/introduction](https://docs.withorb.com/introduction), [docs.withorb.com/overview](https://docs.withorb.com/overview), [withorb.com/blog/usage-based-billing-software-ai-companies](https://www.withorb.com/blog/usage-based-billing-software-ai-companies)

#### Solvimon

- **What they do:** API-first pricing and billing platform for SaaS and AI businesses. Covers metering, pricing plans, quotes, subscriptions, invoicing, payments, and revenue recognition across usage-based, hybrid, and enterprise models.
- **Buyer:** SaaS and AI companies, especially AI-native usage-based startups and finance, billing, or monetization teams at growing and enterprise businesses.
- **USP (their claim):** Solvimon claims to handle complex hybrid, usage-based, and enterprise billing in one end-to-end platform, drawing on founders’ experience building Adyen’s billing infrastructure.
- **Cost attribution:** Meters usage and supports pricing rules for API calls, inference costs, and agent actions. OpenAI integration tracks LLM costs by project, user, or API key for pass-through pricing. Usage data can be ingested from connected data sources; OTEL or cloud-bill attribution is not stated.
- **Revenue and margin:** Supports revenue and usage analytics and built-in revenue recognition. Explicit cost-to-revenue, margin, or profitability reporting per customer or product is not stated.
- **Credits and billing:** Supports credits and tokens, credit burn-down and rollover, prepaid credit pools, and hybrid pricing. Supports outcome-based pricing. AI startups get the first $3M of billing volume free; contact for current terms.
- **Finance integration:** Lists integrations including NetSuite, QuickBooks, Xero, Exact, DATEV, Dynamics 365, Salesforce, HubSpot, Stripe, Adyen, Checkout.com, Snowflake, BigQuery, Redshift, and cloud storage sources. Supports syncing invoices or transaction journal entries to accounting systems.
- **Outcome / ROI:** Supports outcome-based pricing, but outcome or ROI measurement and realized-value tracking are not stated.
- **Pricing:** AI startups get the first $3M of billing volume free; contact Solvimon for current terms. The website also displays sample pricing proposals, but does not establish them as standard platform pricing.
- **Threat to our idea:** Medium
- **Sources:** [docs.solvimon.com/platform-guides/getting-started/about-solvimon](https://docs.solvimon.com/platform-guides/getting-started/about-solvimon), [solvimon.com](https://www.solvimon.com/), [solvimon.com/why-solvimon](https://www.solvimon.com/why-solvimon)

#### Lago

- **What they do:** Open-source metering and billing software for subscription, usage-based, and hybrid pricing. Supports high-volume event processing, invoicing, prepaid credits, and payment-provider integrations.
- **Buyer:** Product-led SaaS and AI companies, especially engineering teams building usage-based pricing; product managers and finance leaders are also mentioned as users.
- **USP (their claim):** Lago claims to be the only open-source metering and usage-based billing solution, combining real-time event metering, flexible billing, and the option to inspect, customize, or self-host the software.
- **Cost attribution:** Not stated. Pages describe usage-event metering, per-token pricing, and customer-level time zones, but do not specify AI/cloud spend attribution dimensions or capture methods such as SDK, proxy, OTEL, or cloud bills.
- **Revenue and margin:** Provides billing analytics and revenue computation, including MRR, but does not state that it connects costs to revenue, margin, or profitability per customer or product.
- **Credits and billing:** Supports prepaid-credit wallets, configurable credit values and quantities, and recurring top-ups based on consumption thresholds or intervals. Supports usage-based billing and invoicing; outcome pricing is not stated.
- **Finance integration:** Native integrations include NetSuite and QuickBooks for accounting, Salesforce for CRM, and Stripe Payments, GoCardless, and Adyen for payments. It can also integrate with QuickBooks, NetSuite, Bill.com, or Stripe for invoicing.
- **Outcome / ROI:** Not stated.
- **Pricing:** Forever-free open-source solution; enterprise plans are available with custom pricing. The product-features page says plans include invoicing automation without a percentage-of-billings charge; hosted-plan pricing is not stated.
- **Threat to our idea:** Low
- **Sources:** [getlago.com/docs/faq/about-software](https://getlago.com/docs/faq/about-software), [getlago.com/docs/faq/general](https://getlago.com/docs/faq/general), [getlago.com/docs/faq/product-features](https://getlago.com/docs/faq/product-features)

#### Flexprice

- **What they do:** Open-source and commercial platform for usage metering, subscription and usage-based billing, credit management, invoicing, and feature entitlements.
- **Buyer:** Developers and AI/agentic companies building products with usage-based or hybrid pricing; finance teams are also mentioned for reconciliation.
- **USP (their claim):** Combines developer-oriented, real-time metering and flexible billing with feature management, and offers open-source self-hosting for control without vendor lock-in.
- **Cost attribution:** Meters custom usage events in real time, including per-customer usage. SDKs and APIs can send usage events. AI/cloud cost attribution by tenant, product, feature, agent, team, or user, and OTEL or cloud-bill ingestion are not stated.
- **Revenue and margin:** Supports usage-based billing and revenue analytics, but connecting costs to revenue, margin, or profitability per customer or product is not stated.
- **Credits and billing:** Supports prepaid and promotional credit grants, wallets, auto top-ups, expiration rules, credit-based pricing, usage-based and hybrid plans, invoicing, and Stripe payments. Outcome-based pricing is not stated.
- **Finance integration:** Lists Stripe Payments, Stripe Tax, Numeral (taxes), and HubSpot (CRM); supports invoicing and reconciliation. ERP, accounting, revenue-recognition, or warehouse integrations are not stated.
- **Outcome / ROI:** Says usage-based pricing aligns revenue with customer value; outcome or ROI measurement is not stated.
- **Pricing:** Pay as you go: from $199/month plus 0.5% of billing, including up to 50M usage events/month. Enterprise: starts at $3,000/month with no revenue share. Open-source version also offered.
- **Threat to our idea:** Low
- **Sources:** [docs.flexprice.io/docs/welcome-to-flexprice](https://docs.flexprice.io/docs/welcome-to-flexprice), [flexprice.io/pricing](https://flexprice.io/pricing), [flexprice.io/product/usage-based-billing-software](https://flexprice.io/product/usage-based-billing-software)
