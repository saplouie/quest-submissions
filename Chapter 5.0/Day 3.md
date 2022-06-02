1. What does "force casting" with as! do? Why is it useful in our Collection? It force changes the type of resource. It is useful because the NFT standard is too basic and we need to pass the specific NFT type into the collection.


What does auth do? When do we use it? Auth is used with a reference so that it can later be down cast. We used it during the borrow function so we can downcast &NFT

This last quest will be your most difficult yet. Take this contract:

and add a function called borrowAuthNFT just like we did in the section called "The Problem" above. Then, find a way to make it publically accessible to other people so they can read our NFT's metadata. Then, run a script to display the NFTs metadata for a certain id.

Added CollectionPublic interface in contract and implemented for resource Collection. 
Added borrowAuthNFT under Collection resource

...........

  pub resource interface CollectionPublic {
    pub fun deposit(token: @NonFungibleToken.NFT)
    pub fun getIDs(): [UInt64]
    pub fun borrowAuthNFT(id: UInt64): &NFT
    
  }
...........

  pub resource Collection: NonFungibleToken.Provider, NonFungibleToken.Receiver, NonFungibleToken.CollectionPublic, CollectionPublic {
    pub var ownedNFTs: @{UInt64: NonFungibleToken.NFT}

.............

    pub fun borrowAuthNFT(id: UInt64): &NFT {
      let ref = &self.ownedNFTs[id] as auth &NonFungibleToken.NFT
      return ref as! &NFT
    }
.............


You will have to write all the transactions to set up the accounts, mint the NFTs, and then the scripts to read the NFT's metadata. We have done most of this in the chapters up to this point, so you can look for help there :)
Created collection in 0x03
![image](https://user-images.githubusercontent.com/26511703/171559795-1cc56ea7-4492-4b3d-8e07-5c74dc551ea2.png)


Mint NFT transaction as 0x01, minting to 0x03
![image](https://user-images.githubusercontent.com/26511703/171559901-de4225cb-75ad-413f-9b01-39f1350010ac.png)

Read and return favorite food from 0x03, id 2"
![image](https://user-images.githubusercontent.com/26511703/171562732-7ca16072-e556-4c11-82c4-1c671fc9acbc.png)


