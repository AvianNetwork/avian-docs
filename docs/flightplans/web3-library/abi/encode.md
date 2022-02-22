# web3.abi.encode

This function allows you encode a smart contract call into an ABI hex for use with EVM RPC `web3.polygon.rpc`

## Example
```lua
function wavn_bal(addr)
  abi = web3.abi.encode("balanceOf(address)", addr)

  args = {
    ["to"] = "0x752dc265eaf6da2db0f8e4a32d5596d3f18e8701",
    ["data"] = abi
  }

  res = web3.polygon.rpc("eth_call", json.encode(args) .. ",\"latest\"")
  data = json.decode(res)

  if(data.error ~= nil) then
    return data.error.message
  end

  return data.result .. " wAVN in wei (hex)"
end
```

Line 2 shows the usage of this function.
```lua
abi = web3.abi.encode("balanceOf(address)", "0xfB0758fF4f10Df1804A9E9EB70383af12fC9a358")
```

## Links

[`web3.polygon.rpc` ↗](../polygon/rpc.md) 