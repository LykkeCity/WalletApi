#Wallet API

##Email broadcasting

Service is queue based (queue name: "emailsqueue"). Currently we handle next queue messages:

 - Create plain text broadcast request

  ```PlainTextBroadcast:{"Data":{"BroadcastGroup":100,"MessageData":{"Subject":"Some subject","Text":"Some text"}}}```

  - Broadcast groups ("BroadcastGroup" parameter):

    ```Kyc = 100```
    
       ```ClientSupport = 200```
       
       ```Errors = 300```

#Lykke Jobs

##Handled transactions HTTP Listener

 - Request to notify us about already handled transaction:

  ```/POST http://+:8088/HandledTx/```
  - Swap:
  ```{ "Id" : "transactionId", "Hash" : "blockchainHash", "Operation" : "Swap" }```

  - CashIn:
  ```{ "Id" : "transactionId", "Hash" : "blockchainHash", "Operation" : "CashIn" }```

  - CashOut:
  ```{ "Id" : "transactionId", "Hash" : "blockchainHash", "Operation" : "CashOut" }```

  - Transfer:
  ```{ "Id" : "transactionId", "Hash" : "blockchainHash", "Operation" : "Transfer" }```

 - Response:

  ```200 OK: { "Error":null }```

  ```500: { "Error" : {Code:1, Message="Invalid input."} }```
