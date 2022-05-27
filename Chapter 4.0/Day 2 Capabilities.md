1. What does .link() do? It creates a pointer in /public/ or /private/ that points to a resource in /storage/, so it can be accessed.

2. In your own words (no code), explain how we can use resource interfaces to only expose certain things to the /public/ path.
Create an interface that only contains fields and functions that you want to give access to. Then link them to /public/ using the interface. 

3.Deploy a contract that contains a resource that implements a resource interface. Then, do the following:
![image](https://user-images.githubusercontent.com/26511703/170647559-2977f812-bbb2-4e21-8753-aa8982fd7cfd.png)

i. In a transaction, save the resource to storage and link it to the public with the restrictive interface.
![image](https://user-images.githubusercontent.com/26511703/170647592-7404d954-cf57-425b-a3e9-4a24e95a5d97.png)

ii. Run a script that tries to access a non-exposed field in the resource interface, and see the error pop up.
![image](https://user-images.githubusercontent.com/26511703/170647810-658cc38c-d633-4634-8b09-75518a5c1211.png)

iii. Run the script and access something you CAN read from. Return it from the script.
![image](https://user-images.githubusercontent.com/26511703/170647519-157adaef-a89b-460e-bcec-cc2eee8fdb6b.png)
