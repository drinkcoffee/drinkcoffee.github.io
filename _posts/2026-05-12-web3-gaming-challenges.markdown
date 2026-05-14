---
layout: post
title:  "Web3 Gaming Challenges"
date:   2026-05-12 11:00:00
categories: web3 gaming
---

Web3 gaming has had some success with Axie Infinity and Gods Unchained, but has failed to gain mainstream traction. This article explores the challenges of creating successful web3 games.

Before I start on the challenges, please keep in mind the substantial advantages of web3 games: true ownership of assets, open player economies allowing trading and loaning of assets, the possibility for decentralised governance, plus transparency and fairness.

In the article I use the terms _many game players_ and _some game players_. This is based on anecdotal discussions only, and not quantitative research.

# Game Players & Wallets

Game players need a wallet to play web3 games. The wallet shows what assets a player owns. This often drives what the game player can do in-game. In some games, players earn and / or spend NFTs and ERC 20 tokens as a part of game play. 

Most cryptocurrency wallets use BIP 39 seed phrases as the secret from which private keys are generated. Even experienced deeply technical people sometimes lose their seed phrase and are then unable to access their assets. Additionally, with this type of wallet, every transaction must be signed. This complexity of needing to remember a seed phrase along with the interrupted game play of needing to sign all transactions makes this type of wallet inappropriate for web3 gaming. 

Web3 gaming wallets such as Immutable's Passport, are facilitated via social login. That is allowing logging into the wallet via Gmail, AppleId, Facebook, and via email pin code. Within games, transactions can be _invisibly_ signed, where the game app submits transactions on behalf of the player.

Issues with web3 gaming wallets are:

* Many game players don't want to login to play a game.
* Some game players don't want to use their Gmail address, because they see it as personal, and not to be shared with untrusted parties. In part the issue is that they don't want to risk their email address being on-sold and then receiving spam email.
* Some game players don't want to use their Gmail address, because they see it as security relevant. They use their email address to log into important financial entities, and don't wish to mix that usage with more frivolous usage such as playing a game. 
* Some game players don't know the password associated with their Gmail address. Logging in likely involves password resetting, which is something they try to avoid.
* Some game players find logging into Google extremely complicated or impossible. These people typically rely on friends and family to log them into systems. 

Possible solutions to these issues are:

* Login should be delayed as long as possible. 
* Once a player is logged in, they should never be logged out. 
* A possible solution is:
  * Players play the game without logging in.
  * When the player needs to submit a transaction or receive an asset, this happens via a game studio controlled wallet. 
  * Game players only sign in when they want to sell assets or buy assets. At this point, the assets in the game studio controlled wallet can be transferred to the game player's wallet. This delayed sign-in solves for players being able, but reluctant to enter credentials: by the time they are entering credentials they perceive they have something of value, and hence it is worth protecting, hence it makes sense to use credentials. However, this doesn't solve for game players who find login too complex.


# Game Economics

Game economics is complicated. Games that would have been successful outside the context of web3 fail due to their web3 aspects. Unpacking this:

* Pre-selling NFTs prior to game launch develops expectations on the utility of the NFTs. Game players may be dissatisfied with the game because the utility of an NFT they purchased (possibly at an inflated price on a secondary market) doesn't match their expectations.
* Mis-pricing NFTs and ERC 20s: If the market place of game players is prepared to pay a certain price, say $1, for an NFT in a game they know little about, but the base price for NFTs in the game is $10, then few of the NFTs will be sold. 
* Requiring NFTs to play the game will make the game impossible to play for game players who just want to try out the game. They will be blocked from enjoying the game, and possibly encouraging others who might invest in the game to play the game.
* Games often go through surges, peaking and then have a declining player base. The steady state could be ten times fewer game players than at the peak. There needs to be enough NFTs for all the players to play the game during the peak, but then for there not to be a glut of NFTs when the peak has passed. 
* As time goes on, there is a tendency to have attribute inflation, where the capabilities of new NFTs are better than previous NFTs, thus providing a reason to purchase or strive to obtain the new NFT. This may make early adoptors feel disenfranchised, as their investment in the early NFTs may feel like a poor investment. They may not want to invest in the new NFTs because they might be concerned that the new NFTs may also be superseded.
* Having more sources of ERC 20 tokens than sinks results in the token price continually having downward pressure. That is, it is easy to hand out game tokens. However, if there aren't enough compelling things for game players to do with the token, then they will dump the token, swapping it at whatever price they can get. If there are compelling reasons for owning the token, then new game players may want to buy the token, this creating a new sink for the token. 

Possible solutions to these issues:

* When offering pre-sale NFTs, you should have different rarities with different capabilities at different prices. Typical rarity categories are: Common, Uncommon, Rare, Epic, Legendary, and Mythical. 
* Have a limited number of NFTs initially. Even if the initial generation of NFTs sell out, do not create more of those NFTs. Doing so would dilute the value of the NFTs for your early adopters. Instead, quickly create a second generation of NFTs. 
* Consume NFTs as a part of crafting. That is, consume NFTs as a way to _power up_ or enhance the capabilities of an NFT. For example, three level one NFTs might be consumed to create a level two NFT.
* Once a game is established, new NFTs can be introduced that offer benefits on a different dimension to existing NFTs. Alternatively, they could be an alternative to a rarer, early NFT, but with some important differences to ensure they don't make the earlier NFT redundant.
* Possible sinks for ERC 20 tokens:
  * A component for crafting enhanced NFTs.
  * A consumable within a game. For example, travelling from planet A to B costs 100 game tokens. Players who don't have any of the game tokens can only play on planet A and can't travel between planets.
  * Donations. Game players could donate to a fund that the game studio matches token for token; with the funds going to content creators. However, the content creators will then wish to cash out the tokens to cover their costs. 
  * Staking. The idea is that game players acquire some tokens and then put the tokens in a non-custodial contract, and are then paid a reward for holding the tokens. Often for compliance reasons there needs to be an activity check, where the game player plays the game or trades NFTs. Doing staking takes tokens out of circulation, thus reducing the supply of tokens. However, staking does not consume tokens as such. The token rewards become a source of tokens.
  * Governance. In addition to or rather than giving rewards, a game studio might allow stakers to have input on governance decisions about the future of the game.


# Transaction Finality and Latency

Transactions submitted to game servers are finalised in game server databases within milli-seconds. Even allowing for globally distributed game players, a game action in a game app could be committed to a backend database and acknowledged back to the game within a few hundreds of milliseconds. Once the data has been committed to the backend database it will not change. It is _final_.

Transactions submitted to a blockchain are not immediately finalised. They are submitted to Remote Procedure Call (RPC) servers which gossip them to a block producing server. Initially, the transactions go into a transaction pool. The block producer takes transactions from the pool and puts them into blocks. The block producer chooses which transactions to include in blocks based on the price per unit gas that is being offered by the transaction submitter. If there are more transactions than can fit in a block, then the transaction may sit in the transaction pool waiting for the next block to be produced. 

Most blockchains produce blocks at certain intervals, block periods. For Ethereum the block period (also called the block time) is twelve seconds. For Immutable zkEVM it is two seconds. If a transaction arrives in the transaction pool just after a block has been produced, then it will have to wait for almost the entire block period before it could be included in a block. Once a block has been produced, it is gossiped to other nodes in the blockchain network. 

Different blockchains come to a consensus on the true (canonical) chain of blocks in different ways. These consensus protocols can lead to the possibility that a transaction is included in a block, but then that block is discarded in favour of an alternative block. This changing of the chain is called _reorganising_ or simply _reorg_. As such, users of the blockchain need to wait until their transaction has been included in a block which is deemed final based on the consensus rules of the blockchain. 

Some chains offer _instant_ finality. This means that once a block is produced, it can never be discarded or superseded. As soon as a user of the chain sees their transaction in a block, they know that it is final. For these chains there are no reorgs.

Issues to consider:

* Transactions on blockchains can take an order of magnitude more time to become final that tradition game transactions.
* Determine the characteristics of the chain:
  * Block period / time.
  * Consensus rules.
  * Finality.

Possible solutions:

* Design game actions that involve blockchain to not interrupt game play.
* Use a blockchain that has short block periods.
* Use a blockchain that provides fast finality or instant finality.


# Gas

Most blockchains use a certain amount of _gas_ to execute each instruction of a transactions execution. Historically, this has needed to be paid in the blockchain's native token. 

Issues to consider:

* Game players don't know what gas or the blockchain's native token is. They won't understand why they should pay using a currency they don't own for something they don't think they need. They just want to play a game. They don't care about your backend infrastructure.
* Some blockchains such as Immutable zkEVM offer gas free transactions assuming the transactions are signed by Immutable Passport.
* Some blockchains offer the ability for transactions to be sponsored. In this scenario, the game studio could pay for the players transactions. The issue with this is that most game related transactions are of low value. Subsidising these transactions could be a loss making venture. 


# Game Logic Matching

To prevent cheating, the logic on a game app that involves a server must be replicated on the server. If this is not done, then some game players might modify the game app to give themselves an unfair advantage. If part of the game logic involves consuming tokens under certain conditions, then that game logic may have to be implemented in a Solidity contract on the blockchain. 

Issues with this:

* Implementing secure Solidity contracts is very hard.

Possible solutions:

* Make contracts upgradeable.
* Ensure on-chain logic is as simple as possible. 
* Test everything. Use AI to audit the code. Have a blockchain expert audit the code. 
* Monitor the deployed code, watching for misuse and attacks.

# Asset Sync

If in-game assets are linked to NFTs, then the game needs to know which NFTs a player owns. For games that allow for loaning of NFTs, then the game needs to know which NFTs a player has access to. 

The timing of when to do _Asset Sync_ is important. If a game continually synchronises which NFTs are owned, then game play could be disrupted when a player suddenly owns or no longer owns a certain NFT. However, if the NFTs owned by a player are snapshotted for a game sequence, then game players might cheat, starting the game play with a certain asset, and then transferring the underlying NFT to a friend, who is then able to start the game play based on the same NFT. 


# DEX Liquidity Pool Design

For a game token to be tradable, there needs to be a liquidity pool set-up on a Decentralised Exchange (DEX). This allows game players to swap other tokens for the game token. Setting up a liquidity pool requires careful consideration to get right.

When a liquidity pool is created some amount of game token and some amount of other tokens need to be deposited into a DEX contract. The other token needs to be a token that has many other token pairs available on the DEX, thus allowing the game token to be swapped with a variety of tokens. The liquidity depth (the amount of liquidity at each price point) needs to be deep enough such that large price slippage doesn't occur during swaps.

When the liquidity pool is established, the initial exchange price needs to be set. Doing a pre-sale of the token to do some price discovery can help determine this exchange rate.

The liquidity pool can be initialised with any amount of each token. If only game tokens are used to initialise the liquidity pool, and none of the other token, then people will be able to swap other tokens for game tokens, but not visa-versa. 

Another factor which must be considered when establishing the liquidity pool is the liquidity depth. Having more tokens per price point will tend to lead to a more stable price. However, this then might limit the required dynamic pricing required to move the price to a point that game players are prepared to pay.

The final consideration when constructing a liquidity pool is the fee tier to use. A fee tier of 1% is typical for game tokens. The reflects the volatility of the game token; the risk the liquidity provider is taking on by holding the game token.


# Token Listing

For game players to see your ERC 20 game token in their wallet, the wallet provider will need to enable your token. Setting this up and ensuring your token remains available in the wallet will require  collaboration with the wallet provider.
