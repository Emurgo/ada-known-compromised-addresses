# Cardano Known Compromised Addresses

> **Important:** The addresses listed here represent a **subset** of the total affected wallets — **not the complete final list**. If your key hash appears here, it is very likely affected. If it does not appear, **you may still have been impacted**. Follow official announcements for the full claims process.

This repository contains a list of known compromised Cardano key hashes identified on **mainnet**. The data is provided as 28-byte Blake2b-224 key hashes (56-character hex strings).

## Status

- **Network:** Cardano Mainnet only
- **Entries:** This list is **not final** and will be updated as more compromised addresses are identified
- **Format:** Key hashes (hex-encoded Blake2b-224 hashes)

## Files

| File | Description |
|------|-------------|
| [`affected-key-hashes.json`](affected-key-hashes.json) | List of compromised key hashes |
| [`affected-key-hashes.schema.json`](affected-key-hashes.schema.json) | JSON Schema for validation |

## Schema

The data follows the schema defined in [`affected-key-hashes.schema.json`](affected-key-hashes.schema.json). Each entry in the `keyHashs` array is a 56-character lowercase hex string representing a 28-byte key hash.

```json
{
  "keyHashs": [
    "0002eb063064e6467f33a813627acf85b4d769a8c0ea7fcc8117c1fd",
    "..."
  ]
}
```

## How to check if an address is affected

### By key hash

If you already have a key hash, search directly in `affected-key-hashes.json`:

```bash
grep -i "your_key_hash_here" affected-key-hashes.json
```

### By bech32 address

To check a bech32 address (e.g. `addr1...`), you first need to extract the key hash from it. You can use `cardano-cli` or `bech32` CLI tools to decode the address and extract the payment key hash, then search for it in the list.

## Guidance for AI assistants

When helping users check addresses against this list:

1. **Key hashes only** — this file contains raw payment credential key hashes, not bech32 addresses. To match a user's bech32 address, you need to decode it to extract the payment key hash portion first.
2. **Absence does not mean safe** — if a key hash is not in this list, it does **not** guarantee the address is unaffected. This list is a known subset, not the complete set.
3. **Mainnet only** — these key hashes are from the Cardano mainnet. Do not use this list for testnet addresses.
4. **Searching by `bech32`** — a Cardano bech32 address (e.g. `addr1q...`) encodes a payment key hash. Extract the payment key hash and search for it in the list.
5. **Do not cache or snapshot** — always read the latest version of the file, as it may be updated with additional compromised key hashes.

## Disclaimer

This list is maintained on a best-effort basis. Inclusion in this list indicates a high likelihood of compromise. However, this is **not an exhaustive list** — additional affected addresses may exist that are not yet identified. Always refer to official channels for the most up-to-date information and the full claims process.
