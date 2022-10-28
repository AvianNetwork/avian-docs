---
title: Examples
description: Example fictitious usecases for Avian Flight Plans
---

# Examples

## Example 1: Real life usecase
!!! note

    The following example is purely fictitious and does not showcase the final product. The sole purpose of this example is to provide a basic workflow on how smart contracts can be used. 

Let’s suppose a simple example. A social media website wants to keep track of a like counter and wants to use the Avian blockchain to keep track of a decentralized matter. 

### This would be their workflow:

- [ ] Install the Avian wallet
   
- [ ] Write code
    
- [ ] Deploy code to Avian blockchain
   
- [ ] Hook website to call flight plan function


### Let’s write the smart contract
![Lua code](https://aviannetwork.github.io/avian-docs/assets/img/image7.png)

### How to call the functions?
Use this RPC method:

```
call_flightplan [flight plan name] [function name] [args] 
```

![RPC](https://aviannetwork.github.io/avian-docs/assets/img/image11.png)
*Figure 1 - An example of calling an Avian flight plan via the RPC*

### How would you show the likes on the website?
Since a new RPC call will allow users to call flight plan functions, any RPC library should work. This means almost any programming language that supports HTTP calls can use Avian smart contracts. Figure 2 will show a simple example in React which is a popular frontend framework.

![React code](https://aviannetwork.github.io/avian-docs/assets/img/image15.png)
*Figure 2 - Example React code using RPC to interact with a flight plan to display the like count.*

## Example 2: Creating a DNS system
!!! note
    This example is theoretical and only serves to show how flight plans can be coded.  

Let’s create a DNS system using Avian flight plans! Our current DNS is used to convert domain names such as “avn.network” to their correct IP address. Unfortunately, DNS is centralized, so let’s take the opportunity to use assets and smart contracts to create a basic DNS system in Avian. 

![DNS](https://aviannetwork.github.io/avian-docs/assets/img/image20.png)
*Figure 5 shows the code to implement our decentralized DNS flight plan.*

## Example 3: Linking to Python
![python](https://aviannetwork.github.io/avian-docs/assets/img/image34.png)
![py code](https://aviannetwork.github.io/avian-docs/assets/img/image33.png)


## Example 4: Linking to Web using SvelteKit
*Server side rendering using Svelte Kit and NodeJS*
![web outpit](https://aviannetwork.github.io/avian-docs/assets/img/image17.png)
![svelte code](https://aviannetwork.github.io/avian-docs/assets/img/image38.png)
