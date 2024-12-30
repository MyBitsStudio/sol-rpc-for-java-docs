### Actions

> Actions are ease-to-use classes that simplifies otherwise complex procedures. The goal of this library is to extend what is missing, but also make it easier for developers to create unique utilities and large scale systems.
> All actions can be found in the io.sol.account.action.impl

## TransferSOL (V 0.1.2 +)

> As the class name states, this action is used to easily transfer SOL from one wallet to the other, in simple few lines of code.
> This returns a signature when sent to the blockchain.
> 
> Example usage of TransferSol.class
> 
> ```java
> import io.sol.account.action.impl.TransferSol;
> 
> Connection connection = Connection.createConnection(RPCUrls.TESTNET, Commitment.CONFIRMED);
> Wallet sender = new Wallet(Keypair.generate());
> Wallet receiver = new Wallet(Keypair.generate());
> 
> String signature = new TransferSol(sender.getPair(), receiver.getPair().getPublicKey(), 0.05, connection).send64Legacy();
>```
> 
> There are 4 sending functions, each correlating to transaction sending from Connection :
> > send64Legacy() - uses function sendTransaction64()
> >
> > send58Legacy() - uses function sendTransaction58()
> >
> > send64Raw() - uses function sendRawTransaction54()
> >
> > send58Raw() - uses function sendRawTransaction58()
> 
> The class accepts both long input for amount (lamports) and decimal value.

## TransferSPL (V 0.1.2 +)

> This class makes it easy to transfer custom tokens to any address. It is similar to TransferSOL, except it intakes a minted token to transfer.
> Make sure there is enough SOL to cover gas fees with this.
> 
> Example usage of TransferSPL
> 
> ```java
> import io.sol.account.action.impl.TransferSPL;
> 
> Connection connection = Connection.createConnection(RPCUrls.TESTNET, Commitment.CONFIRMED);
> Wallet sender = new Wallet(Keypair.generate());
> Wallet receiver = new Wallet(Keypair.generate());
> 
> String signature = new TransferSPL(sender.getPair(), receiver.getPair().getPublicKey(), "DpDuHScSNi6LQZ9hjrwS2fjfgfeoAH1jRgcXt38rDrEw",
> 100000, Commitment.CONFIRMED, connection).send64Legacy();
>```
> 
> As with TransferSol, this has the 4 sending functions correlating to the function used to send the transaction.
> > send64Legacy() - uses function sendTransaction64()
> >
> > send58Legacy() - uses function sendTransaction58()
> >
> > send64Raw() - uses function sendRawTransaction54()
> >
> > send58Raw() - uses function sendRawTransaction58()
>
> The class accepts both long input for amount (lamports) and decimal value.

## WriteMemo (V 0.1.3 +)

> This class is an ease-of-use to add memo to any transaction, or send a specific memo transaction by itself.
> Memo's are messages stored in teh blockchain, usually used for verification
> 
> Example usage of WriteMemo (Instructions)
> 
> ```java
> import io.sol.account.action.impl.WriteMemo;
> 
> Connection connection = Connection.createConnection(RPCUrls.TESTNET, Commitment.CONFIRMED);
> Wallet sender = new Wallet(Keypair.generate());
> 
> Instruction instruction = new WriteMemo("This is a test message!", sender.getPair(), connection).writeMemoInstruction();
> String blockhash = connection.getLatestBlockHash();
> TransactionMessage message = TransactionMessage.newMessage(sender.getPair().getPublicKey(), blockhash, instruction);
> VersionedTransaction transaction = new VersionedTransaction(message);
> transaction.sign(signer.getPair());
> String signature = connection.sendRawTransaction64(transaction);
> ```
> 
> > Example usage of WriteMemo (Instructions)
> ```java
> import io.sol.account.action.impl.WriteMemo;
> 
> Connection connection = Connection.createConnection(RPCUrls.TESTNET, Commitment.CONFIRMED);
> Wallet sender = new Wallet(Keypair.generate());
> 
> VersionTransaction transaction = new WriteMemo("This is a test message!", sender.getPair(), connection).writeMemoTransaction();
> transaction.sign(sender.getPair());
> String signature = connection.sendRawTransaction64(transaction);
> ```