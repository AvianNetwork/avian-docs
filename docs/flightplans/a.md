# Introdution

## What are Avian Flight Plans?
!!! note

    Avian Flight Plans can compared as *smart contracts* but are **NOT** the same thing. Avian Flight Plans is a scripting frotend for RPC methods.

Users of the Avian Network can create assets and decide their purpose and rules independent of the protocol. To further leverage and automate the use of assets, flight plans can be used to assist in this task. Flight plans allow the users to design their own protocol according to their needs, allowing further control over assets. 
Assets themselves alone can be transferred, minted, etc. We want to further unlock the capabilities of assets by developing a smart contract system to allow developers to have greater control and automation over assets. Although RPC commands exist for token management, a scripting language will allow more control and help with readability as opposed to using multiple RPC methods.

## Basic example

### Flight plan code (test.lua)

!!! note

    Avian Flight Plans are written in the Lua programming language. 

    To learn more about the `avian` object, refer to [Avian Lib ↗](avian-library)

```lua
-- Function to get random block
function rnd_hash()
    height = math.random(1, 3000)
    return avian.blockchain.getblockhash(height)
end

-- Print time of random block
function info_hash()
    block = json.decode(avian.blockchain.getblock(rnd_hash()))
    time = os.date("%x", block.time)
    return "Result: " .. time
end

```

### Calling function using RPC

!!! note "RPC"

    Since Avian Flight Plans can called using the RPC, this allows flight plans to be called from any programming language that supports Bitcoin RPC. We will use `avian-cli` for this example.

```bash
avian-cli call_function test info_hash
```

### Output
```
Result: 01/15/2022
```

## Links

### [Examples ↗](b)

### [Getting Started ↗](c)

### [Inner workings ↗](d)

### [Avian Lib ↗](avian-library)
