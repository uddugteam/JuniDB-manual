# Introduction

`JuniDB` is a [Substrate] database powered by [`offchain::ipfs`].

By using IPFS power in the native
Substrate runtime, and by allowing pass-through wasm calls via Substrate's
[Off-chain Workers], we enable a powerful tool to store data in KEY-VALUE model:

- `set` - store data with specific key to DB
- `gey` - Read data from DB by provided key

Manual have updated to Sybstrate v3 by: [@andskur] and [Uddùg team]

## Disclaimers

You should still consider this an **alpha preview**.

[`offchain::ipfs`]: https://github.com/uddugteam/substrate/tree/offchain-ipfs-v0.3
[Substrate]: https://substrate.io
[Off-Chain Workers]: https://docs.substrate.io/v3/concepts/off-chain-features/
[Uddùg team]: https://github.com/uddugteam
[@andskur]: https://github.com/andskur