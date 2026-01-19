# ZK Private Pass 🔒✨  
**Anonymous, verifiable membership + one-time actions using Zero-Knowledge proofs (on-chain verification).**

## What this is
**ZK Private Pass** is a smart-contract system that lets a user prove they are an approved member (or eligible for an action) **without revealing their identity** — and still enforces **one-time usage** through **nullifiers** (prevents double-claims/votes).

This repo demonstrates an end-to-end zero-knowledge pipeline:
- **ZK circuits → proof generation → on-chain verification → application logic**
- Membership is represented as a **Merkle tree**
- Access / claim / vote is gated by a **ZK Merkle membership proof**
- **Nullifiers** prevent replay & double-use while preserving privacy

Think: private allowlists, anonymous voting, private airdrop claims, KYC gating without doxxing.

---

## Why it matters (what employers look for)
This project is intentionally built to showcase protocol-level engineering skills:
- Designing privacy-preserving protocols with correct threat modeling
- Building ZK circuits and understanding public vs private inputs
- Verifying proofs on-chain efficiently (Solidity verifier contracts)
- Using Merkle trees for scalable membership
- Preventing replay with nullifiers (anonymous “use once” primitive)
- Writing tests that cover invalid proofs, stale roots, and replay attempts

---

## Core features
✅ **Anonymous membership proof** (Merkle inclusion inside ZK)  
✅ **Nullifier-based replay protection** (claim/vote once, anonymously)  
✅ **On-chain proof verification** (Solidity verifier contract)  
✅ **Root management** (support for updating allowlists over time)  
✅ **Clean architecture**: circuits, contracts, scripts, tests, frontend separated

---

## Tech stack
### ZK
- **Circom** — circuit language for building ZK constraints  
- **snarkjs** — setup, proving, verification key generation, Solidity verifier export  
- **Groth16** (proof system) — widely supported + efficient on-chain verification

### Smart contracts
- **Solidity** — application + verifier integration  
- **Hardhat (TypeScript)** — compile, deploy, test, scripts

### App / tooling
- **Node.js + TypeScript** — proof generation scripts, Merkle tree utilities  
- (Optional) **Next.js** frontend for wallet UX + local proof generation

---

## Repository structure
```txt
zk-private-pass/
  circuits/              # Circom circuits (membership, nullifier, etc.)
  contracts/             # Solidity contracts (Verifier + PrivatePass logic)
  scripts/               # Proof generation, Merkle tree utilities, deploy scripts
  test/                  # Hardhat tests (valid/invalid proofs, replay, root checks)
  frontend/              # (Optional) Next.js UI for generating/submitting proofs
