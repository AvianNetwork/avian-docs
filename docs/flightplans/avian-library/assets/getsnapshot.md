# getsnapshot

Returns details for the asset snapshot, at the specified height

Arguments:
1. "asset_name"               (string, required) the name of the asset
2. block_height                 (int, required) the block height of the snapshot

Result:
```json
{
  name: (string),
  height: (number),
  owners: [
    {
      address: (string),
      amount_owned: (number),
    }
}
```
