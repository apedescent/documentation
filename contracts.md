---
description: All our contract are verified on BSCScan so feel free to dive in.
---

# Smart Contracts

There was no formal audit yet. We've been online since May 2021 with no exploit.

Here's a quick reference and below is a more detailed structure with brief explanations.

Token|Address
---|---
NTRO token | [0x8fc50089De41A0f3436D616077c94907D0162BE6](https://www.bscscan.com/0x8fc50089De41A0f3436D616077c94907D0162BE6)
ROKT token | [0xc0731c3A2cbd795c6AB6dd7Fe2146Edc51CC21B0](https://www.bscscan.com/0xc0731c3A2cbd795c6AB6dd7Fe2146Edc51CC21B0)
DEGEN token | [0x7c57435C0d7B664600F59784075518Ff80C1E4c8](https://www.bscscan.com/0x7c57435C0d7B664600F59784075518Ff80C1E4c8)
Reactor | [0x0F7072748cd0762df37d89B9C191BD33512e3f49](https://www.bscscan.com/0x0F7072748cd0762df37d89B9C191BD33512e3f49)
BNB masterchef | [0xCA74b3db871c679e928E70917Ae804DC7BFd8781](https://www.bscscan.com/0xCA74b3db871c679e928E70917Ae804DC7BFd8781)
ROKT masterchef | [0x062D9b9a97B4eFC67D286e99618dA87C614B166F](https://www.bscscan.com/0x062D9b9a97B4eFC67D286e99618dA87C614B166F)
Governor | [0x3440B18cd8103e39EE547F5a477DdEeC44710a52](https://www.bscscan.com/0x3440B18cd8103e39EE547F5a477DdEeC44710a52)
Governor Timelock | [0xDAd5C824B8f1f7249C17132C80B091b4752169F1](https://www.bscscan.com/0xDAd5C824B8f1f7249C17132C80B091b4752169F1)
Guardian | [0x946238Ee8774B8b38732C76345d40EA1CB7ad3dC](https://www.bscscan.com/0x946238Ee8774B8b38732C76345d40EA1CB7ad3dC)
TreasuryStrategy | [0x52E6C3B710e64Ab083B9109A44240c16b277D737](https://www.bscscan.com/0x52E6C3B710e64Ab083B9109A44240c16b277D737)
BUSD/ETH/BTC Stragegy | [0xc616Da5876FfD9cb8935a89F7515bE0104Fe86e8](https://www.bscscan.com/0xc616Da5876FfD9cb8935a89F7515bE0104Fe86e8)
Ntro Autocompound Pool | [0x42C30c2548b28Abacd23e178aB1e4DbaA4e3469b](https://www.bscscan.com/0x42C30c2548b28Abacd23e178aB1e4DbaA4e3469b)
Rokt Autocompound Pool | [0xd372b6F77fEf2E93da37C4C3A72a68fAAA286444](https://www.bscscan.com/0xd372b6F77fEf2E93da37C4C3A72a68fAAA286444)
Treasury | [0x22cD35fb46E03Bd443746B67E19a2Af91C2d975A](https://www.bscscan.com/0x22cD35fb46E03Bd443746B67E19a2Af91C2d975A)


## Tokens

### NTRO

BSC Address: [`0x8fc50089De41A0f3436D616077c94907D0162BE6`](https://www.bscscan.com/0x8fc50089De41A0f3436D616077c94907D0162BE6)

Our main index token (ERC20/BEP20), backed by BNB and Cake. It's minted by the reactor contract against BNB deposit.

NTRO can be staked in both BNB Masterchef and ROKT Masterchef to earn BNB and ROKT respectively.

[Read more about NTRO token](nitro.md)

### ROKT

BSC Address: [`0xc0731c3A2cbd795c6AB6dd7Fe2146Edc51CC21B0`](https://www.bscscan.com/0xc0731c3A2cbd795c6AB6dd7Fe2146Edc51CC21B0)

ROKT is our governance token. It's  inflationary by nature: every block (on BSC that's every 3 seconds) 0.1 ROKT is minted. That makes 120 per hour, 2,880 per day and 1,051,200 per year.

All minted ROKT is distributed by the ROKT Masterchef contract to stakers in active pools.

[Read more about ROKT token](rocket)

### DEGEN

BSC Address: [`0x7c57435C0d7B664600F59784075518Ff80C1E4c8`](https://www.bscscan.com/0x7c57435C0d7B664600F59784075518Ff80C1E4c8)

The team token. Every member of the founding team got an equal share of these and they can be staked in the ROKT Masterchef.

### PAMP (discontinued)

BSC Address: [`0xF811f05eEF1f7207356E2a313757eCE15dB92168`](https://www.bscscan.com/0xF811f05eEF1f7207356E2a313757eCE15dB92168)

The influencer token. We gave these to influencers before launching the project so that they can stake them in ROKT Masterchef and receive ROKT rewards. It didn't work out very well so we disabled the pool.

### CHAD (discountinued)

BSC Address: [`0xFb7b96B0C0AD9Cc956f9d22453609F1314f9AeC5`](https://www.bscscan.com/0xFb7b96B0C0AD9Cc956f9d22453609F1314f9AeC5)

Token with a maximum supply which used to be minted and given to the user for every NTRO bought. It could be staked in the ROKT Masterchef to farm ROKT.

We discountinued it in favor of staking NTRO directly. It's effectively the same with the firstcomer advantage removed.

## Reactor

BSC Address: [`0x0F7072748cd0762df37d89B9C191BD33512e3f49`](https://www.bscscan.com/0x0F7072748cd0762df37d89B9C191BD33512e3f49)

Reactor is where the magic around NTRO token happens.

It mints and burns NTRO along the bonding curve serving as an automated market maker. Internally it hooks into PancakeSwap and converts the BNB to BNB/Cake LP tokens and stakes those on Pancake.  

The "curve" is actually a linear function in a form of `y = 0.000001 * x` meaning that every the price of every newly minted NTRO token is 0.000001 BNB more. 

[Learn more about how NTRO works](nitro.md)

## Masterchefs

Masterchefs are pool managers. Based on the SushiSwap contracts that everyone else uses and totally battle tested.

Masterchef distributes tokens to pools. Each masterchef can have any number of pools and each pool has a specific multiplier implying the portion of all the rewards that particular pool gets. The pool rewards are then distributed proportionally to all stakers.

We have two masterchef contracts: BNB Masterchef and ROKT Masterchef. The basic function is the same but there are differences. See below.

### BNB Masterchef

BSC Address: [`0xCA74b3db871c679e928E70917Ae804DC7BFd8781`](https://www.bscscan.com/0xCA74b3db871c679e928E70917Ae804DC7BFd8781)

Distributes BNB rewards to ROKT and NTRO stakers 50/50.

The BNB tokens being distributed come from NTRO swap tax (10% of every NTRO buy or sell) and from PancakeSwap staking rewards from the NTRO underalying asset (BNB/Cake LP). Read more about how NTRO works in [apescape/ntro]

### ROKT Masterchef

BSC Address: [`0x062D9b9a97B4eFC67D286e99618dA87C614B166F`](https://www.bscscan.com/0x062D9b9a97B4eFC67D286e99618dA87C614B166F)

Distributes ROKT rewards. There are currently three pools but that might change in the future through governance:
- BNB/ROKT LP pool (highest yield): 50x multiplier
- NTRO pool: 5x multiplier
- DEGEN pool (team tokens): 15x multiplier. Read more about [team allocations](team.md) and what it means for the project.

## Governance

The governance module is a fork of the original Compound Finance system ([Governor Alpha](https://github.com/compound-finance/compound-protocol/blob/master/contracts/Governance/GovernorAlpha.sol)). Nothing special there. 

[Read more about governance](governance.md).

### BSC Addresses:

- Governor: [`0x3440B18cd8103e39EE547F5a477DdEeC44710a52`](https://www.bscscan.com/0x3440B18cd8103e39EE547F5a477DdEeC44710a52)
- Governor Timelock: [`0xDAd5C824B8f1f7249C17132C80B091b4752169F1`](https://www.bscscan.com/0xDAd5C824B8f1f7249C17132C80B091b4752169F1)
- Guardian: [`0x946238Ee8774B8b38732C76345d40EA1CB7ad3dC`](https://www.bscscan.com/0x946238Ee8774B8b38732C76345d40EA1CB7ad3dC)

## Autocompounding pools

Compound interest is a powerfull thing. It can turn your gains from linear to exponential. Also it saves your time and fees. [More info on autocompounding](intro-to-defi/autocompounding).

Currently we have an autocompound option on two of our pools: the NTRO pool (BNB masterchef) and the BNB/ROKT (ROKT masterchef). Both work very similarly, the main difference being the underlying asset and thus the exact autocompound procedure.

Our compouding method is actually semi-automatic. The process still needs to be triggered by a user but it's way simpler than manual compounding because
- one compound action compounds for all users currently in the pool
- only one transaction and no math is necessary

As a trade-off, there's a small service fee that goes to the treasury.

### Autocompound strategies

#### TreasuryStrategy

BSC Address: [`0x52E6C3B710e64Ab083B9109A44240c16b277D737`](https://www.bscscan.com/0x52E6C3B710e64Ab083B9109A44240c16b277D737)

Strategies wrapper. Custom strategies can be plugged in.

#### StrategyBusdEthBtc

BSC Address: [`0xc616Da5876FfD9cb8935a89F7515bE0104Fe86e8`](https://www.bscscan.com/0xc616Da5876FfD9cb8935a89F7515bE0104Fe86e8)

Splits BNB amount in four parts and buys ETH, BTC and BUSD (as wrapped BSC tokens)

### NTRO Autocompound

BSC Address: [`0x42C30c2548b28Abacd23e178aB1e4DbaA4e3469b`](https://www.bscscan.com/0x42C30c2548b28Abacd23e178aB1e4DbaA4e3469b)
Strategy: StrategyBusdEthBtc
Fee: 0 %

### ROKT Autocompound

BSC Address: [`0xd372b6F77fEf2E93da37C4C3A72a68fAAA286444`](https://www.bscscan.com/0xd372b6F77fEf2E93da37C4C3A72a68fAAA286444)
Strategy: StrategyBusdEthBtc
Fee: 1 %

## Treasury

BSC Address: [`0x22cD35fb46E03Bd443746B67E19a2Af91C2d975A`](https://www.bscscan.com/0x22cD35fb46E03Bd443746B67E19a2Af91C2d975A)

The funds owned by the protocol and accessible through governance. As the protocol grows, we'd like the treasury to own a significant part of ROKT liquidity and variety of other assets.
