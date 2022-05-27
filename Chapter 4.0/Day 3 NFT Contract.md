1. Why did we add a Collection to this contract? List the two main reasons.
We need a container to hold multiple NFTs in one path since only one item can be saved at a path
A collection is needed in order to get NFTs gifted or minted to our account

2. What do you have to do if you have resources "nested" inside of another resource? ("Nested resources")
You need to have a destroy function to destroy nested resources.

3. Brainstorm some extra things we may want to add to this contract. Think about what might be problematic with this contract and how we could fix it.

Add some additional fields, like traits for the NFT like color, size, names.
Add some change functions for the fields. For example, if the NFT has levels, maybe have a function to increase values.
Main problem will be to determine who should have access to the change functions and being able to read the fields. Resources interfaces will be necessary to restrict access.

Idea #1: Do we really want everyone to be able to mint an NFT? 🤔. No, there should be a restriction and only the minter should be able to mint.

Idea #2: If we want to read information about our NFTs inside our Collection, right now we have to take it out of the Collection to do so. Is this good?
It's better to use a reference to the NFT rather moving the NFTs around.
