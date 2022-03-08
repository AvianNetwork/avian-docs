# Info

!!! warning
    Using the `web3` library relies on a 3rd party RPC connection via HTTP. We are not responsible for any issues when connecting to the RPC.

    Please keep in mind of [man-in-the-middle attacks](https://en.wikipedia.org/wiki/Man-in-the-middle_attack) and follow appropriate security measures.


!!! info
    To use the `web3` library in flight plans, Avian needs to be launched with the flag: `-flightplans-web3`

    Refer to [Getting Started ↗](../d.md) for more help with flags


Avian Flight Plans contains the **Web3 Library** for full access to the EVM chains, such as ETH or Polygon, in order to interact with smart contracts.

The library is contained in the `web3` object. 
And EVM chains, like "polygon" would look like this: `web3.polygon`

## Polygon (MATIC)
[`web3.polygon.rpc` ↗](polygon/rpc.md)

## ABI (application binary interface)
[`web3.abi.encode` ↗](abi/encode)
