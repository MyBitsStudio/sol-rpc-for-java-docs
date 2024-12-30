## Connection

> **The functions are still in Alpha stage. You may experience some errors or conflicts with existing systems. This is not recommended for production builds at this stage**

> This creates a new Connection class that enables the usage of multiple RPC methods. The connection class is an ease-of-use class, handling all RPC methods with extensive error reporting.

# Using Connections

> An example of how to use the connection class. 
> 
>**Make Sure To Use io.sol.connection and not sol4k connection class.**
>```java
>import io.sol.connection.Connection;
>
>Connection connection = Connection.createConnection(RPCUrls.TESTNET, Commitment.CONFIRMED);
>
>String blockhash = connection.getLatestBlockHash();
>```

# Connection RPC Methods

> **Currently running and tested to work**
> 
> (Those marked with a ** are custom methods)
> >getBalance (long) - Retrieves Lamports balance of PublicKey
> >
> >latestBlockHash (string) - Retrieves lastes blockchash
> >
> >extendedBlockhash (JsonObject) - Extended information of blockhash
> >
> >getBlockHeight (long) - Gets the current height of the block
> >
> >getBlockHeightFinal** (long) - Gets the current height of the block under Finalized commitment
> >
> >firstAvailableBlock (long) - Gets the first available block slot
> >
> >health (string) - Displays the health of the RPC
> >
> >getSignatureStatuses (JsonArray) - An array of confirmation statuses of signatures
> >
> >getSignatureStatus** (JsonArray) - Returns confirmation status of one signature
> >
> >slot (long) - The most current slot
> >
> >getTokenAccountsByOwner (JsonArray) - Displays balances of tokens of specified account
> >
> >getTokenAmountByOwner** (long) - Displays balance of minted token by account
> >
> >getAllTokenBalances** (Map<String, Long) - Displays all balances of tokens by account
> >
> >getTokenAccountsByOwnerAndMint (JsonArray) - returns accounts of owner that are associated with the mint
> >
> >getTokenSupply (JsonObject) - Information about the mint including tokenSupply
> >
> >getTokenDecimals** (int) - Gives the decimal amount for specified mint
> >
> >isBlockhashValid (boolean) - Returns if the blockhash is still valid
> >
> >sendTransaction (string) - Transaction signature of sent transaction
> >
> >sendTransaction64** (string) - Transaction signature of sent transaction on Base 64
> >
> >sendTransaction58** (string) - Transaction signature of sent transaction on Base 58
> >
> >sendRawTransaction64** (string) - Transaction signature of sent transaction bypassing preflight on Base 64
> >
> >sendRawTransaction58** (string) - Transaction signature of sent transaction bypassing preflight on Base 58
> >
> >simulateTransaction (JsonObject) - Simulates transaction and returns information about simulation
> >
> >getTransaction (JsonObject ) - Retrieves information about the transaction

> **Current Running, Untested **
> >getFeeForMessage (long) - Gets lamports fee for TransactionMessage
> >
>>getMinimumBalanceforRent (long) - Gets minimum lamports needed for rent
> >
>>getMultipleAccounts (JsonArray) - Displays information for collection of accounts
>>
>>getSignaturesForAddress (JsonArray) - A list of signatures associated with the address
>>
>>getTokenAccountsByOwnerAndProgram (JsonArray) - A list of accounts by owner and specified program
>>
>>getTokenLargestAccounts (JsonArray) - A list of the highest holders of the mint
>>
>>requestAirdrop (string) - Transaction signature of Airdrop

> ** Coming in future updates **
> > getAccountInfo
> >
>>getBlock
> >
>>getBlockCommitment
> >
>>getBlockProduction
> >
>>getBlockTime
> >
>>getBlocks
> >
>>getBlocksWithLimit
> >
>>getClusterNodes
> >
>>getEpochInfo
> >
>>getEpochSchedule
> >
>>getGenesisHash
> >
>>getHighestSnapshotSlot
> >
>>getIdentity
> >
>>getInflationGovernor
> >
>>getInflationRate
> >
>>getInflationReward
> >
>>getLargestAccounts
> >
>>getLeaderSchedule
> >
>>getMaxRetransmitSlot
> >
>>getMaxShredInsertSlots
> >
>>getProgramAccounts
> >
>>getRecentPerformanceSamples
> >
>>getRecentPrioritizationFees
> >
>>getSlotLeader
> >
>>getSlotLeaders
> >
>>getStakeMinimumDelegation
> >
>>getSupply
> >
>>getTokenAccountBalance
> >
>>getTokenAccountsByDelegate
> >
>>getTransactionCount
> >
>>getVersion
> >
>>getVoteAccounts
> >
>>minimumLedgerSlot



