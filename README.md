# IPFS_Ethereum_Upload
You can upload any files on IPFS and Ethereum blockchain.

Origianl codes are from Dapp Academy, but current solidity, truffle etc version 

The version of Solidity used by Dapp Academy was 0.4.18. However, when you actually follow his code, you will get 0.5.0 Solidty and also different version of Truffle. 

This cause some minor errors. 

So you need to change Migrations.Sol 

Here is the code you need to type/change. 

-----------------------------------------------------------------------------------------------------------------------------
pragma solidity 0.5.0;    //Check your version of Solidity

contract Migrations {

    address public owner;
    uint public last_completed_migration;

    modifier restricted() {
        if (msg.sender == owner) _;
    }

    constructor() public {
        owner = msg.sender;
    }

    function setCompleted(uint completed) public restricted {
        last_completed_migration = completed;
    }

    function upgrade(address new_address) public restricted {
        Migrations upgraded = Migrations(new_address);
        upgraded.setCompleted(last_completed_migration);
    }
 }

-----------------------------------------------------------------------------------------------------------------------------To check your Solidty version and Truffle version,

Type below

truffle version (If you install truffle globally type truffle version in any directory)

then you will see below

Truffle v5.0.4 (core: 5.0.4)
Solidity v0.5.0 (solc-js)
Node v8.12.0

----------------------------------------------------------------------------------------------------------------------------
How to set up the Dapp

1. git clone the repositrory.
2. cd ipfs_image_uploader
3. ~/ipfs_image_uploader$ npm install
4. cd ..
5. npm install -g ganache-cli 
6. npm install -g truffle
7. cd ipfs_image_uploader
8. ~/ipfs_image_uploader$ npm install --save ipfs-api

----------------------------------------------------------------------------------------------------------------------------
When you download ipfs-api,

you will see the comment saying "ipfs-api has been renamed to ipfs-http-client, please update your package.json to get the latest version." then it will be downloaded. 
Just ignore it. You dont have to change anything. Let your computer do everything for you.

-----------------------------------------------------------------------------------------------------------------------------

How To Run.
1. go to your ganache directory and type "npm run start" then ganache will be started. 
2. Check ganache port. if port number is 8545, you need to change port of your dapp and metamask.
3. go to your ipfs_image_uploader directory. view truffle.js
4. change port number to 8545. If it is preset as 8545 and leave it.
5. go to your metamask and add custom rpc as http://127.0.0.1:8545
6. go back to your ipfs_image_uploader directory and type "truffle migrate --reset"
7. after that you can see very few amount of ethereum was gone in ganache application. 
8. In ipfs_image_uploader directory, type "npm run start" 
9. upload your images and click "submit". A few seconds later metamask will pop up and ask you whether you continue the transaction by paying a transaction fee. 
10. After you pay it, you will see image preview on the same page. 

-----------------------------------------------------------------------------------------------------------------------------

How To Check IPFS Hash

1. go to ipfs_image_uploader directory.
2. Type "truffle console"
3. you will be moved to truffle(development) 
4. Type "SimpleStorate.deployed().then(function(i) { app = i;})
5. you will see "undefined"
6. Type app.get().then(function(value) { ipfsHash = value});
7. You will see "undefined" again. ignore it
8. Type ipfsHash
9. You will see the hash. 
10. Congrats

-----------------------------------------------------------------------------------------------------------------------------
If you see Error: rpc error with payload {"id": ~~~~~~~~~~."jsonrpc": 2.0 ["~~~~~~~~~~~~~~~"]} 

It is nothing wrong with the code of the Dapp. It is a metamask problem. 

signout from metamask and retry. or change the port number and retry. 

it will work fine. 


Thank you.










