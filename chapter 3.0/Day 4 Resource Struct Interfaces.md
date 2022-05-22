1. Explain, in your own words, the 2 things resource interfaces can be used for (we went over both in today's content). An interface is used to give access to parts of a resource. In that way, resource variables and functions can be hidden or unavailable to other parts of the contract. When a resource implments an interface, the resource has to contain the components of the interface.

2. Define your own contract. Make your own resource interface and a resource that implements the interface. Create 2 functions. In the 1st function, show an example of not restricting the type of the resource and accessing its content. In the 2nd function, show an example of restricting the type of the resource and NOT being able to access its content.

pub contract CK {

    pub resource interface IKitty {
      pub let cattribute: String
    }

    pub resource Kitty: IKitty {
      pub let cattribute: String
      pub let number: Int
      init() {
        self.cattribute = "Jaguar"
        self.number = 100
      }
    }

    pub fun noInterface() {
      let test: @Kitty <- create Kitty()
      log(test.number) // 100

      destroy test
    }

    pub fun yesInterface() {
      let test: @Kitty{IKitty} <- create Kitty()
      log(test.number) // Same error as example. number not exposed in IKitty interface.

      destroy test
    }
}


3. How would we fix this code?

pub contract Stuff {

    pub struct interface ITest {
      pub var greeting: String
      pub var favouriteFruit: String 
      pub fun changeGreeting(newGreeting: String): String // Added to expose function to fixThis()

    }

    // ERROR:
    // `structure Stuff.Test does not conform 
    // to structure interface Stuff.ITest`
    pub struct Test: ITest {
      pub var greeting: String
      pub var favouriteFruit: String  // Added due to requirement in ITest
      
      pub fun changeGreeting(newGreeting: String): String {
        self.greeting = newGreeting
        return self.greeting // returns the new greeting
      }

      init() {
        self.greeting = "Hello!"
        self.favouriteFruit = "Apple" // init required for new variable
      }
    }

    pub fun fixThis() {
      let test: Test{ITest} = Test()
      let newGreeting = test.changeGreeting(newGreeting: "Bonjour!") // ERROR HERE: `member of restricted type is not accessible: changeGreeting`
      log(newGreeting)
    }
}
