1. Define your own contract that stores a dictionary of resources. Add a function to get a reference to one of the resources in the dictionary.


pub contract CK {

    pub var dictionaryOfCattributes: @{String: Cattribute}

    pub resource Cattribute {
        pub let abbreviation: String
        init(_abbreviation: String) {
            self.abbreviation = _abbreviation
        }
    }

    pub fun getReference(key: String): &Cattribute {
        return &self.dictionaryOfCattributes[key] as &Cattribute
    }

    init() {
        self.dictionaryOfCattributes <- {
            "Jaguar": <- create Cattribute(_abbreviation: "Jag"), 
            "Burmilla": <- create Cattribute(_abbreviation: "Burm")
        }
    }
}

2. Create a script that reads information from that resource using the reference from the function you defined in part 1.
import CK from 0x01

pub fun main(): String {
  let ref = CK.getReference(key: "Jaguar")
  return ref.abbreviation // returns "Jag"
}

3. Explain, in your own words, why references can be useful in Cadence. References are useful so the actual resources don't have to be moved around when trying to use them, especially when no changes are made.

