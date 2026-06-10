# Opaque Protocol

Opaque is an open, cross-chain privacy protocol for unlinkable stealth payments and privacy-preserving verifiable reputation. It runs on Ethereum and Solana, with a TypeScript SDK and reference wallet implementations.

## Core Primitives

**Stealth Payments (DKSAP)**
Recipients publish a single meta-address (a viewing key and a spending key). Every inbound payment lands at a fresh, one-time address derived on the sender side using secp256k1 ECDH. The sender and recipient are cryptographically unlinkable on-chain. Compatible with EIP-5564 and ERC-6538.

A one-byte view tag lets recipients skip roughly 99.6% of on-chain announcements before any elliptic curve work, making client-side scanning practical at scale.

**Programmable Stealth Reputation (PSR)**
Schema-bound attestations issued to stealth addresses. Recipients prove traits (KYC status, DAO membership, credit tier) using Groth16 zero-knowledge proofs without revealing their wallet, identity, or unrelated credentials. Nullifier-based Sybil resistance prevents replay across contexts.

**Universal Announcement Bus (UAB)**
Cross-chain announcement relay over Wormhole. A payment announced on Ethereum can be scanned and swept from Solana, and vice versa, through a compact 96-byte on-chain payload.

## Repositories

| Repo | Description |
|------|-------------|
| [opaquecash/sdk](https://github.com/opaquecash/sdk) | TypeScript monorepo: 12 packages covering stealth core, chain adapters (EVM + Solana), ZK proving, UAB, balance aggregation, and a unified `OpaqueClient` |
| [opaquecash/ethereum](https://github.com/opaquecash/ethereum) | Solidity contracts, Hardhat deployment, and reference React wallet |
| [opaquecash/solana](https://github.com/opaquecash/solana) | Anchor programs, Rust WASM scanner, and reference React wallet |
| [opaquecash/circuits](https://github.com/opaquecash/circuits) | Circom V2 circuit (canonical), Groth16/BN254, Merkle depth-20; V1 frozen for backward compatibility |
| [opaquecash/relayer](https://github.com/opaquecash/relayer) | Off-chain relay service for Wormhole VAA delivery to Solana |
| [opaquecash/spec](https://github.com/opaquecash/spec) | Protocol specifications: CSAP, PSR V2, UAB, and payload format |

## Technical Stack

- **Cryptography:** secp256k1 ECDH, Keccak-256, Groth16 over BN254
- **ZK verification:** Native on-chain via Solana `alt_bn128` syscalls and Ethereum `ecPairing` precompile
- **Cross-chain transport:** Wormhole Core (Ethereum Sepolia, Solana devnet)
- **Browser scanning:** Rust compiled to WASM, no server dependency
- **Standards:** EIP-5564, ERC-6538, Wormhole VAA format

## Status

The protocol is live on testnet (Ethereum Sepolia and Solana devnet). All contracts are deployed and cross-chain announcement flows in both directions have been verified. The SDK packages are published under the `@opaquecash` scope.

Mainnet deployment is gated on a ZK trusted setup ceremony and security review. The software is experimental.

## Links

- Documentation: [docs.opaque.cash](https://docs.opaque.cash)
- Specification: [spec/](https://github.com/opaquecash/spec)
- License: Apache-2.0 (SDK, spec), GPLv3 (Ethereum), MIT (Solana), CC0 (circuits), AGPL-3.0 (relayer)
