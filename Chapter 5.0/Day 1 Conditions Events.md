1. Describe what an event is, and why it might be useful to a client. It is something that is broadcast to the outside world when something happens. It is useful when an outside entity like a website can use those events to make changes to their own website.


2. Deploy a contract with an event in it, and emit the event somewhere else in the contract indicating that it happened.
Using the contract in step 2), add some pre conditions and post conditions to your contract to get used to writing them out.
Contract with event and pre and post conditions:

![image](https://user-images.githubusercontent.com/26511703/170854845-dea3118e-1d1e-44b9-95b8-9da6e44fbf1d.png)


For each of the functions below (numberOne, numberTwo, numberThree), follow the instructions.

pub contract Test {
  // TODO
  // Tell me whether or not this function will log the name.
  // name: 'Jacob'

  // It will log Jacob because the pre condition is met of length 5.

pub fun numberOne(name: String) {
    pre {
      name.length == 5: "This name is not cool enough."
    }
    log(name)
  }

  // TODO
  // Tell me whether or not this function will return a value.
  // name: 'Jacob'
  
  // The return value will be Jacob Tucker because name length > 0 and it concats "Jacob" and " Tucker" at the end to meet the post condition.
  
  pub fun numberTwo(name: String): String {
    pre {
      name.length >= 0: "You must input a valid name."
    }
    post {
      result == "Jacob Tucker"
    }
    return name.concat(" Tucker")
  }

  pub resource TestResource {
    pub var number: Int

    // TODO
    // Tell me whether or not this function will log the updated number.
    // Also, tell me the value of `self.number` after it's run.
    
    // It won't log because 0 != 2
    // self.number reverts to 0.

pub fun numberThree(): Int {
      post {
        before(self.number) == result + 1
      }
      self.number = self.number + 1
      return self.number
    }

    init() {
      self.number = 0
    }

  }

}
