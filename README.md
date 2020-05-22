# Pythonblockchain

### Essentially what the wallet does is it uses pnemonics to create hashes for test networks in a blockchain. it connects to blockchaines depending on the coin you are using. it is built with PHP and the way you use it is by calling the "send_tx" function and passin the coin, sender, recipient and ammount that you would like to send within the function.

```{r}
def send_tx(coin,account, recipient, amount):
    tx = create_tx(coin,account,recipient,amount)
    
    if coin == ETH:
        signed_tx = eth_account.sign_transaction(tx)
        result = w3.eth.sendRawTransaction(signed_tx.rawTransaction)
        return result.hex()
    elif coin == BTCTEST:
        signed_tx = btctest_account.sign_transaction(tx)
        return NetworkAPI.broadcast_tx_testnet(signed_tx)
```

![bitcointest](bitcointesttransaction.png)
## This is the code that i used to send the transaction imaged above. 
```{r}
send_tx(BTCTEST, btctest_account,"mhzQ7M4s4a5b6Cu3pYQ9B4g1HW251KqcUD",.001)
```

![ethtest](ethtransaction.png)
## This is the code that i used to send the Ehtereum transaction above

```{r}
send_tx(ETH, eth_account, "0x23fcD28B554B390F13b7A0CEaE222e7d0f80Ebb9", 25)
```



