access(all) contract SomeContract {
    pub var testStruct: SomeStruct

    pub struct SomeStruct {

        //
        // 4 Variables
        //

        pub(set) var a: String

        pub var b: String

        access(contract) var c: String

        access(self) var d: String

        //
        // 3 Functions
        //

        pub fun publicFunc() {}

        access(contract) fun contractFunc() {}

        access(self) fun privateFunc() {}


        pub fun structFunc() {
            /**************/ a (read,write)   b(read,write)
            /*** AREA 1 ***/ c(read,write)    d(read,write)
            /**************/ Functions that can be run publicFunc, contractFunc, and privateFunc
        }

        init() {
            self.a = "a"
            self.b = "b"
            self.c = "c"
            self.d = "d"
        }
    }

    pub resource SomeResource {
        pub var e: Int

        pub fun resourceFunc() {
            /**************/ a(read,write)  b(read)
            /*** AREA 2 ***/ c(read)        d(none)
            /**************/  Functions that can be run publicFunc and contractFunc
        }

        init() {
            self.e = 17
        }
    }

    pub fun createSomeResource(): @SomeResource {
        return <- create SomeResource()
    }

    pub fun questsAreFun() {
        /**************/  a(read,write)  b(read)
        /*** AREA 3 ****/ c(read)        d(none)
        /**************/  Functions that can be run publicFunc and contractFunc
    }

    init() {
        self.testStruct = SomeStruct()
    }
}
This is a script that imports the contract above:

import SomeContract from 0x01

pub fun main() {
  /**************/  a(read)    b(read)
  /*** AREA 4 ***/  c(none)          d(none)
  /**************/ Functions that can be called: publicFunc
}
