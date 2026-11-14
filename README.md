# Awesome-QA-Account-Subscription-Management

# Awesome QA Account & Subscription Management

> A curated list of top QA Account and Subscription Management platforms — both SaaS/Hosted commercial device cloud admin portals and open-source alternatives for managing billing, plans, seats, and subscription lifecycle across testing infrastructure.
> 🌟 Star this repo if you find it useful! 🌟

---

## 📋 Table of Contents

- [SaaS / Hosted Platforms](#-saas--hosted-platforms)
  - [BrowserStack Account Management](#browserstack-account-management)
  - [Sauce Labs Subscription & Billing](#sauce-labs-subscription--billing)
  - [LambdaTest Subscriptions](#lambdatest-subscriptions)
  - [Kobiton Subscription Management](#kobiton-subscription-management)
  - [BitBar Subscriptions](#bitbar-subscriptions)
  - [TestGrid Pricing & Plans](#testgrid-pricing--plans)
  - [AWS Device Farm Slots](#aws-device-farm-slots)
- [Open-Source Software](#-open-source-software)
  - [Kill Bill](#kill-bill)
  - [stapel-billing](#stapel-billing)
- [Comparison at a Glance](#-comparison-at-a-glance)
- [Contributing](#-contributing)

---

## 🟦 SaaS / Hosted Platforms

Commercial, cloud-hosted QA Account and Subscription Management platforms. These are not open-source but are included as reference points for feature comparison.

### BrowserStack Account Management
**Type:** Plan management with owner-restricted billing access
BrowserStack's subscription management is restricted to the **Organization Owner** role. Billing information and credit card details can be updated in the **Billing & Invoices** section if purchased directly through the website; subscriptions purchased through Sales require contacting the account representative [citation:1]. Cancellation stops auto-renewal, but access continues until the end of the current billing cycle . A limited A/B test exposes cancellation via a three-dots menu next to the plan for some users .
**Best for:** Organizations needing strict owner-controlled billing governance, accepting that only the Owner can perform subscription changes.

### Sauce Labs Subscription & Billing
**Type:** Self-serve plan changes with proration handling
Sauce Labs allows plan changes at any time via **Account > Subscription and Billing**. Upgrades take effect immediately with prorated refunds and charges; downgrades take effect at the next billing cycle [citation:2]. Cancellation is self-serve via **Cancel Plan(s)** followed by **Unsubscribe now**, with email fallback to `billing@saucelabs.com` [citation:10]. Enterprise upgrades require contacting Sales [citation:2].
**Best for:** Teams wanting self-serve plan flexibility with clear proration rules and a straightforward cancellation path.

### LambdaTest Subscriptions
**Type:** Granular plan customization with monthly/annual toggle
LambdaTest (TestMu AI) provides **View Subscription** and **Go to Subscriptions & Billings** flows for adding, removing, and switching plans. Plans can be customized with parallel test quantities per product via a QTY dropdown [citation:3]. A monthly-to-yearly toggle saves up to 20%. Cancellation is via **Billing > CANCEL SUBSCRIPTION** with a reason selection, and a **Resume** option appears post-cancellation [citation:3].
**Best for:** Teams needing fine-grained control over parallel test quantities and the ability to resume a cancelled plan.

### Kobiton Subscription Management
**Type:** Org-owner-gated plan switching and cancellation
Kobiton restricts subscription management to **Org Owners** (ADMINs require additional permissions) via **Account > Subscription** [citation:4]. Plan switching uses **Switch Plans** with Monthly/Annual options. Cancellation takes effect at the end of the current billing period, after which a new plan can be purchased [citation:4]. Billing information is editable in the **Billing Information** section.
**Best for:** Teams needing clear owner-gated subscription control with end-of-period cancellation semantics.

### BitBar Subscriptions
**Type:** Personal/team plans with trial and usage visibility
BitBar distinguishes personal and team plans, with daily and monthly options payable by credit card and a **14-day trial** (limited devices, one automated run per hour, 4-minute live sessions) [citation:5]. **My Subscriptions** shows the current plan and latest usage, with **Unsubscribe** available directly. Billing history and receipts are accessible under **Account**. Plan changes are via **Subscriptions**, though only Team or custom plans can be billed and require admin changes [citation:5].
**Best for:** Teams wanting a trial-first evaluation with clear usage visibility and simple unsubscribe.

### TestGrid Pricing & Plans
**Type:** Seat-based AI platform with token-based test creation
TestGrid's **Starter** package is **$199 per seat/month** with 5,000 tokens (10-20 tokens per AI-generated test case; self-healing and bug summarization do not consume tokens) [citation:7]. **Growth** adds SSO, LDAP, MFA, site-to-site VPN, device pools, and unlimited tokens. **Custom Device Lab** offers on-premise or private cloud deployment. Upgrades take effect immediately; downgrades occur at renewal. No self-serve free trial—POCs run one to two weeks with a solutions engineer [citation:7].
**Best for:** Teams wanting an all-inclusive AI platform where agent access is bundled into the base price with no per-agent fees.

### AWS Device Farm Slots
**Type:** Slot-based concurrency with CLI/API management
AWS Device Farm uses **device slots** for concurrency: each automated testing slot allows one simultaneous test, and each remote access slot allows one simultaneous session [citation:13]. Slots are purchased per platform (Android/iOS) at **$250/slot/month** for unmetered testing [citation:6]. Management is via AWS CLI (`purchase-offering`, `get-account-settings`, `list-offerings`) or the console, with trial minutes visible in account settings [citation:6].
**Best for:** AWS-centric teams wanting pay-as-you-go or slot-based pricing with programmatic subscription control.

---

## 🟩 Open-Source Software

Self-hosted, community-driven QA Account and Subscription Management tools. The open-source ecosystem for **dedicated QA subscription management** is essentially nonexistent — available projects are general-purpose billing platforms that could be adapted for QA infrastructure billing.

### Kill Bill
**Stack:** Java / MySQL/MariaDB/PostgreSQL | **License:** Apache-2.0
Kill Bill is an open-source subscription billing and payments platform in production since 2010, released under Apache 2.0 and self-hosted on your own infrastructure [citation:15]. It provides subscriptions, usage billing, invoicing, and payments with **REST API** and **Kaui** (the admin UI for Finance/Support to issue refunds and adjust invoices) [citation:15]. Payment plugins exist for Stripe, Braintree, Adyen, and others, with tax plugins for Kintsugi. It supports **multi-tenant white-label billing** for platforms managing thousands of tenants [citation:15]. **Trade-off:** It is a full billing engine, not a QA-specific subscription manager—you build the plan/product mapping yourself.
**Best for:** Organizations wanting a proven, permissively licensed billing foundation to manage QA tool subscriptions internally, accepting the operational overhead of a Java/DB stack.

### stapel-billing
**Stack:** Python / Django | **License:** MIT
stapel-billing is a Django app providing payments and billing with **per-user credit wallets**, one-off credit packages, and **recurring subscription plans** [citation:8]. It includes Stripe-backed checkout, a **self-service customer portal**, idempotent webhooks, and a service-to-service debit endpoint. It is part of the Stapel framework of composable Django apps, deployable as a monolith or microservices [citation:8]. **Trade-off:** It is a billing component, not a QA platform—you integrate it into your own tooling.
**Best for:** Django teams wanting an MIT-licensed billing foundation with a self-service portal to manage QA tool seats or credit-based usage.

---

## 📊 Comparison at a Glance

| Software | License | Stack | Self-Serve Billing | Plan Change Timing | Cancellation | Best For |
|----------|---------|-------|-------------------|-------------------|--------------|----------|
| **BrowserStack** | Proprietary | Cloud | ✅ Owner only | (Not specified) | End of cycle | Owner-gated governance |
| **Sauce Labs** | Proprietary | Cloud | ✅ | Immediate (up) / Next cycle (down) | Self-serve | Prorated plan flexibility |
| **LambdaTest** | Proprietary | Cloud | ✅ | (Check) | Self-serve + Resume | Granular quantity control |
| **Kobiton** | Proprietary | Cloud | ✅ Owner only | (Check) | End of period | Owner-gated + end-of-period |
| **BitBar** | Proprietary | Cloud | ✅ | Admin required | Self-serve Unsubscribe | Trial-first evaluation |
| **TestGrid** | Proprietary | Cloud | ❌ (POC only) | Immediate (up) / Renewal (down) | (Check) | All-inclusive AI + tokens |
| **AWS Device Farm** | Proprietary | Cloud | ✅ CLI/API | (Slot-based) | (Check) | Programmatic slot management |
| **Kill Bill** | Apache-2.0 | Java/DB | (Build yourself) | Configurable | (Build yourself) | Full OSS billing engine |
| **stapel-billing** | MIT | Django | ✅ Portal | (Configurable) | (Build yourself) | Django billing + portal |

---

## 🤝 Contributing

Contributions are welcome! If you know of an open-source QA Account or Subscription Management tool that should be listed here, please open a pull request with:

- Project name and URL
- Brief description (1–2 sentences)
- Stack and license
- Why it stands out

Please ensure the project is actively maintained (releases within the last 12 months) and genuinely open-source. Note that the open-source ecosystem for **QA-specific subscription management** is **essentially nonexistent** — commercial device clouds each implement their own billing portals, and no open-source project replicates that QA-native experience. **Kill Bill** is the most mature open-source billing engine that could be adapted for internal QA tool subscriptions [citation:15], while **stapel-billing** offers a lightweight Django-based alternative with a self-service portal [citation:8]. For teams needing a purpose-built QA subscription portal today, commercial platforms remain the only option.

---

## 📄 License

This list is released under CC0 1.0 Universal (Public Domain). The software projects listed retain their respective licenses.

---

⭐ **If this list helped you discover a useful tool, please star the repo!** ⭐
