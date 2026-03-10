<div align="center">

# Monaiq

**The developer-first licensing and monetization platform, built for the AI era.**

[![Nuget](https://img.shields.io/nuget/v/Sidub.Licensing.Client)](https://www.nuget.org/packages/Sidub.Licensing.Client/)
[![npm](https://img.shields.io/npm/v/@sidub/licensing-client)](https://www.npmjs.com/package/@sidub/licensing-client)

[Website](https://monaiq.com) | [Documentation](https://docs.monaiq.com) | [Discord](https://discord.gg/monaiq) | [Portal](https://portal.monaiq.com)

</div>

---

Shipping features is fun. Building entitlement engines, catalog syncs, billing integrations, and paywalls is not. 

Existing solutions force you into heavy network dependencies, bloated SDKs, or complex dashboard configurations that pull you out of your flow. **Monaiq** shifts the paradigm: a lightweight, cryptographically secure licensing engine structured entirely around developer workflows and AI automation.

## ✨ Why Monaiq?

* 🤖 **AI-Native Workflow:** The world's first Model Context Protocol (MCP) server for monetization. Ask your IDE's AI to monetize an endpoint, and it handles the rest.
* ⚡ **Zero-Latency Enforcement:** Licenses are issued as secure tokens. Validation happens locally within your app, offline, with zero network calls and no single point of failure.
* 🧩 **Polymorphic Entitlements:** Don't just check if a user "has a subscription." Model complex realities like rate limits, metered usage, and granular feature toggles.
* 💳 **Stripe Connect Built-in:** Automated recurring and metered billing orchestration running seamlessly under the hood.

---

## 🛠️ The Developer Experience

Monaiq is designed to keep you in the editor. You can build your access controls manually using our strongly-typed SDKs, or let our MCP server configure them for you.

### 1. The AI Workflow (Monaiq MCP)
Plug Monaiq directly into VS Code, Cursor, Windsurf, or Claude Desktop. 

> **You:** "I want to monetize this new PDF endpoint. Require a 'Pro' subscription and charge $0.05 per generation."
> 
> **Monaiq MCP + Copilot:** Automatically provisions the feature in your Monaiq catalog, configures Stripe, and generates the exact runtime assertion code right in your project.

### 2. The Code Workflow (The Reality)
Under the hood, Monaiq relies on explicit, strongly-typed assertions. No magic strings padding API calls, and no silent failures. Because validation is cryptographic and local, your app's performance is never impacted.

**In your .NET Backend:**

```csharp
using Sidub.Licensing.Client;
using Sidub.Licensing.Models;

// Inject the ILicensingService
var licensing = serviceProvider.GetRequiredService<ILicensingService>();

// Assert access to a specific feature directly in your application logic
var result = await licensing.AssertLicenseAsync(
    serviceReference: "my-service",
    context: userContext, 
    assertion: ServiceAccessLicenseAssertion.Create("advanced-reporting")
);

if (!result.IsGranted) 
{
    return Unauthorized("Upgrade to the Pro tier to access advanced reporting.");
}
```

**In your React/Node Frontend:**

```typescript
import { useLicensing } from '@sidub/licensing-client';

function AdvancedReporting() {
  const { assertLicense } = useLicensing();
  
  // Clean, reactive hooks for UI state
  const { isGranted, loading } = assertLicense('advanced-reporting');

  if (loading) return <Spinner />;
  if (!isGranted) return <UpgradePrompt feature="Advanced Reporting" />;

  return <ReportDashboard />;
}
```

---

## 🎯 What can you build with it?

Whether you're selling complex enterprise workflows or bootstrapping a micro-SaaS, Monaiq adapts to your model without restructuring your database:

1. **B2B SaaS Platforms:** Tiered feature gating (Basic, Pro, Enterprise) enforced effortlessly at the API boundary or front-end UI.
2. **Metered API Monetization:** Charge by the token, the byte, or the API call using robust, localized consumption tracking.
3. **On-Premise & Desktop Software:** Utilize true offline cryptographic token validation for software running entirely outside the cloud.

---

## 🚀 Getting Started

Start integrating Monaiq into your stack in seconds.

**For .NET Applications:**
```bash
dotnet add package Sidub.Licensing.Client
```

**For Node/React Applications:**
```bash
npm install @sidub/licensing-client
```

📚 [Read the full documentation](https://docs.monaiq.com) for deep dives into catalog configuration, Stripe integration, and MCP setup.

## 🤝 Join the Community

- **Discord**: [Chat with the team and other developers](https://discord.gg/monaiq)
- **Twitter / X**: [Follow us for updates @monaiq](https://twitter.com/monaiq)
- **Issues**: [Found a bug? Open an issue on GitHub](https://github.com/Sidub-Inc/Sidub.Licensing/issues)

## 📄 License

Monaiq (Sidub Licensing) is made available under a **Proprietary License**. 
See the [LICENSE.txt](LICENSE.txt) file in the repository for full details and terms of use. For inquiries about obtaining a license, visit [https://sidub.ca/licensing](https://sidub.ca/licensing).
