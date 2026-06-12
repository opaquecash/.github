# Opaque Protocol

An open, serverless, cross-chain privacy protocol on **Ethereum** and **Solana**:
payments that can't be linked to you, credentials you can prove without revealing who
you are. Every layer is specified before its code, so any wallet or dApp can implement
compatibility — the Opaque apps are reference implementations, not the only ones.

## What it does

| Layer | In one line | Spec |
|---|---|---|
| **Stealth payments** | Every payment lands at a fresh one-time address only the recipient controls (DKSAP, EIP-5564/ERC-6538-compatible; client-side WASM scanning via 1-byte view tags) | [CSAP](https://github.com/opaquecash/spec/blob/main/CSAP.md) |
| **Stealth reputation (PSR)** | Prove a credential (KYC, membership, score) with a Groth16 ZK proof — without revealing your wallet or other traits | [PSR](https://github.com/opaquecash/spec/blob/main/PSR.md) |
| **Cross-chain announcements (UAB)** | A payment announced on one chain is scannable from the other, over Wormhole | [UAB](https://github.com/opaquecash/spec/blob/main/UAB.md) |
| **Naming (ONS)** | `alice.opq.eth` resolves the same meta-address from either chain | [ONS](https://github.com/opaquecash/spec/blob/main/ONS.md) |
| **Relayer market** | Gas-private on-chain submission through staked, slashable relayers | [relayer-market](https://github.com/opaquecash/spec/blob/main/relayer-market.md) |
| **Privacy pool** | Amount privacy with association-set compliance proofs (Privacy Pools model — not a mixer) | [privacy-pool](https://github.com/opaquecash/spec/blob/main/privacy-pool.md) |
| **Conditional disclosure** | M-of-N custodians authorize selective, single-transaction disclosure — the full viewing key never exists in one place (FROST) | [conditional-disclosure](https://github.com/opaquecash/spec/blob/main/conditional-disclosure.md) |

## Status

Every layer above is **live on testnet** (Ethereum Sepolia + Solana devnet) with
end-to-end acceptance verified. **Experimental, testnet-only software** — mainnet is
gated on circuit/contract audits and a production trusted-setup ceremony.

[Docs](https://docs.opaque.cash) · [Quickstart](https://docs.opaque.cash/quickstart) · per-repo licenses (Apache-2.0 / GPL-3.0 / MIT / CC0)
