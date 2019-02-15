# IPFS_Ethereum_Upload
You can upload any files on IPFS and Ethereum blockchain.

Origianl codes are from Dapp Academy, but current solidity, truffle etc version 

The version of Solidity used by Dapp Academy was 0.4.18. However, when you actually follow his code, you will get 0.5.0 Solidty and also different version of Truffle. 

This cause some minor errors. 

So you need to change Migrations.Sol 

Here is the code you need to type/change. 

-----------------------------------------------------------------------------------------------------------------------------
pragma solidity 0.5.0;

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

truffle version

then you will see below

Truffle v5.0.4 (core: 5.0.4)
Solidity v0.5.0 (solc-js)
Node v8.12.0
-----------------------------------------------------------------------------------------------------------------------------
When you download ipfs-api,

you will see "ipfs-api has changed to ipfs-http-client" then it will be downloaded. 
Just ignore it. You dont have to change anything. Let your computer do everything for you.








