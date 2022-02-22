# getaddressdeltas

Returns all changes for an address (requires addressindex to be enabled).

## Arguments:
```
{
  "addresses"
    [
      "address"  (string) The base58check encoded address
      ,...
    ]
  "start" (number) The start block height
  "end" (number) The end block height
  "chainInfo" (boolean) Include chain info in results, only applies if start and end specified
  "assetName"   (string, optional) Get deltas for a particular asset instead of AVN.
}
```

## Result:
```
[
  {
    "assetName"  (string) The asset associated with the deltas (AVN for Aviancoin)
    "satoshis"  (number) The difference of satoshis
    "txid"  (string) The related txid
    "index"  (number) The related input or output index
    "height"  (number) The block height
    "address"  (string) The base58check encoded address
  }
]
```

## Examples:

```avian-cli getaddressdeltas '{"addresses": ["12c6DSiU4Rq3P4ZxziKxzrL5LmMBrzjrJX"]}'```


```avian-cli getaddressdeltas '{"addresses": ["12c6DSiU4Rq3P4ZxziKxzrL5LmMBrzjrJX"],"assetName":"MY_ASSET"}'```