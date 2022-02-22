# web3.polygon.rpc

This function allows you to make a JSON-RPC call to the Polygon (MATIC) chain.

## Example
```lua
function wavn_bal(addr)
  args = {
    ["to"] = "0x752dc265eaf6da2db0f8e4a32d5596d3f18e8701",
    ["data"] = "0x70a08231000000000000000000000000fb0758ff4f10df1804a9e9eb70383af12fc9a358"
  }

  -- Data is ETH ABI in Hex which is "balanceOf 0xfB0758fF4f10Df1804A9E9EB70383af12fC9a358"

  res = net.polygon.rpc("eth_call", json.encode(args) .. ",\"latest\"")
  data = json.decode(res)

  if(data.error ~= nil) then
    return data.error.message
  end

  return data.result .. " wAVN in wei (hex)"
end
```

If you convert the resulthex to decimal, you get `18000000000000000000` then convert from wei to wAVN by multiplying by `10^−18` then you get 18 wAVN.

## Links

[`web3.abi.encode` ↗](../abi/encode.md)
 