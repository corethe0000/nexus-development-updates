# Nexus frontend - development updates

![phase](https://img.shields.io/badge/phase%201-frontend%20%26%20UX-2b6cb0)
![open PRs](https://img.shields.io/badge/open%20PRs-19-1f6feb)
![wallet modules](https://img.shields.io/badge/wallet%20modules-2-2f855a)
![next](https://img.shields.io/badge/next-TAO%20backend-f59e0b)
![core](https://img.shields.io/badge/core%20(TAO)-untouched-8b8b8b)

A community effort to improve the whole Nexus user-facing side and hand it back to Nexusoft. Everything here is interface and user experience, the Core (LLL-TAO) binary is untouched, so it all runs on mainnet exactly like the official software.

This board is the single place to see what is already built and shared, what is left, and who can take each open item, so the community and Nexusoft can keep track together.

## The plan

The idea is to finalize the whole frontend and user experience first, piece by piece, and only then move to the actual blockchain backend. Once the base is all in place we can work on everything at the same time and move much faster.

- **Phase 1 - frontend and user experience.** Explorer, desktop wallet, browser wallet, DEX module, contracts module: done and shared.
- **Phase 2 - mobile wallet.** The same fixes and UX brought to mobile: done and shared.
- **Phase 3 - the TAO backend.** Once the frontend is finalized, work on the actual blockchain layer.
- **Phase 4 - all together.** With the base done, frontend and backend improve in parallel.

## Who does what

| badge | who | means |
|------|------|-------|
| ![our team][own] | us | we are doing it or will do it next |
| ![community][com] | community | anyone in the community can pick it up, test or help |
| ![Nexusoft][nxo] | Nexusoft | only the core maintainers can do it (merge PRs, verify modules, official releases, audit) |
| ![we can guide][help] | us (support) | not ours to run, but we can help or guide if needed |

We keep to the development itself, the code (the frontend, and later the TAO backend). Anything that needs money, hosting or infrastructure (deploying contracts on chains, running relays and nodes, store listings, external audits) we leave to Nexusoft and the community, but we are happy to help and guide.

---

## Explorer  ![shared](https://img.shields.io/badge/status-shared-2f855a)

A redesigned modern explorer plus an optional block indexer and API.

- [x] Redesigned explorer: tokens, assets, market, signature chains and more
- [x] Optional block indexer and `/explorer` API
- Repos: [nexus-explorer-next](https://github.com/corethe0000/nexus-explorer-next) - [nexus-explorer-backend](https://github.com/corethe0000/nexus-explorer-backend)
- Pull requests: [explorer-next #4](https://github.com/Nexusoft/nexus-explorer-next/pull/4) - [explorer-backend #1](https://github.com/Nexusoft/nexus-explorer-backend/pull/1)

Left to do:
- [ ] Review and merge the two explorer PRs ![Nexusoft][nxo]

## Desktop wallet  ![shared](https://img.shields.io/badge/status-shared-2f855a)

A long list of fixes and additions to the official NexusInterface wallet, split into small focused pull requests, plus a build you can try right now.

- [x] 11 focused PRs against upstream (`Staging`): stale-data fixes, core startup and config (closes #246 #243 #261), updater (closes #248), translations (all 16 languages plus Croatian), new-user registration, staking rework and a small-amount warning, transactions and explorer links, UI polish, testnet safety markers, and an opt-in new dashboard
- [x] Community fixes build: [v3.2.0-fixes.1](https://github.com/corethe0000/NexusInterface/releases/tag/v3.2.0-fixes.1) (Windows installer, mainnet-safe)
- Repo and PRs: [fork](https://github.com/corethe0000/NexusInterface) - [all 11 PRs](https://github.com/Nexusoft/NexusInterface/pulls?q=is%3Apr+author%3Acorethe0000)

Left to do:
- [ ] Review and merge PRs #283 to #293 ![Nexusoft][nxo]
- [ ] Decide on the opt-in new dashboard, #292 (it is off by default) ![Nexusoft][nxo]
- [ ] Fold the fixes into the next official release ![Nexusoft][nxo]

## Browser wallet  ![shared](https://img.shields.io/badge/status-shared-2f855a)

A light Nexus wallet as a browser extension: no blockchain sync, Sign in with Nexus, and payments for websites.

- [x] Extension for Chrome, Edge, Brave, Opera and Firefox: [v0.3.0](https://github.com/corethe0000/nexus-browser-wallet/releases)
- [x] Sign in with Nexus and website payment flow
- Repo: [nexus-browser-wallet](https://github.com/corethe0000/nexus-browser-wallet)

Left to do:
- [ ] List it on the browser extension stores ![Nexusoft][nxo] ![we can guide][help]
- [ ] Nexus review of the Sign-in and payment flow ![Nexusoft][nxo] ![community][com]

## DEX module  ![preview](https://img.shields.io/badge/status-shared%20(preview)-2f855a)

Atomic swaps of NXS and Nexus tokens against USDT and USDC on EVM chains: a website, a desktop wallet module, and the `NexusSwap` HTLC contract. No custody, no owner, no fees in the contract.

- [x] Full swap flow with the HTLC on both sides, the browser extension as an optional way in
- [x] `NexusSwap.sol` (ERC-20 HTLC), 9 contract tests passing
- [x] BSC testnet swap and refund passed, Sepolia tested
- [x] Preview release: [v0.1.0](https://github.com/corethe0000/nexus-dex/releases) (test networks)
- Repo: [nexus-dex](https://github.com/corethe0000/nexus-dex)

Left to do:
- [ ] Deploy `NexusSwap` on BSC and Polygon mainnet (needs funds and infrastructure) ![Nexusoft][nxo] ![community][com] ![we can guide][help]
- [ ] Add more chains later: Ethereum and others ![Nexusoft][nxo] ![community][com] ![we can guide][help]
- [ ] Public relay and keeper hosting (HTTPS) and a mainnet Nexus API node ![Nexusoft][nxo] ![community][com] ![we can guide][help]
- [ ] WalletConnect v2 so you can pay USDT inside the desktop wallet ![our team][own]
- [ ] Verify the DEX module so it loads for everyone ![Nexusoft][nxo]
- [ ] Security review or audit before mainnet ![Nexusoft][nxo] ![community][com]

## Contracts module  ![shared](https://img.shields.io/badge/status-shared-2f855a)

Conditional payments for the desktop wallet: lock a payment with your own rules.

- [x] Templates: escrow, time-lock, return if unclaimed, release with a code, approvals k of n, crowdfunding, vesting, milestones; plus a block builder and a code console
- [x] Builds and signs its own transactions, the Core is untouched; mainnet escrow claim and fee tested
- [x] Release: [v0.1.0](https://github.com/corethe0000/nexus-contracts/releases)
- Repo: [nexus-contracts](https://github.com/corethe0000/nexus-contracts)

Left to do:
- [ ] Verify the contracts module so it loads for everyone ![Nexusoft][nxo]

## Mobile wallet  ![shared](https://img.shields.io/badge/status-shared-2f855a)

Fixes and new screens for the official nexus-mobile app (Android), split into pull requests that build on each other, plus an Android build you can try right now.

- [x] 6 stacked PRs against upstream (`master`): bug fixes, UI redesign, GitHub issues (closes #17 #19 #33 #38), new screens (app lock, monthly summary and CSV export, staking, names, invoices), languages (eleven besides English), and a second round after phone testing
- [x] Community fixes build: [v0.9.9-2-fixes.1](https://github.com/corethe0000/nexus-mobile/releases/tag/v0.9.9-2-fixes.1) (Android APK, mainnet-safe, own signing key so the official app has to be uninstalled first)
- Repo and PRs: [fork](https://github.com/corethe0000/nexus-mobile) - [all 6 PRs](https://github.com/Nexusoft/nexus-mobile/pulls?q=is%3Apr+author%3Acorethe0000)

Left to do:
- [ ] Review and merge the PRs in order, #40 to #45 ![Nexusoft][nxo]
- [ ] Fold the changes into the next official release, signed with the Nexus key ![Nexusoft][nxo]
- [ ] Build and test on iPhone (the code is shared, not built here without a Mac) ![Nexusoft][nxo] ![community][com] ![we can guide][help]
- [ ] Core fix for the light Core stopping the history download early on older sigchains (#38, #33); the app works around it ![Nexusoft][nxo]

---

## All repos and releases

| part | repo | release |
|------|------|---------|
| Explorer (frontend) | [nexus-explorer-next](https://github.com/corethe0000/nexus-explorer-next) | PR [explorer-next #4](https://github.com/Nexusoft/nexus-explorer-next/pull/4) |
| Explorer (backend) | [nexus-explorer-backend](https://github.com/corethe0000/nexus-explorer-backend) | PR [explorer-backend #1](https://github.com/Nexusoft/nexus-explorer-backend/pull/1) |
| Desktop wallet | [NexusInterface fork](https://github.com/corethe0000/NexusInterface) | [v3.2.0-fixes.1](https://github.com/corethe0000/NexusInterface/releases/tag/v3.2.0-fixes.1) |
| Browser wallet | [nexus-browser-wallet](https://github.com/corethe0000/nexus-browser-wallet) | [v0.3.0](https://github.com/corethe0000/nexus-browser-wallet/releases) |
| DEX module | [nexus-dex](https://github.com/corethe0000/nexus-dex) | [v0.1.0](https://github.com/corethe0000/nexus-dex/releases) |
| Contracts module | [nexus-contracts](https://github.com/corethe0000/nexus-contracts) | [v0.1.0](https://github.com/corethe0000/nexus-contracts/releases) |
| Mobile wallet | [nexus-mobile fork](https://github.com/corethe0000/nexus-mobile) | [v0.9.9-2-fixes.1](https://github.com/corethe0000/nexus-mobile/releases/tag/v0.9.9-2-fixes.1) |

[own]: https://img.shields.io/badge/-our%20team-2b6cb0
[nxo]: https://img.shields.io/badge/-Nexusoft-e8663c
[com]: https://img.shields.io/badge/-community-2f855a
[help]: https://img.shields.io/badge/-we%20can%20guide-6b7280
