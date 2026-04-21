# Architecture

This document matches the high-level design described in [`PROPOSAL.md`](../PROPOSAL.md). It will evolve as contracts and services are implemented.

## Diagram (image)

![Agentic Economy architecture](diagrams/architecture.svg)

Source file: [`diagrams/architecture.svg`](diagrams/architecture.svg) — open or embed in presentations; GitHub renders the SVG on the file page.

## Diagram (Mermaid)

GitHub renders this Mermaid block in Markdown previews.

```mermaid
flowchart TB
  subgraph participants [Participants]
    U[Users and builders]
    A[Autonomous agents]
    C[Counterparties]
  end
  subgraph product [Agentic Economy]
    M[Marketplace]
    S[SDK and API]
    I[Agent identity]
    R[Reputation]
  end
  subgraph data [Data and settlement]
    IDX[Indexer]
    SC[Smart contracts]
    L2[Ethereum L2 / Ethereum]
  end
  participants --> product
  M --> IDX
  S --> IDX
  S --> SC
  I --> SC
  R --> SC
  IDX -->|reads events| SC
  SC --> L2
```

## Layers

| Layer | Role |
|--------|------|
| **Participants** | Humans and agents that list services, pay, and receive work. |
| **Product** | Marketplace discovery, programmatic access (SDK/API), wallet-linked identity, reputation. |
| **Indexer** | Indexes chain events for search and UX; does not replace on-chain truth. |
| **Contracts** | Registry, listings, payments/escrow; deployed testnet first, L2-aligned for cost. |

## Revision

Update this file when the first on-chain modules are named and deployed.
