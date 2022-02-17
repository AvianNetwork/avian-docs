# Example

!!! note "Note:"

    The following example is purely fictitious and does not showcase the final product. The sole purpose of this example is to provide a basic workflow on how smart contracts can be used. 

Let’s suppose a simple example. A social media website wants to keep track of a like counter and wants to use the Avian blockchain to keep track of a decentralized matter. 

This would be their workflow:

- [ ] Install an Avian wallet
   
- [ ] Write code
    
- [ ] Deploy code to Avian blockchain
   
- [ ] Hook website to call flight plan function


## Let’s write the smart contract

## How to call the functions?
We will create a new RPC method called:

```
call_function [flight plan name] [function name] [args] 
```

Figure 2 - An example of calling an Avian flight plan via the RPC

## How would you show the likes on the website?
Since we will add a new RPC call to allow users to call flight plan functions, any RPC library should work. This means almost any programming language that supports HTTP calls can use Avian smart contracts. Figure 3 will show a simple example in React which is a popular frontend framework.

Figure 4 - Example React code using RPC to interact with a flight plan to display the like count.
