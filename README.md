Problem: Lack of Privacy & Trust in Order Matching
- In traditional finance, dark pools let institutions place large buy/sell orders without revealing them to the public book (to avoid front-running and slippage).
- In DeFi/crypto, all orders are public on-chain, which creates massive MEV/front-running risks.
- Current “fixes” (like batch auctions or commit–reveal) either add latency or still leak metadata.

CipherMatch is a peer-to-peer validator network that:
- Receives encrypted buy/sell orders from traders.
- Randomly selects a committee of validators. (t-of-n) https://github.com/yswa-var/SolMPC-Node
- Committee runs MPC order matching (essentially, runs a matching engine on encrypted orders).
    Example: binary search tree (BBO = best bid/offer).
- No validator sees the actual bids, but together they compute the matched pairs.
- Committee jointly produces a threshold signature on matched trades.
- A small random subset forwards the signed trades to a Solana smart contract for settlement.
- Solana verifies threshold signature → executes settlement.
