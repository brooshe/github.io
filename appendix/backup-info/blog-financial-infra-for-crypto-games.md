---
description: Bringing DeFi innovations into crypto games
---

# ℹ️ BLOG: Financial Infra for Crypto Games

## Introduction

**As with any economy, a balanced and sustainable monetary system is fundamental to its success.** However, game economies have not found a balance between their money supply and demand. The extreme volatilities of these in-game currencies pose the greatest challenge for all stakeholders.&#x20;

The price of any in-game currency can be abstracted into the relationship between burning and minting. Burning is driven by ingame consumption such as upgrading, boosting, breeding, and transacting. Minting is driven by ingame activities such as quests and PvPs. While most attention is on tuning the intricate balance of burning (demand generation) and minting (supply generation), very few are thinking about the financial nature of these systems.

**In this piece, Aiko and I will bring several battle-tested DeFi primitives to fill the gap and embed them in a gamer-friendly way.**

### The Predicament of Crypto Games

The old monetization model is unsustainable. **Gold farmers continuously move from one game to another, creating false prosperities and leaving behind turmoils.** Even with the Ronin chain and a new Axie game, RON price has been halved and SLP is not seeing any upward momentum. Scholars had to leave this overcultivated land and migrate to other chains like Avax and Polygon. Pegaxy, which almost took over the Philippine market with 50k DAU, also failed to sustain itself. VIS (Pegaxy’s token) entered into hyperinflation as more players joined, and the price bottomed again in two weeks. Some large guilds also decided to liquidate their Pegaxy NFTs.

<figure><img src="../../.gitbook/assets/image (53).png" alt=""><figcaption><p>Pegaxy Holder Counts: <em>https://dune.xyz/shloked/Pegaxy</em></p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (52).png" alt=""><figcaption><p><em>$VIS Price Performance: https://www.coingecko.com/en/coins/vigorus</em></p></figcaption></figure>

To reduce massive token devaluation, some prevention measures have been **implemented but with limited success.** These inefficient measures are oftentimes tedious for developers to design. For example, Thetan Arena, a MOBA game with high playability and previous success on the mobile market, is one of the most popular crypto games with 8mn players. It is currently being valued at a $151mn market cap. Although gold sinks and battle limits are implemented to decrease inflation, it cannot avoid scholars grinding $THC and cashing out. $THC, the in-game currency, has been in a slow decline since the launch, falling nearly 99% in four months. Combine it with an illiquid NFT market, you quickly go into a price death spiral.&#x20;

<figure><img src="../../.gitbook/assets/image (51).png" alt=""><figcaption></figcaption></figure>

**Financializing the gaming experience introduces reflexivity into the system.** When there’s massive attention and asset appreciation, a new player might be tempted to buy the asset and try the game or use it as an investment opportunity and earn tokens in return. Regardless of their motives, when the token price suddenly drops, it can cause massive downward price reflexivity as different players front-run each other to exit the system.

Strong playability is essential but we also need safeguards around them to curb the reflexivity of these systems. Most developers are still trying to follow the traditional way to solve the inflation problem through gold sinks. **Why not turn to battle-tested financial infrastructures and embed them in a gamer-friendly version?**

## Current Innovations

I would love to first provide some background information on a few innovations in DeFi and crypto games. However, if you are familiar with AMMs in crypto games, Bancor V3, and ve(3,3), please feel free to skip to the next part.



> By leaning on existing Decentralized Exchanges, we can create highly liquid instant-settling trade markets for in-game assets that didn’t exist in past games. You always needed someone on the other side of the trade-in WoW or Runescape. In crypto, with Automated Market Makers, you don’t. - Nat Eliason

With an AMM, the protocol could bootstrap initial liquidity very easily and earn additional transaction fees. Since the protocol controls both sides of the liquidity, initializing the liquidity pool is easy and prediction about future price movement is also within grasp (more on this later). As the majority liquidity owner of these liquidity pools, the protocol could also earn an additional trading fee from user activities.

### Bancor V3

Bancor launched in mid-2017 as the first AMM. It is one of the most under-the-radar projects in the entire DeFi space. Different from most AMMs where you can create any pool between any tokens, Bancor requires all tokens to be paired with BNT (Bancor’s native token).

<figure><img src="../../.gitbook/assets/image (50).png" alt=""><figcaption></figcaption></figure>

**The name “Bancor”** comes from the famous economist John Maynard Keynes’ currency conception called the “International Clearing Union (ICU)” - **an economic unit that is the basis of all settlement and denomination.** Although the initial idea did not materialize in the Ethereum world, the parallelism between Bancor’s vision and the game economy is apparent. In games, the basic economic unit is determined by the protocol. In Axie, it is $SLP. In Crypto Raiders, it is $AURUM. So maybe Bancor’s design philosophy is best fitted in an ingame economy.

In the next two sections, I will introduce Bancor’s newest innovations: the Omnipool AMM and the Bancor Vortex.

#### Omnipool AMM

Bancor’s Omnipool AMM allows trading against a central liquidity pool. In the traditional AMM model, all liquidity is fragmented because there is no common denomination (numeraire). In the example below, Token A has a deep liquidity pair against Token X but medium liquidity pairs against Token B and Token C (an intuitive example could be: Token X = ETH, Token A = any token, Token B = USDC, Token C = USDT). This design introduces composability but adds a layer of complexity, leading to fragmented liquidity across different pairs.&#x20;

<figure><img src="../../.gitbook/assets/image (49).png" alt=""><figcaption></figcaption></figure>

**Bancor’s Omnipool model uses only one denomination.** All liquidity is paired against BNT, Bancor’s native token. In this design, all the liquidity in the denomination token is pooled together, facilitating a better trading experience across all trading pairs.

#### Vortex

Vortex is an innovative method to **achieve highly capital-efficient token buybacks.**

One common way for protocols to support token prices is through token buybacks. **Protocols would use a portion of their revenue to conduct buybacks through the open market**. The buyback tokens are normally distributed to token holders (stakers) or burnt.

**Bancor’s Vortex system aims to buy back tokens at a discount.** To achieve such a feat, Bancor enables liquid staking for users. After staking BNT into the system, stakers can exchange their vBNT (staked BNT) for BNT through the Vortex system. The current Vortex can be thought of as an AMM pair between BNT and vBNT. If people want liquidity out of their staked positions, they can trade out of it through the Vortex. As more people sell their vBNT for BNT, the vBNT price decreases against BNT. Currently, in Vortex, 1 vBNT can be traded for 0.6 BNT. For sellers of vBNT, to redeem their staked BNT, they will need to buy their vBNT back at a later date.

<figure><img src="../../.gitbook/assets/image (48).png" alt=""><figcaption><p>Process flow for vBNT staking and Vortex</p></figcaption></figure>

Since both vBNT and BNT represent 1 BNT, the protocol could buy vBNT at a discount and burn it, effectively removing BNT from the supply. **For example, if the protocol makes $1mn a year and the BNT price is $1, with the traditional buyback model, Bancor could only take 1mn BNT out of circulation. With Vortex, it could take 1.7mn (1 / 0.6) BNT out of circulation, an increase of 67%.**

### Vote-escrow & ve(3,3)

The term ve(3,3) is proposed by Andre Cronje, aiming to combine Curve’s vote-escrow (ve) model with Olympus’s (3,3) to ensure voters’ power is never diluted.

<figure><img src="../../.gitbook/assets/image (47).png" alt=""><figcaption><p>Curve DAO’s governance page</p></figcaption></figure>

In the traditional ve model, token holders can lock their CRV (Curve’s native token) in exchange for veCRV. veCRV is the governance token for the Curve DAO where they decide on the provision of future liquidity rewards. The exchange rate between veCRV and CRV is based on a linear function to time. At 4 year lock up, 1 CRV = 1veCRV. At 1 year, 1 CRV = 0.25 veCRV.

veCRV holders receive platform trading fees from the protocol. For example, if on a given day Curve generates $1mn in trading fees to the protocol, and there are 1mn veCRV tokens in supply, for each 1 veCRV you hold, you will receive $1 in return. (The actual numbers and percentages are different.)

veCRV is by nature non-transferable. However, people have found ways to circumvent this design through different wrapping mechanisms. With Andre’s ve(3,3) design, after locking the token it will transfer the token into an NFT where people can trade on the secondary market not as liquid tokens but as less-liquid NFTs. **Although Andre appraises this design for its future financialization merits, locking tokens into an NFT is much more exciting in the game space.**

## Avengers Assemble!

**Now, what do we do with these innovations?**

I propose the \[BLOG] Design for crypto games. **BLOG** stands for **B**uybacks, **L**ocking, **O**mnipool, and **G**overnance.

<figure><img src="../../.gitbook/assets/image (46).png" alt=""><figcaption><p>Flowchart of All Interactions within BLOG</p></figcaption></figure>

In this design, I aim to 1) **increase trading experience** through an all-inclusive AMM, 2) **decrease token sell pressure** through long-term locking, 3) **increase locked token utility** through governance control, and 4) **increase token buying pressure** through efficient buybacks.

**From the gamer's perspective, this design is extremely simple and easy to understand.**

1. Gamers trade items with an instant settlement under the same UI.
2. Gamers lock their GOLD into the Bank (Locking Contract) for veGOLD and earn passive income. Just like a deposit into a bank.
3. Gamers purchase honorous titles (govNFT) with their veGOLD (after passing some nonfinancial requirements) for cosmetics (and/or stats boost) and governance power.&#x20;
4. Gamers can sell (through Vortex) their veGOLD (locked GOLD) for GOLD.

Before I continue, I always want to iterate that I am simply combining existing designs and am standing on the shoulders of the giants before me. Thank you to all the DeFi and crypto game innovators and let’s continue.

### Trading Experience

**Not all items within a game should be an NFT.** Within traditional crypto game projects, the most important assets are the NFTs. Axies for Axie Infinity, Pega in Pegaxy, Crab in Crabada, and Raiders for Crypto Raider. However, not everything in a game should be an NFT (ERC721). For example, let’s imagine a traditional fighting RPG game. In this simple game, the player has a sword and a shield. Each of these items has its unique stats. Therefore, they should be considered NFTs because they are not fungible. Your sword is not my sword. No problem here. When a player enters the wild to fight monsters, he collects different drops. Think of these drops as meat, bones, gems, etc. These items are not unique anymore, they are fungible. All meat is equal, all gems are equal, so on and so forth. Some of you MMORPG players are thinking now, **“But what about different gems? They are not fungible.”** You are correct. Within gems, a strength gem is not the same as a speed gem. However, you can design a strength gem as an ERC20 and a speed gem as another ERC20. They are not fungible across each other but fungible within one another - My strength gem equals your strength gem (fungible within) my speed gem is not my strength gem (not fungible across). The same concept can be also expanded into levels of gems as well.

**Thinking about crypto games from a “fungible asset” perspective, we can utilize Bancor’s Omnipool AMM to facilitate a better trading experience.** I will call these fungible items “commodities” from now on. In traditional games and current crypto games, all items are traded through an order book. An order book is where buyers and sellers post their desired prices for the commodities they want to sell or buy. **For low-liquidity commodities, this may not be the best approach.** If I want to sell some gems I collected a few days ago, I have to post a sell order to the order book and wait for an indefinite amount of time until another person buys it. **With an Omnipool AMM, I can trade any number of gems instantly just like how I normally would sell my MATIC or ETH on Uniswap.** The same applies if I were the buyer and want to buy some commodities. **Omnipool eliminates the need for counterparty in any trade and enables a much better experience for trading ingame commodities.**

<figure><img src="../../.gitbook/assets/image (45).png" alt=""><figcaption></figcaption></figure>

**With Omnipool, the protocol could also have more nuanced control over commodities’ price discovery.** In the order book model, liquidity is made up of different players buying and selling these commodities. When we change it to the Omnipool model, the protocol could bootstrap the pool with a certain amount of liquidity to better control the price movement of its commodities. **This change is achieved through printing both sides of the pool and owning the liquidity. For example**, going back to the fighting game, the protocol wants to introduce gems into the game. The protocol could bootstrap the GEM/GOLD pair with 100,000 GEM and 1,000,000 GOLD, implied price (1 GEM = 10 GOLD). If the protocol will emit 1,000 - 2,000 gems in the next month based on user activity, they can calculate the **lowest possible price** of a gem by assuming everyone sells their gems for gold. This information could help teams to build more robust models for the ingame economy.

By controlling the liquidity, protocols could even deploy more granular approaches. Another example could be: when there’s a sudden influx of players who need gem, causing gem price to spike up. To curb the sudden price increase, the protocol could increase the depth of the liquidity pool by printing and adding both sides into the Omnipool. The same approach could be used when the price crashes as well.

_Note: protocol printing these tokens should be communicated to the player base or through governance._

### Long-term Locking

**Long-term locking is low-hanging fruit for decreasing sell pressure. Many DeFi projects have adopted such a design to curb emission and increase long-term value alignment between token holders and the protocol.** One of the major criticisms of locking is the illiquidity imposed on the token. This is the case for many DeFi tokens, however less problematic for ingame tokens. Ingame tokens are by nature highly inflationary and liquid, making locking much more valuable and constructive.

In \[BLOG], gamers can lock their GOLD in exchange for veGOLD through the locking contract. An exchange rate can be determined through any function of time. For example, the gamer could lock its GOLD for a year and receive 0.5 veGOLD, or lock it for two years and receive 1 veGOLD. The longer the gamer locks, the more rewards and governance power he/she gets.

<figure><img src="../../.gitbook/assets/image (44).png" alt=""><figcaption></figcaption></figure>

To utilize GOLD in the contract, the protocols could direct it as liquidity into its Omnipool to earn a trading fee. This way, there’s a native yield for locking GOLD without the protocol printing more tokens into the system. However, this may not be enough due to a wide array of reasons (IL & low APR). Protocols could then boost up locking APR through traditional liquidity rewards (with or without vesting).

By locking GOLD into the locking contract, the protocol effectively removes it from the circulating supply and decreases sell pressure.

### Locked Token and Governance in Crypto Games

One major reason for locking tokens in a DeFi protocol is to ensure long-term value alignment. Therefore, most of the governance decisions are decided by the locked **token holders.** In the context of crypto games, it is not doable for two reasons. First, most games already have a duo token system. Second, more importantly, token balance for governance is not the most appropriate format for games. **Gamers should not be thinking about detailed and often time large numbers when playing a game. Therefore, for these reasons, I introduce govNFT to tackle these problems.**

**On a high level, after receiving veGOLD, gamers could spend it to purchase these govNFTs (titles).** These govNFTs, based on their tiers, would grant players different cosmetics effects, abilities, and also governance power to make simple governance decisions.

<figure><img src="../../.gitbook/assets/image (43).png" alt=""><figcaption></figcaption></figure>

**These governance decisions could be really interesting and let me give you an example of how this could play out.**

After a while, the game has matured and there are different clans and guilds inside the game. Clan A is made up of warriors. Warriors can kill monsters easily but are weak against wizards, another enemy. Each monster killed will give the gamer 9 meat and 1 gem. So warriors have much fewer gems. Clan B on the other hand is made up of mages. Mages can kill wizards very easily but are weak against monsters. Each wizard killed gives the gamer 9 gems and 1 meat. Since each clan has one side of the resource in excess, both clans could engage in trading and ensure the resources are exchanged effectively.

**Now we introduce a simple governance structure: every week, the game will boost the killing rewards by 5 and resets every month.** These 5 rewards could be all meat - (monster kill = 14 meat + 1 gem) (wizard kill = 9 gem + 6 meat) or all 5 could be gem (monster kill = 9 meat + 6 gem) (wizard kill = 14 gem + 1 meat). For the full breakdown, see the table below.

<figure><img src="../../.gitbook/assets/image (42).png" alt=""><figcaption></figcaption></figure>

The final rewards distribution will be determined by the votes. If 80% vote for gem and 20% vote for meat, then the rewards will increase all kills with 4 gems and 1 meat. If the votes are 40% for gem and 60% for meat, then the rewards will increase all kills with 2 gems and 3 meat. The yellow row represents the mage's goal and the blue row represents the warrior’s goal.

**With this simple governance structure, the game suddenly has an interesting game theory dynamic.** Warriors want the rewards to be 5 gems and 0 meat while mages want the rewards to be 0 gems and 5 meat. Each clan would want their earnings not to be diluted by the rewards. This competition increases the need for governance power. Where does governance power come from? It comes from the govNFTs, and govNFTs come from veGOLD, and veGOLD comes from GOLD.&#x20;

<figure><img src="../../.gitbook/assets/image (41).png" alt=""><figcaption></figcaption></figure>

If you are a DeFi native, you might realize that this design comes from Curve’s gauge design which gives veCRV holders the ability to direct liquidity rewards to different pools. **In \[BLOG] design, I gamify the entire voting procedure and let gamers decide based on their interests.**

Through this approach, it does not dilute the governance power of the govToken holders. These game designs are currently decided by game developers. The govToken holders do not have any influence on these decisions currently, and their governance power is generally assumed to be around major game development directions.

### Efficient Token Buyback

To close off the entire \[BLOG] design, I introduce the Vortex system to enable efficient token buybacks.&#x20;

**Token buyback is a method to increase native token buying pressure through exchanging protocol revenue for native tokens.** **However, this design is powerless in the crypto game space.** Each game can be thought of as an individual system. The closed-system design introduces a barrier for crypto games to do token buybacks. If all the revenue in my example game is generated through GOLD (or other commodities), the best I can do is burn it. So for 1 GOLD in revenue, I can burn 1 GOLD from the supply. It is not ideal. If you are familiar with time discounting, this would make more sense. If not, no worries.

Here is where Vortex comes in.

**From the gamer point of view**, after locking their GOLD into the Bank, they can either 1) hold on to veGOLD to earn interest or 2) spend it to buy govNFTs. Now with Vortex, **they can sell their veGOLD for GOLD.** This is useful for gamers because they might need GOLD for a wide range of ingame purposes. The veGOLD/GOLD Vortex system can be thought of as a liquidity pair on Uniswap v2. So users can offload their veGOLD anytime based on market demand and supply.

By buying veGOLD with game revenue, the protocol could guarantee to have a more efficient token buyback system. Imagine my fighting game earned 1mn GOLD in protocol revenue and I would want to reduce circulating supply. I could buy 1mn+ veGOLD through the vortex and burn them. Since each veGOLD represents 1 or more GOLD, this is more capital efficient. Remember the exchange rate between GOLD and veGOLD is capped at 1 because you can always mint 1 veGOLD with 1 GOLD from the Bank.

<figure><img src="../../.gitbook/assets/image (39).png" alt=""><figcaption></figcaption></figure>

## Final Words

**The crypto game’s economy is an emerging field with the possibility to onboard the first billion users onto crypto.** I do not want their first experience in crypto to be the same as mine - seeing their portfolios go down 50% in a week. We need a more robust in-game system to mitigate such risks if we cannot eliminate them right away. In this post, we proposed BLOG: a new economic model for crypto games involving AMM, token locking, governance, and buybacks. **This general framework, while useful, should be tailored to each project’s goal during implementation.** Due to its modular design structure, projects could also only use a subset of the whole design. **I hope this design could be useful for crypto game projects and let’s all work together to onboard the next billion users!**

## References

1. [Alienated Playbour: Relations of Production in EVE Online](https://journals.sagepub.com/doi/pdf/10.1177/1555412014565507)
2. [EVE is Real](https://kellybergstrom.ca/wp/wp-content/uploads/2015/04/EVE\_is\_Real\_final.pdf)
3. [The Case for Dynamic Difficulty Adjustment in Games](https://dl.acm.org/doi/pdf/10.1145/1178477.1178573)
4. [Building Sustainable Web3 Games with Owned Liquidity & Tokenized Assets](https://every.to/almanack/building-sustainable-web3-games-with-owned-liquidity-tokenized-assets)
5. [Introducing Bancor 3](https://blog.bancor.network/introducing-bancor-3-962a3c601c25)
6. [BIP15: Proposing Bancor 3](https://docs.google.com/document/d/1WFMWRCOqgYHuWXeT02n82f044EDmReGg9hhdeS3TEY8/edit#heading=h.dhq318m9x0qp)
7. [State of Crypto Raiders Economy Snapshot](https://medium.com/@web3econ/state-of-crypto-raiders-economy-snapshot-823e008bbd4a)
8. [Understanding Curve](https://resources.curve.fi/base-features/understanding-curve)
9. [Staking your CRV](https://resources.curve.fi/guides/staking-your-crv)
10. [The mythos of Curve Finance](https://theknower.substack.com/p/the-mythos-of-curve-finance?s=r)

> [https://kydo.substack.com/p/blog-financial-infrastructures-for](https://kydo.substack.com/p/blog-financial-infrastructures-for)
>
> Authors: Kydo & Aiko
>
> _Acknowledgment is always on top: thank you Nat and Nicolas (Crypto Raiders), Nate (Bancor), Jason (Folius), Jerry (Stepn), TY (Cradlesio), PhABC and Salvator (Horizon), Bailey (Defiance), Cyn Bahati (moongateguild), and Raymond Chng for making this piece possible._
