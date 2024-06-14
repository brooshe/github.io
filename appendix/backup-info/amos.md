# ⚙️ AMOs

Algorithmic market operations (or AMOs), also referred to as direct deposit modules, are operations performed by contracts to mint or burn stablecoins without collateral immediately backing these stablecoins. Stablecoins minted by AMOs are still controlled by the protocol, and if other people start controlling these stablecoins, then this new supply should be properly backed in one way or another.

AMOs are conceived not to affect the peg of the stablecoin.

#### Liquidity AMOs <a href="#liquidity-amos" id="liquidity-amos"></a>

Protocol also uses liquidity AMOs to seed some pools with  MSC and/or USDM liquidity. The idea is to either match some of the protocol's reserves with MSC/USDM minted from AMOs or to mint both MSC and USDM to provide liquidity.

In this last case, MSC ends up being backed by SDM  when people swap USDM to MSC and conversely, and the balance sheets of the two stablecoins become correlated up to the size of this AMO.

While liquidity AMOs expose the protocol to a potential divergence loss + loss versus rebalancing risk, they also help bootstrapping stablecoins liquidity without relying on individual LPs from start. Their size and balances are in any monitored in real-time to make sure that the potential loss or bad debt never grows beyond an acceptable size with respect to the protocol equity.

### Implications of AMOs <a href="#implications-of-amos" id="implications-of-amos"></a>

By making stablecoins more easily accessible on some protocols, AMOs widen the user base of the protocol. They can also be an interesting source of revenue for the protocol (from lending yield or transaction fees).

It's important to note though that AMOs are not completely neutral on the protocols on which they are taking place. On a lending market for instance, having an AMO reduces both the deposit and borrow APYs hence reducing yield opportunities for lenders while making it easier for borrowers.

Another issue as well is that having AMOs on a protocol (like Aave or Morpho) means that the risk of Angle becomes to some extent the risk of the underlying protocol. If Angle lends 1m EURA on Aave and Aave gets hacked, then the Angle protocol also makes a loss.

As such, AMOs are a powerful tool to expand Angle stablecoins use cases in DeFi as well as protocol revenue, but they do not come without any risk, and every new AMO type is carefully calibered by protocol governance to control systemic risk before being put in place.
