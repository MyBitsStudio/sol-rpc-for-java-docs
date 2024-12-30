## Tools

> Tools are made to help with complex functions, like checking if a transaction went through successfully. 
> 
> These tools are being improved constantly to excel at their functions.

# BalanceChecker (V 0.1.1 +)

> Balance Checker is a tool to be able to check balances, both SOL and SPL tokens.
> 
> There is a count check, which will run checks until it reaches this cap.
> 
> There is a delay of 500 ms per check, to reduce costs and credit usages on nodes.
> 
> An example of using BalanceChecker for SOL :
> 
> ```java
> Connection connection = Connection.createConnection(RPCUrls.TESTNET, Commitment.CONFIRMED);
> Wallet sender = new Wallet(Keypair.generate());
> 
> long balance = new BalanceChecker(connection, sender.getPair().getPublicKey().toBase58(), false, "", 10);
> ```
> 
> An example of using BalanceChecker for SPL Token :
> 
> ```java
> Connection connection = Connection.createConnection(RPCUrls.TESTNET, Commitment.CONFIRMED);
> Wallet sender = new Wallet(Keypair.generate());
> 
> long balance = new BalanceChecker(connection, sender.getPair().getPublicKey().toBase58(), true, "DpDuHScSNi6LQZ9hjrwS2fjfgfeoAH1jRgcXt38rDrEw", 10);
> ```

# Transaction Checker (V 0.1.1 +)

> Transaction Checker is a tool to poll the status of a transaction that has been sent in
> 
> It brings in to check and returns if it is confirmed or finalized.
> 
> This also checks for the block height to make sure your not capping over, and has a count check like Balance Checker
> 
> An example of using the Transaction Checker
> 
> ```java
>  Connection connection = Connection.createConnection(RPCUrls.TESTNET, Commitment.CONFIRMED);
> 
> String status = new TransactionChecker(connection, "TRANSACTION_HASH", 10);
> ```

# Transaction Log (V 0.1.3 +)

> Transaction checker is just a simple tool to check on information about the transaction.
> 
> This uses the getTransaction() RPC function. No additional information or functions provided.
> 
> An example of using Transaction Log:
> 
> ```java
> Connection connection = Connection.createConnection(RPCUrls.TESTNET, Commitment.CONFIRMED);
>   
> JsonObject data = new TransactionLog("TRANSACTION_HASH", connection);
> ```

# Transaction ReSender (V 0.1.2 +)

> **Transaction ReSender** is a tool used to help verify and ensure a transaction goes through.
> 
> This tool inputs an **Instruction** and than uses that instruction to retry to send a transaction upon failure.
> 
> There are two inputs, count **checks** for iterations, and **intensity** which helps with time management.
> 
> > Intensity Formula : (currentTimeMillis + ((1000 * 5) * (intensity % 2 = 0 ? intensity * 3L : intensity * 2L)))
> 
> An example of using Transaction ReSender :
> 
> ```java
> Connection connection = Connection.createConnection(RPCUrls.TESTNET, Commitment.CONFIRMED);
> Wallet sender = new Wallet(Keypair.generate());
> Wallet receiver = new Wallet(Keypair.generate());
> 
> TransferInstruction instruction = new TransferInstruction(sender.getPair().getPublicKey(), receiver.getPair().getPublicKey(), 100000);
> 
> String signature = new TransactionResender(connection, instruction, sender.getPair(), 10, 10);
> ```