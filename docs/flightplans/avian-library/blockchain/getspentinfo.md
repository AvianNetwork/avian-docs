# getspentinfo

Returns the txid and index where an output is spent.

## Arguments:
```
{
  "txid" (string) The hex string of the txid
  "index" (number) The start block height
}
```

## Result:
```
{ 
  "txid"  (string) The transaction id
  "index"  (number) The spending input index
  ,...
}
```

## Examples:

```avian-cli getspentinfo '{"txid": "0437cd7f8525ceed2324359c2d0ba26006d92d856a9c20fa0241106ee5a597c9", "index": 0}'```