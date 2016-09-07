#Wallet API

##Email broadcasting

Service is queue based (queue name: "emailsqueue"). Currently we handle next queue messages:

 - Create plain text broadcast request

  ```PlainTextBroadcast:{"Data":{"BroadcastGroup":100,"MessageData":{"Subject":"Some subject","Text":"Some text"}}}```

  - Broadcast groups ("BroadcastGroup" parameter):

    ```Kyc = 100```
    
       ```ClientSupport = 200```
       
       ```Errors = 300```
       
       ```Warnings = 400```

 - Create plain text email request

  ```PlainTextEmail:{"Data":{"EmailAddress":"billg@microsoft.com","MessageData":{"Sender":"bob@noname.com","Subject":"Hi, Bill!","Text":"Some text"}}}```


#Lykke Jobs

##Handled transactions HTTP Listener

 - Request to notify us about already handled transaction:

  ```/POST http://+:8088/HandledTx/```
  - Swap:
  ```{ "TransactionId" : "transactionId", "BlockchainHash" : "blockchainHash", "Operation" : "Swap" }```

  - CashIn:
  ```{ "TransactionId" : "transactionId", "BlockchainHash" : "blockchainHash", "Operation" : "CashIn" }```

  - CashOut:
  ```{ "TransactionId" : "transactionId", "BlockchainHash" : "blockchainHash", "Operation" : "CashOut" }```

  - Transfer:
  ```{ "TransactionId" : "transactionId", "BlockchainHash" : "blockchainHash", "Operation" : "Transfer" }```

 - Response:

  ```{ "Error":null }```

  ```{ "Error" : {Code:1, Message="Invalid input."} }```

#MyLykke

###To check should client app show "MyLykke" tab or no use GET api/MyLykkeSettings with authorization.

 - Response:
```sh
{
  "Result": {
    "MyLykkeEnabled": true
  },
  "Error": null
}
```

 - Under hood:
 
MyLykkeEnabled = **[client setting "MyLykke enabled"]** != null ? **[client setting "MyLykke enabled"]** : **[global setting "MyLykke enabled"]**
  
**[client setting "MyLykke enabled"]** stored in IClientSettingsRepository (MyLykkeSettings -> bool? MyLykkeEnabled)
  
**[global setting "MyLykke enabled"]** stored in IAppGlobalSettingsRepositry (IAppGlobalSettings -> bool ShowMyLykke)
