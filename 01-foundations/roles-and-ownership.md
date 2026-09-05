# Roles and Ownership

`Home › 01-foundations › Roles and Ownership`

[Chapter 24 — Roles, Teams and Governance Forums](https://github.com/knowledgetrailsai/OASIS/blob/main/methodology/chapter-24-roles-teams-and-governance-forums.md) names the enterprise role this repository's authority-and-evidence design decisions ultimately answer to:

> **Business Outcome Owner**: accountable for outcome baseline, target, process authority and value realization.

This is the enterprise-level expression of the Business Process Owner, and it is the reason "the process owner is never the agent" is a principle rather than a preference: accountability always sits with a named human, regardless of how many steps in a process are agent-executed.

## Related roles this repository's work feeds or depends on

| Role | Chapter 24 accountability | Relationship to Loom |
|---|---|---|
| Business Outcome Owner | Outcome baseline, target, process authority and value realization | Owns the process a Loom workflow blueprint redesigns; holds authority to actually change it |
| Product / Service Owner | Scope, release, service health, backlog and lifecycle | Owns the interface and release cadence a workflow blueprint's "interface" field specifies |
| Data / Knowledge Owner | Authority, quality, access, freshness and lineage | Supplies the evidence a workflow blueprint's "evidence shown to human" field depends on — see [Forge](../../Forge) |
| Model / AI Steward | Model strategy, provider risk, evaluation and version policy | Counterpart on the AI-contribution side of the blueprint |
| Security / Privacy / Legal / RAI | Requirements, challenge, advice and acceptance within mandate | Reviews authority and escalation design for regulated decision points |
| Operations Owner | Runbook, support, incidents, capacity, change and recovery | Owns the fallback and escalation paths named in the blueprint once live |
| Independent Assurance | Objective challenge for high-impact evidence and controls | Challenges autonomy-ladder promotion decisions for high-impact workflows |

## Why "who may decide" cannot be left implicit

A common failure is leaving the authority field implicit, so the system ends up with more authority than anyone formally granted, simply because no one built a fallback path for timely human intervention. Naming a Business Outcome Owner for every workflow (not just for the system, but for the process the system participates in) is what prevents this drift.
