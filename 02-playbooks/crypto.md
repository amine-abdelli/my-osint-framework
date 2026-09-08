# Playbook — Cryptocurrency address

**Use when:** a wallet address appears — typically in a fraud, extortion or scam case.

---

## 1. Identify the chain

| Currency | Address format |
| --- | --- |
| **Bitcoin** | Starts with `1`, `3`, or `bc1` |
| **Ethereum** | `0x` + 40 hex characters |
| **Litecoin** | Starts with `L`, `M`, or `3` |
| **Monero** | Starts with `4` or `8`, 95 characters |
| **Solana** | Base58, ~44 characters |

⚠️ Some chains are case-sensitive. Record the address **exactly**, and verify by checksum
where the chain supports it. A transposed character is a different wallet.

## 2. Scam database lookups

Check before analysing — the address may already be documented.

- **ChainAbuse** — `chainabuse.com/address/<ADDRESS>` (multi-chain)
- **BitcoinAbuse** — reports of scam Bitcoin addresses
- **CryptoScamDB** — `cryptoscamdb.org/search`

Screenshot and archive every hit.

## 3. Blockchain explorer analysis

```bash
# Bitcoin
curl -s "https://blockchain.info/rawaddr/ADDRESS?limit=50" | jq

# Ethereum — API v1 was fully deprecated 2025-08-15; v2 requires chainid (1 = mainnet)
curl -s "https://api.etherscan.io/v2/api?chainid=1&module=account&action=txlist&address=ADDRESS&apikey=YOUR_KEY" | jq
```

Explorers: blockchain.info · Etherscan · BlockCypher (multi-chain).

Record: total received and sent, transaction count, first and last transaction timestamps,
current balance, and linked addresses.

## 4. Trace

1. **First funding source** — often reveals the on-ramp, and on-ramps are usually KYC'd.
2. **Outgoing transactions** — follow the flow.
3. **Exchange deposits** — the point at which crypto meets identity. Cluster analysis
   tools: OXT, Breadcrumbs.
4. **Address clustering** — wallets controlled by the same entity. Common-input heuristics
   group addresses that co-signed a transaction.

⚠️ Monero and privacy coins do not support this analysis in any meaningful way.
Mixers, coinjoins and cross-chain bridges break the trail deliberately.

## 5. Document

- Full address, case-exact
- Chain and explorer URL
- Total transacted, in crypto **and** approximate fiat, with the rate and date used
- Scam database results, with screenshots
- Transaction screenshots with timestamps
- Any cluster or exchange attribution, and its confidence level

## 6. Report

For a fraud case, the crypto address feeds the abuse-reporting workflow
([`domain-ip.md`](domain-ip.md) §Abuse reporting) — exchanges are reportable parties, and
a documented deposit to a compliant exchange is one of the few routes to real-world
identification.

---

## Sources

- Pnwcomputers, *OSINT Guide* — Cryptocurrency Investigation Procedure
- i-intelligence, *OSINT Handbook 2018* — Cryptocurrencies (17 entries)
