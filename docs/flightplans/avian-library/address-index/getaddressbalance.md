# getaddressbalance

Returns the balance for an address(es) (requires addressindex to be enabled).

##Arguments:
```
{
  "addresses:"
    [
      "address"  (string) The base58check encoded address
      ,...
    ]
},
"includeAssets" (boolean, optional, default false)  If true this will return an expanded result which includes asset balances
```

## Result:
```
{
  "balance"  (string) The current balance in satoshis
  "received"  (string) The total number of satoshis received (including change)
}
```

**OR**

```
[
  {
    "assetName"  (string) The asset associated with the balance (AVN for Aviancoin)
    "balance"  (string) The current balance in satoshis
    "received"  (string) The total number of satoshis received (including change)
  },...

]
```

## Examples:

```avian-cli getaddressbalance '{"addresses": ["12c6DSiU4Rq3P4ZxziKxzrL5LmMBrzjrJX"]}'```