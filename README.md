### 18.3-Proof_of_Authority
Homework for section 18.3

This assignment walks through the steps needed to create a tesnet blockchain for a fictitous organization

# Setup Steps
1. Two nodes were create, Node 1 and Node 2 resulting in the following details. 
Node 1:

Public address of the key:   0x62042bAb7aA633D0E33B632cD75Bf5945a6Ad1b5  (Sealer 1)
Path of the secret key file: node1\keystore\UTC--2021-06-26T19-41-11.386459100Z--62042bab7aa633d0e33b632cd75bf5945a6ad1b5

Node 2:

Public address of the key:   0x9b5b12CC5CDA5C3677150d075Dc02fa9d677708C
Path of the secret key file: node2\keystore\UTC--2021-06-26T19-42-33.073175100Z--9b5b12cc5cda5c3677150d075dc02fa9d677708c

2. The test network was names "abbynet" and the chain ID was set to 610
3. Since this was a test network, the passwords were set to a simplistic one "password"

## Launch Nodes and Mine
Running from separate GIT bash terminals (with admin rights) the following commands were used:

# Command 1
"geth --datadir node1 --unlock "0x62042bAb7aA633D0E33B632cD75Bf5945a6Ad1b5" --mine --rpc --allow-insecure-unlock"

This unlocks the node1 and tells the node to start listening on the default port (8545).  A prompt will open and this is where the password "password" should be entered.  
Once this is done, there will be section referencing "enode://....." , copy this sections all the way to "@127.0.0.1:30303"  This will be needed for the second node command 
that is to be run from another terminal window.

# Command 2
"geth --datadir node2 --unlock "0x9b5b12CC5CDA5C3677150d075Dc02fa9d677708C" --mine --port 30304 --bootnodes "enode://fd427efc03e0f5c7264f226ce835b23914d6274dd2848343db06aac783b28e13fa9dd9da3da04e67484a3081805ae62e72e742368446ebfda37ba5ab6c3b5c13@127.0.0.1:30303" --ipcdisable --allow-insecure-unlock"    - This should be run without the first and last "

Note the "unlock" section references the key of the second node: 0x9b5b12CC5CDA5C3677150d075Dc02fa9d677708C

At this point, both nodes should be up and mining. 

# Verify in MyCrypto GUI

1. Launch the MyCrypto app.
2. Once open, click on "Change Network" in the botton left of the screen.
3. We will use "Custom" in the list of options.
4. This will open a form and we will enter the following:  
      Node Name: Anything you like
      Network: Custom
      Network Name: abbynet
      Currency: ETH
      Chain ID: 610
      URL: http://127.0.0.1:8545   (This is the local loopback address and the default RPC port)
 5. We now hit "Save & Use Custom Node"
 6. If we are successful, our MyCrypto will not have access to the Mnemonic Phrase and the only two options (Under View and Send) will be "Keystore File" and "Private Key"
 7. We will chose "KeyStore File"
 8. This will open another screen and we will browse to the Node1 directory and we will select the "keystore" file.
 9. The password "passowrd" wil unlock
 10.The account is now open in MyCrypto
 11.We will now send tokens to the address in Node2: 0x9b5b12CC5CDA5C3677150d075Dc02fa9d677708C
 12. Send the transaction at this point.
 13. <img width="998" alt="TXstatus" src="https://user-images.githubusercontent.com/60984494/123525269-5f2e2000-d69d-11eb-87ec-4accec791567.PNG">


