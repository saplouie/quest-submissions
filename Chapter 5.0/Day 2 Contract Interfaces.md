1. Explain why standards can be beneficial to the Flow ecosystem. Standards are beneficial so that contracts can be interacted with and constructed with a common set of functions.
By importing standards, we can be assured the contract behave in a certain way such aa the NonFungibleToken Standard.

What is YOUR favourite food? Char Siu, Chinese BBQ Pork

Please fix this code (Hint: There are two things wrong):

The contract interface:

pub contract interface ITest {
  pub var number: Int
  
  pub fun updateNumber(newNumber: Int) {
    pre {
      newNumber >= 0: "We don't like negative numbers for some reason. We're mean."
    }
    post {
      self.number == newNumber: "Didn't update the number to be the new number."
    }
  }

  pub resource interface IStuff {
    pub var favouriteActivity: String
  }

  pub resource Stuff {
    pub var favouriteActivity: String
  }
}
The implementing contract:
-It doesn't import or implement the contract interface.
-The new number is being set to 5 instead of newNumber?
-Need to implement Resource Interface from Contract Interface instead of local interface.

Import ITest from 0x01
pub contract Test: Itest {
  pub var number: Int
  
  pub fun updateNumber(newNumber: Int) {
    self.number = newNumber
  }

// Remove local IStuff Interface 
//  pub resource interface IStuff {
//    pub var favouriteActivity: String
//  }

  pub resource Stuff: ITest.IStuff {
    pub var favouriteActivity: String

    init() {
      self.favouriteActivity = "Playing League of Legends."
    }
  }

  init() {
    self.number = 0
  }
}
