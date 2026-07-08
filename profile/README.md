<!-- <p align="center">
  <img src="https://raw.githubusercontent.com/dshield-xyz/dshield/main/frontend/public/dshield.png" alt="DShield Logo" width="160" />
</p> -->

<h1 align="center">DShield</h1>

<p align="center">
  <strong>Private by Default. Compliant by Choice.</strong>
</p>

<p align="center">
  A shielded stablecoin wallet on <a href="https://stellar.org">Stellar</a> — private USDC payments powered by Zero-Knowledge Proofs, with selective disclosure for compliance.
</p>

<p align="center">
  <a href="https://stellar.org"><img src="https://img.shields.io/badge/Built%20on-Stellar-7D00FF?style=flat-square" alt="Built on Stellar"></a>
  <a href="https://noir-lang.org"><img src="https://img.shields.io/badge/Circuits-Noir-1C1C1C?style=flat-square" alt="Noir"></a>
  <img src="https://img.shields.io/badge/Proofs-UltraHonk-2B6CB0?style=flat-square" alt="UltraHonk">
  <img src="https://img.shields.io/badge/Network-Testnet-orange?style=flat-square" alt="Testnet">
</p>

---

## What we're building

Public blockchains expose every balance, payment, and financial relationship. Privacy networks hide everything — including from regulators. Neither works for real-world money.

DShield is the third model: **prove what's true, reveal nothing else.**

- 🛡️ **Shielded pool** — deposit USDC into a Merkle-tree commitment pool; withdraw to any address with a client-side ZK proof, breaking the on-chain link between depositor and recipient
- 🔁 **Trustless relayer** — the withdrawer's account never appears on-chain; recipient binding makes the relayer unable to steal, only refuse
- 🚫 **Double-spend proof** — nullifiers consumed on-chain; replayed proofs fail
- 📋 **Selective disclosure** — prove KYC status, jurisdiction, or balance thresholds to an auditor without exposing identity or unrelated transactions

All of this verifies **on-chain** using Stellar's native ZK primitives (Protocol 25/26: BN254 pairings, Poseidon hashing, MSM).

## Status

Live on **Stellar testnet** — a full deposit → ZK proof → relayed withdraw loop runs on-chain today, plus CLI-verified compliance and threshold-disclosure proofs. Currently fixed-denomination pools (10/100/1000 USDC tiers); arbitrary-amount private transfers are on the roadmap.

> ⚠️ Testnet demo — unaudited. Do not use on mainnet.

## Repositories

| Repo | Description |
| --- | --- |
| [`dshield`](https://github.com/dshield-xyz/dshield) | The monorepo: Soroban contracts (Rust), Noir circuits, and the Next.js wallet UI |

## Tech stack

**Contracts:** Rust / Soroban · **Circuits:** Noir + Barretenberg (UltraHonk, keccak transform) · **Hashing:** Poseidon2 (BN254) · **Frontend:** Next.js + Stellar Wallets Kit · **Tooling:** `just`, `stellar` CLI, `nargo`, `bb`

## Try it

```bash
git clone https://github.com/dshield-xyz/dshield && cd dshield
just setup          # check prerequisites
just test           # 85 contract + 50 frontend tests
just demo           # deposit → ZK proof → relayed withdraw, live on-chain
just demo-compliance # KYC registry → compliance proof → on-chain verification
```

---

<p align="center">
  Built for <strong>Stellar Hacks: Real-World ZK</strong> · <a href="https://github.com/dshield-xyz/dshield/blob/main/LICENSE">License</a>
</p>
