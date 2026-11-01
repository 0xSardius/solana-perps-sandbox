# solana-perps-sandbox

Exploratory sandbox for app ideas built on Solana perpetual-futures protocols.
Early stage: no code yet. See `IDEAS.md` for the idea backlog.

## Working agreements
- Prototype fast, but **never put private keys, seed phrases, or RPC API keys in the repo**.
  Use env vars (`.env` is gitignored) — e.g. `SOLANA_RPC_URL`, `KEYPAIR_PATH`.
- Default to **read-only / devnet** first. Anything that signs mainnet transactions
  must be opt-in behind an explicit flag and reviewed.
- Treat on-chain amounts as integers in base units (respect each protocol's
  precision constants); never use floats for money math.
- Each prototype lives in its own folder under `apps/<name>/` with its own README
  covering: what it does, how to run it, which protocols/accounts it touches.

## Likely stack (update as decisions are made)
- TypeScript + `@solana/web3.js` / protocol SDKs (Drift, Jupiter Perps, etc.)
- Python acceptable for data/analysis scripts.
- Rust/Anchor only if we actually need an on-chain program.

## Notes for Claude
- The user often works from their phone: keep replies scannable, summarize diffs,
  and prefer small, self-contained commits.
- Verify protocol SDK APIs against current docs before writing integration code —
  these SDKs change frequently.
