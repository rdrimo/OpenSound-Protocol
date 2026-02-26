# OpenSound Protocol (OSP)

> An open, decentralized protocol for music distribution. No platform. No company. Just a spec.

---

## What is this?

OpenSound Protocol is an open standard for how music can be published, distributed, and discovered — without requiring permission from any platform, company, or intermediary.

Think of it as HTTP for music distribution. Anyone can implement it. Nobody owns it. No server controls it.

OSP defines:
- How artists identify themselves (decentralized, cryptographic)
- How tracks are addressed and verified (content-addressed, immutable)
- How audio is distributed (peer-to-peer, streaming-capable)
- How music is discovered (decentralized, open)

It does **not** define a platform, a business model, or a token economy.

---

## Why?

The internet has open protocols for nearly everything:

| Use case | Protocol |
|---|---|
| Web pages | HTTP |
| Email | SMTP |
| Social networking | ActivityPub |
| Video streaming | WebRTC / HLS |
| File sharing | BitTorrent |
| **Music distribution** | ❌ nothing |

Every music streaming platform today is a centralized silo. Artists need permission to publish. Catalogs can be removed at will. Royalty structures are opaque. Platforms can disappear.

OSP is the missing protocol.

---

## How it works

OSP is built by composing existing proven standards rather than inventing new ones:

```
Identity       →  W3C Decentralized Identifiers (DIDs)
Content        →  IPFS content addressing (CIDs)
Streaming      →  WebTorrent (P2P, works in browser)
Metadata       →  JSON-LD signed Track Records
Discovery      →  DHT (Kademlia / libp2p)
Social layer   →  ActivityPub or Nostr (optional)
Payments       →  Lightning Network (optional extension)
```

A **Track Record** — the core data structure — looks like this:

```json
{
  "type": "osp:Track",
  "version": "0.1",
  "title": "Song Name",
  "artist": "did:key:z6Mk...",
  "duration": 243,
  "format": "audio/opus",
  "cid": "QmXyz...ipfs-content-hash",
  "torrent": "magnet:?xt=urn:btih:...",
  "released": "2026-01-15",
  "license": "CC-BY-SA-4.0",
  "signature": "base64-artist-signature"
}
```

The artist signs their own releases. No platform can forge or suppress them.

---

## Project structure

```
/
├── spec/               ← The protocol specification (CC0)
│   └── OSP-v0.1.md     ← Core spec document
├── whitepaper/         ← OSP whitepaper (PDF + source)
│   └── OSP-whitepaper-v0.1.pdf
├── reference/          ← Reference implementation (MIT)
│   ├── src/
│   └── README.md
├── oips/               ← OSP Improvement Proposals
│   └── OIP-0001.md     ← Template
└── README.md
```

---

## Status

**This is a public draft. Nothing is final. Everything is open for discussion.**

- [x] Initial whitepaper published
- [x] Core data model defined (Track Record)
- [ ] Layer 0 spec complete
- [ ] Reference CLI implementation
- [ ] Browser streaming proof of concept
- [ ] DHT discovery working
- [ ] First independent implementation

---

## Read the whitepaper

The full whitepaper — including the design philosophy, 4-layer architecture, governance model, and open questions — is in [`/whitepaper`](./whitepaper/).

It covers why previous decentralized music projects failed, how OSP is structured differently, and what problems remain unsolved.

---

## How to contribute

OSP is governed by a public RFC process. Changes to the protocol are proposed as **OSP Improvement Proposals (OIPs)**.

1. Read the [whitepaper](./whitepaper/) and [current spec](./spec/)
2. Open an issue to discuss your idea before writing a formal proposal
3. Submit an OIP using the template in [`/oips/OIP-0001.md`](./oips/)
4. Core spec changes require consensus among active maintainers
5. Extension layer proposals are more permissive

All contributors are welcome. You do not need permission to participate.

---

## License

- **Protocol specification** (`/spec`): [CC0 1.0 Universal](https://creativecommons.org/publicdomain/zero/1.0/) — public domain, no restrictions
- **Reference implementation** (`/reference`): [MIT License](./LICENSE)
- **Whitepaper** (`/whitepaper`): [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) — free to share and adapt with attribution

---

## Origin

This protocol was conceived on February 26, 2026, in a conversation between a human author and [Claude](https://claude.ai) (Anthropic AI). The whitepaper, architecture, and this README emerged from that dialogue.

The ideas draw on the work of the BitTorrent, IPFS, WebTorrent, Nostr, ActivityPub, and W3C DID communities. None of this is invented from scratch — it is assembled, with gratitude.

---

*OSP is a protocol, not a company. There is nothing to invest in, nothing to buy, and nobody to ask for permission.*
