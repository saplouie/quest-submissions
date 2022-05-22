1. Explain, in your own words, the 2 things resource interfaces can be used for (we went over both in today's content)

2. Define your own contract. Make your own resource interface and a resource that implements the interface. Create 2 functions. In the 1st function, show an example of not restricting the type of the resource and accessing its content. In the 2nd function, show an example of restricting the type of the resource and NOT being able to access its content.
pub contract CK {

    pub resource interface ITest {
      pub let cattribute: String
    }

    pub resource Kitty: ITest {
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
      let test: @Kitty{ITest} <- create Kitty()
      log(test.number) // ERROR: `member of restricted type is not accessible: number`

      destroy test
    }
}

How would we fix this code?

pub contract Stuff {

    pub struct interface ITest {
      pub var greeting: String
      pub var favouriteFruit: String
    }

    // ERROR:
    // `structure Stuff.Test does not conform 
    // to structure interface Stuff.ITest`
    pub struct Test: ITest {
      pub var greeting: String

      pub fun changeGreeting(newGreeting: String): String {
        self.greeting = newGreeting
        return self.greeting // returns the new greeting
      }

      init() {
        self.greeting = "Hello!"
      }
    }

    pub fun fixThis() {
      let test: Test{ITest} = Test()
      let newGreeting = test.changeGreeting(newGreeting: "Bonjour!") // ERROR HERE: `member of restricted type is not accessible: changeGreeting`
      log(newGreeting)
    }
}
