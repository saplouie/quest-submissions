1. Explain why we wouldn't call changeGreeting in a script. The function makes a change to the data and scripts do not modify data.

2. What does the AuthAccount mean in the prepare phase of the transaction? The AuthAccount is what is taken in in order to access the data in the signer's account.

3. What is the difference between the prepare phase and the execute phase in the transaction? The prepare phase is for accessing data in the signer's account. The execute phase is for calling the functions.

4. This is the hardest quest so far, so if it takes you some time, do not worry! I can help you in the Discord if you have questions.

*Add two new things inside your contract:
A variable named myNumber that has type Int (set it to 0 when the contract is deployed)
A function named updateMyNumber that takes in a new number named newNumber as a parameter that has type Int and updates myNumber to be newNumber

![image](https://user-images.githubusercontent.com/26511703/168414925-72d910b6-7a3d-4689-9e70-47e997117747.png)


*Add a script that reads myNumber from the contract

![image](https://user-images.githubusercontent.com/26511703/168414963-4d4d93b0-c56c-4e6c-a0e8-1b97f3a326a0.png)

*Add a transaction that takes in a parameter named myNewNumber and passes it into the updateMyNumber function. Verify that your number changed by running the script again.

![image](https://user-images.githubusercontent.com/26511703/168415047-6c71ae50-8a24-4ac1-9549-735c824f15ae.png)

After executing with 33 for NewNumber

![image](https://user-images.githubusercontent.com/26511703/168415123-f9743957-da33-4696-939e-53fbf297023a.png)
