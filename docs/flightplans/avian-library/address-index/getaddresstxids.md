# getaddresstxids

Returns the txids for an address(es) (requires addressindex to be enabled).

## Arguments:
```
{
  "addresses"
    [
      "address"  (string) The base58check encoded address
      ,...
    ]
  "start" (number, optional) The start block height
  "end" (number, optional) The end block height
},
"includeAssets" (boolean, optional, default false)  If true this will return an expanded result which includes asset transactions
```

## Result:
```
[
  "transactionid"  (string) The transaction id
  ,...
]
```

## Examples:
```avian-cli getaddresstxids '{"addresses": ["12c6DSiU4Rq3P4ZxziKxzrL5LmMBrzjrJX"]}'```