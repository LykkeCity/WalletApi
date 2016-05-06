#Wallet API

##Email broadcasting

Service is queue based (queue name: "emailsqueue"). Currently we handle next queue messages:

 - Create simple plaintext broadcast request

  ```PlainTextBroadcast:{"Data":{"BroadcastGroup":100,"MessageData":{"Subject":"Some subject","Text":"Some text"}}}```

  - Broadcast groups ("BroadcastGroup" parameter):

    ```Kyc = 100```
    
       ```ClientSupport = 200```
       
       ```Errors = 300```
