1. In words, list 3 reasons why structs are different from resources.
- Structs can be copied
- Structs can be created anywhere, not just inside contracts
- Structs can be overwritten

2. Describe a situation where a resource might be better to use than a struct.
- A resource would be useful in the case of the instance of an NFT. We don't want them copiable nor easily lost.

3. What is the keyword to make a new resource?
- create is the keyword for creating a new resource

4. Can a resource be created in a script or transaction (assuming there isn't a public function to create one)?
- resources can only be created within a contract, as "create" can only be used within a contract.

5. What is the type of the resource below?
- @Jacob
 
pub resource Jacob {

}

6. Let's play the "I Spy" game from when we were kids. I Spy 4 things wrong with this code. Please fix them.
pub contract Test {

    // Hint: There's nothing wrong here ;)
    pub resource Jacob {
        pub let rocks: Bool
        init() {
            self.rocks = true
        }
    }

    pub fun createJacob(): @Jacob 
        let myJacob <- create Jacob() 
        return <- myJacob 
    }
}
