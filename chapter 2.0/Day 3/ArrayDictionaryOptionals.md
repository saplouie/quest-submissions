1. In a script, initialize an array (that has length == 3) of your favourite people, represented as Strings, and log it.
![image](https://user-images.githubusercontent.com/26511703/168449467-9f851e6f-8bdb-4e5f-a67e-b94c604807fd.png)

2. In a script, initialize a dictionary that maps the Strings Facebook, Instagram, Twitter, YouTube, Reddit, and LinkedIn to a UInt64 that represents the order in which you use them from most to least. For example, YouTube --> 1, Reddit --> 2, etc. If you've never used one before, map it to 0!
![image](https://user-images.githubusercontent.com/26511703/168448787-c79df53d-6730-4d98-afb0-d139052c0fe7.png)

3. Explain what the force unwrap operator ! does, with an example different from the one I showed you (you can just change the type). - Removes the optional type from the variable and throws an error if nil is found.
![image](https://user-images.githubusercontent.com/26511703/168449401-cd8382f3-bb2a-41b6-b073-46c6ac050093.png)

4. Using this picture below, explain...

What the error message means. -The error means the type that needs to be returned is of type String and doesn't match the actual type returned, an Optional String.

Why we're getting this error - thing[0x03] is an element of a dictionary with type Optional String. The main function is wanting a return type of String.

How to fix it - We can fix it by changing the return value to an optional type
![image](https://user-images.githubusercontent.com/26511703/168449089-2dc26619-52ae-466e-9844-9b6dcda206f8.png)

Alternatively, the return can be unwrapped with the following statement:

return thing[0x03]!

