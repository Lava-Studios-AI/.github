# Lava Studios AI

Lava Studios AI is building a connected creative platform for AI-assisted media production, workflow automation, and enterprise administration.

## Product architecture

| Product | Responsibility | Access |
|---|---|---|
| **Aisthetic OS** | Parent entry point, product navigation, and n8n-powered workflows | Public entry point with authenticated workspace features |
| **Aisthetic Studio** | Customer-facing creative application for image, video, character, and related generation tools | Customer product |
| **Enterprise Dashboard** | Organization administration, seats, roles, invitations, and usage oversight | Private beta for enterprise customers |
| **Aisthetic Backend** | Shared APIs, generation services, persistence, usage enforcement, and infrastructure | Internal platform infrastructure |

## Environments and hosting

| Environment | URL | Deployment |
|---|---|---|
| Aisthetic OS | `aistheticos.ai` | Cloudflare |
| Aisthetic Studio UAT | [uat.aistheticstudio.com](https://uat.aistheticstudio.com) | Automatically deployed from the staging workflow |
| Aisthetic Studio production | [app.aistheticstudio.com](https://app.aistheticstudio.com) | Automatically deployed from `main` |

Aisthetic OS and the Firebase-hosted applications share the same product data and storage foundation. Cross-domain authentication and authorization behavior is being standardized around Firebase Auth.

## Current priorities

1. Complete the local Aisthetic Studio refactor and production-readiness work.
2. Stabilize the UAT-to-production release path for Aisthetic Studio.
3. Organize Aisthetic OS as the parent entry point and workflow surface.
4. Complete Enterprise Dashboard QA for a controlled private beta.
5. Harden shared backend concerns: durable asset persistence, server-side usage enforcement, authentication, authorization, and observability.
6. Decide repository boundaries based on deployment ownership rather than repository count alone.

## Repository status

| Repository | Purpose | Status | Current focus |
|---|---|---:|---|
| [Aisthetic-frontend](https://github.com/Lava-Studios-AI/Aisthetic-frontend) | Aisthetic Studio customer application | 🟡 Active refactor | Architecture stabilization, UAT validation, and public-launch readiness |
| [Aisthetic-backend](https://github.com/Lava-Studios-AI/Aisthetic-backend) | Shared generation APIs and platform services | 🟠 Hardening | Durable storage, token enforcement, service ownership, and deployment boundaries |
| [Enterprise-Dashboard](https://github.com/Lava-Studios-AI/Enterprise-Dashboard) | Enterprise organization administration | 🟣 Private-beta preparation | QA, permissions, invitations, auditing, and release signoff |
| [Aisthetic-OS](https://github.com/Lava-Studios-AI/Aisthetic-OS) | Parent entry point and workflow platform | 🔵 Organization and deployment | Cloudflare hosting, Firebase authentication integration, navigation, and n8n workflows |

## Launch-readiness focus

### Aisthetic Studio

- Local refactor and architecture cleanup are active.
- Staging changes deploy to the UAT environment.
- Changes merged to `main` deploy to production.
- Public-launch stability is the top product priority.

### Aisthetic Backend

- Backend services remain shared infrastructure across products.
- Repository consolidation is under evaluation, but no merge is assumed.
- Immediate concerns include durable generated assets, server-side wallet enforcement, consistent authentication, and reliable API contracts.

### Enterprise Dashboard

- The dashboard is intended only for entitled enterprise customers.
- The initial release will be a private beta.
- Server-side organization and role enforcement, invitation delivery, audit records, and final QA are required before broader access.

### Aisthetic OS

- Aisthetic OS is the parent entry point for the ecosystem.
- It will route users to Aisthetic Studio and, when entitled, the Enterprise Dashboard.
- It may also host native workflows orchestrated through n8n.
- It is hosted on Cloudflare while sharing Firebase-backed identity, data, and storage with the wider platform.

## Platform principles

- **One ecosystem, clear product boundaries.** OS is the shell and workflow surface; Studio is the creative product; Enterprise is the administration product; backend services are shared infrastructure.
- **Shared identity and data.** Products should use consistent Firebase identities, authorization rules, Firestore data, and Firebase Storage ownership.
- **Durable customer assets.** Generated media must be copied from temporary provider URLs into owned storage.
- **Server-side enforcement.** Entitlements, roles, seats, and token usage must be enforced by trusted backend services.
- **Independent deployments where useful.** Repository structure should follow ownership and release boundaries, not force unrelated products into one deployable unit.

## Near-term roadmap

1. Complete Aisthetic Studio refactor and UAT validation.
2. Close launch-critical persistence, token, and authentication gaps.
3. Establish the Aisthetic OS entry-point experience on `aistheticos.ai`.
4. Validate cross-domain sign-in, navigation, entitlements, and logout.
5. Complete Enterprise Dashboard private-beta readiness.
6. Make and document the backend repository-boundary decision.
7. Publish a shared launch checklist and operational ownership map.

## Quick links

- [Aisthetic Studio frontend](https://github.com/Lava-Studios-AI/Aisthetic-frontend)
- [Aisthetic backend](https://github.com/Lava-Studios-AI/Aisthetic-backend)
- [Enterprise Dashboard](https://github.com/Lava-Studios-AI/Enterprise-Dashboard)
- [Aisthetic OS](https://github.com/Lava-Studios-AI/Aisthetic-OS)

This profile README is the high-level source of truth for product boundaries, environment ownership, and launch priorities. Detailed implementation plans remain in their respective repositories.
