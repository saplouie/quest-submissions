pub contract Cars {

    pub var arrayOfMakes: @[Make]

    pub resource Make {
        pub let name: String
        init() {
            self.name = "Ford"
        }
    }

    pub fun addMake(make: @Make) {
        self.arrayOfMakes.append(<- make)
    }

    pub fun removeMake(index: Int): @Make {
        return <- self.arrayOfMakes.remove(at: index)
    }

    pub var dictionaryOfModels: @{String : Model}

    pub resource Model {
        pub let modelName: String
        init() {
            self.modelName = "Mustang"
        }
    }

    pub fun addModel(model: @Model) {
        let key = model.modelName
        let oldModel <- self.dictionaryOfModels[key] <- model
        destroy oldModel
    }
    
    pub fun removeModel(key: String): @Model {
        let modelName <- self.dictionaryOfModels.remove(key: key) ?? panic("Could not find the model!")
        return <- modelName
    }    

    init() {
        self.arrayOfMakes <- []
        self.dictionaryOfModels <- {}
    }
}
