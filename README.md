# Autonoma

> Non-custodial AI agents for Bitcoin DeFi. Personal, deployable, open source.

Autonoma is a hosted platform where users spin up their own AI agents and run them against a curated library of skills for Bitcoin ecosystem DeFi. Yield optimization, LP lifecycle management, alpha detection, autonomous rebalancing. The user holds their own keys. The agents work for them.

Built on the [aibtc MCP](https://github.com/aibtcdev/mcp) open source infrastructure, extended with skills already validated in production competition.

## What Autonoma is

Autonoma is the layer between the AI agent primitives that already exist (Claude, MCP, agent frameworks) and the DeFi protocols that African and emerging market users cannot access without institutional infrastructure. It packages a library of tested skills into a runtime that anyone can deploy for themselves.

The user does three things:

1. Spin up a personal agent instance
2. Create a new non-custodial wallet or connect an existing one
3. Choose which skills the agent runs and against which protocols

The agent executes autonomously within the user's defined parameters. All capital stays in the user's wallet. Autonoma never has custody.

## The skill library at v0.1

The initial skill set is drawn from work already shipped by the founder in the 30-Days-AI-Challenge repository, with five skills that won the AIBTC x Bitflow Skills Competition and one (Stacks Alpha Engine) approved upstream into aibtcdev/skills.

Five skills anchor v0.1:

- **Smart Yield Migrator** — Compares APY across Bitflow, ALEX, PoX with gas modeling and profit-gate enforcement
- **Stacks Alpha Engine** — Autonomous signal detection for Stacks DeFi opportunities
- **HODLMM LP Lifecycle** — Entry, monitoring, rebalancing, and exit automation for LP positions
- **Impermanent Loss Guard** — Continuous IL tracking with automated exit triggers
- **Gas-Aware Migrator** — Live gas fee sampling from Stacks network with migration profit modeling

Each skill is documented in `skills/[skill-name]/`. Each has its own tests, its own README, and its own version.

## Architecture

Autonoma is built in three layers:

**Layer 1: The MCP** — Extended from aibtc's open source MCP, hosts the skill library and provides the interface any compatible AI agent can call.

**Layer 2: The Agent Runtime** — Wraps a Claude-family model with the MCP connection, the user's wallet configuration, and their skill-selection preferences. Runs the agent within user-defined constraints.

**Layer 3: The Wallet Layer** — Non-custodial by design. Autonoma never holds keys. Supports both new wallet creation (mnemonic returned to user) and connection of existing wallets (Xverse, Leather, Hiro).

Full architecture documentation lives in `docs/architecture.md`.

## Non-custodial by architecture

Autonoma cannot become custodial by accident. The Wallet Layer is designed so that keys never touch Autonoma infrastructure. Users hold their own mnemonics. Skills sign transactions in the user's client environment. Autonoma sees signed transactions on the way out and results on the way back in, never keys.

This is a technical constraint, not a policy. Losing keys is impossible because Autonoma never had them.

## Skill specification

Any skill in the Autonoma library conforms to the `SKILL_SPEC` interface defined in `docs/skill-spec.md`. This specification is open. Any developer can propose a skill by conforming to the interface, opening a PR, and passing the review process.

Skills are versioned semantically. Breaking changes require major version bumps. Users see skill versions in their agent configuration and can pin specific versions.

## Roadmap

**Phase 1: Foundation (Season 7)**
Five anchor skills documented and hardened. MCP server deployed. Skill specification published. Working example agent that runs one skill end to end against Stacks testnet.

**Phase 2: Runtime (Season 8)**
Agent runtime built. Wallet layer non-custodial integration with Xverse and Leather. User-facing configuration for skill selection and constraint setting. Mainnet support.

**Phase 3: Library expansion (Season 9)**
Ten additional skills added. Public skill contribution process live. First external contributor skill accepted. Basic usage analytics for skill effectiveness reporting.

**Phase 4: Ecosystem (Season 10)**
Cross-protocol coverage: ALEX, Bitflow, Velar, Zest, Arkadiko. Integration with additional wallets. Advanced skill composition where multiple skills chain into one strategy.

**Phase 5: Scale (Season 11+)**
Community-maintained skill contributions become the majority of the library. Autonoma becomes coordination infrastructure for autonomous DeFi participation, not a single-maintainer project.

## Who this is for

Small-capital users in African and emerging markets who cannot afford the institutional infrastructure that professional trading desks use to participate in DeFi. Autonoma democratizes what previously required a team and a treasury.

Also for developers who want to build agents against Stacks DeFi without stitching together protocol integrations from scratch. Autonoma is the shortcut.

## Why the LAB Open Source Builders Fund

Autonoma satisfies the fund's eligibility criteria directly:

- Open source with a public code repository under permissive license
- Core contributor is African, operating in Nigeria, part of the LAB developer ecosystem
- Built on and integrates with Bitcoin infrastructure across Stacks, Lightning-adjacent protocols, and Bitcoin L1 through Stacks anchoring
- Working prototype and active repository development, with five skills already competition-validated and one upstream-approved
- Contributes to infrastructure, developer tooling, and decentralized systems
- Participation in the LAB developer community and collaboration through the LAB GitHub organization
- Development updates, documentation, and learning resources published continuously

Autonoma is exactly what the LAB Open Source Builders Fund exists to fund.

## Contributing

See `CONTRIBUTING.md` for how to add skills, report issues, or contribute to the runtime.

## License

MIT

## Founder

Built by the operator of [@microbasilisk](https://x.com/microbasilisk), a Nigerian smart contract engineer with deep DeFi infrastructure expertise. Five wins in the AIBTC x Bitflow Skills Competition. Stacks Alpha Engine upstream approved into aibtcdev/skills. Rank #4 on aibtc.news.

## Fund attribution

Supported by the [LAB Open Source Builders Fund](https://artizen.fund/index/mf/lab-open-source-builders-fund) on Artizen.
