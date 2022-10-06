# Just DAOit: easy as x-y-z


![DAOit](https://daoit.xyz/images/daoit128-black.png)

Create a DAO in minutes:
Perfect a DAO in less than one year
https://github.com/DAONOW

- submit two forms / transactions
- ERC20 Voting token + streaming-enabled version (Superfluid)
- OpenZeppelin Governor + Timelock (treasury)
- DAO Manager enables grants, deposit + streaming contributions, issues/streams shares


## Contracts
By submitting two short forms, 5 contracts are deployed:

- *DAO Token*. Choose your own name and symbol for this ERC20 token. The DAO token leverages Open Zeppelin contracts and support the *ERC20Votes* extension, enabling vote delegation and the ability to assess voting power as of the block that a proposal was made.

- *Super DAO Token*. The _super_ token is the DAO Token upgraded (wrapped) using the Superfluid protocol, enabling it to be streamed in real-time. 

- *DAO Manager*. The DAO manager contract handles financial contributions to the DAO and distribution of DAO tokens to members. Using the `deposit()` function, contributions can be sent to the DAO. As part fo the deposit transaction, the DAO manager will mint and send DAO tokens to the member, equivalent to their "share" of the treasury. If the deposit is made with tokens other than the chosen "accepted" token, the DAO Manager will attempt to swap the tokens using Uniswap. Members can also contribute by sending streams of accepted tokens to the DAO Manager, which acts as a "Super App" in the Superfluid protocol. In this case, the DAO Manager starts a real-time stream of DAO Tokens back to the member, which continues as long as the deposit stream remains active. Whether deposited or streamed, all tokens are forwarded immediately to the treasury (Timelock/Executor) contract. The DAO Manager is not intended to HODL tokens, rather it ensures that tokens are sent or streamed to the correct recipients.  Finally, the `grant()` function can be used to grant DAO Tokens without requiring a deposit. Normally this would be executed via a governance proposal.

- *DAO Governor*. The DAO Governor contract is an *Open Zeppelin Governor* contract with the _TimelockControl_ extension, enabling the Timelock(treasury) to act as the executor of governance proposals with a time delay between a proposal passing and being executed. The Governor is the asset allocation contract when it interacts with the Executor.

- *DAO Executor*. This an *OpenZeppelin Timelock* contract that acts a treasury for the DAO. It executes DAO proposals and holds all funds/tokens odf the DAO. DAO members can direct these funds via goverance proposals.

### No Withdrawals
Note: by design, there is no permissionless means for members to *withdraw* funds from the DAO. It is not to be confused with a *vault* -- once funds have been contributed to the DAO, it is up to governance to decided how those funds are spent. Code is law.

### Vetoable
During governance creation, there is an option to grant *veto power* to the deployer. This enables the deployer to directly execute functions on behalf of the treasury and `grant()` DAO Tokens via the DAO Manager. This is intended to facilitate the early activities of the DAO before membership is well established, and it intended to be *temporary*. At the appropriate time, the Vetoer *should* renounce these roles (via Open Zeppelin's Access Control).

### Multi-chain DAOs
- DAOit creates DAO Token, DAO Manager, Governor, and Timelock contracts at the same addresses on multiple chains.
- Enables contributions from L2s / sidechains to same Manager and/or Timelock address

## Frontend for Deposits & Grants
The DAOit interface does not include frontend functions for interacting with the DAO contract after they have been deployed. Most DAOs will want to integrate such features into their own websites. Alternatively, the deployer can use Etherscan to interact with the contracts (ie. to grant DAO Tokens).

## Tally Goverance Interface
Tally (https://withtally.com) provides a user interface for creating and voting on governance proposals. After creating a DAO using DAOit, the deployer is presented with the details needed to "Add a new DAO" on Tally. Once the DAO has been added to Tally, members can create proposals, delegate votes, and vote on proposals.

## Pain Points
DAOs can be complicated to launch and may require thousands of dollars in development costs. DAOit makes it easy and fast ... and on a sidechain or L2, even deploying is inexpensive.

## Use Cases
- Non-profit DAOs raising funds directly from DAO members
- Investment clubs where members receive shares (DAO tokens) based on how much they invest
- NFT DAOs for pooling funds to collectively bid on one or more NFTs

## Demo Video
[https://youtu.be/EL46BEQQvhc](https://youtu.be/EL46BEQQvhc "DAOit Demo Video")


## History
Worked on DAOit started in early December 2021.

## Contact

Original design by
**Discord**: markcarey#5670

adopted for use in DeltaVerse DAO (c) <a href="https://deltav.exchange">DeltaV THRUST</a>

