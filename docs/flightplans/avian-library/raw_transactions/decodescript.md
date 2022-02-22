# decodescript

Decode a hex-encoded script.

## Arguments:
```
1. "hexstring"     (string) the hex encoded script
```

## Result:
```
{
  "asm":"asm",   (string) Script public key
  "hex":"hex",   (string) hex encoded public key
  "type":"type", (string) The output type
  "asset" : {               (json object) optional
     "name" : "name",      (string) the asset name
     "amount" : n,           (numeric) the amount of asset that was sent
     "message" : "message", (string optional) the message if one was sent
     "expire_time" : n,      (numeric optional ) the message epoch expiration time if one was set
  "reqSigs": n,    (numeric) The required signatures
  "addresses": [   (json array of string)
     "address"     (string) avian address
     ,...
  ],
  "p2sh":"address",       (string) address of P2SH script wrapping this redeem script (not returned if the script is already a P2SH).
  "(The following only appears if the script is an asset script)
  "asset_name":"name",      (string) Name of the asset.
  "amount":"x.xx",          (numeric) The amount of assets interacted with.
  "units": n,                (numeric) The units of the asset. (Only appears in the type (new_asset))
  "reissuable": true|false, (boolean) If this asset is reissuable. (Only appears in type (new_asset|reissue_asset))
  "hasIPFS": true|false,    (boolean) If this asset has an IPFS hash. (Only appears in type (new_asset if hasIPFS is true))
  "ipfs_hash": "hash",      (string) The ipfs hash for the new asset. (Only appears in type (new_asset))
  "new_ipfs_hash":"hash",    (string) If new ipfs hash (Only appears in type. (reissue_asset))
}
```

## Examples:

```avian-cli decodescript "hexstring"```
