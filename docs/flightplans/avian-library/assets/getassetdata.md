# getassetdata

Returns assets metadata if that asset exists

Arguments:
1. "asset_name"               (string, required) the name of the asset

Result:
```json
{
  name: (string),
  amount: (number),
  units: (number),
  reissuable: (number),
  has_ipfs: (number),
  ipfs_hash: (hash), (only if has_ipfs = 1 and that data is a ipfs hash)
  txid_hash: (hash), (only if has_ipfs = 1 and that data is a txid hash)
  verifier_string: (string)
}
```

Examples:

```avian-cli getassetdata "ASSET_NAME"```