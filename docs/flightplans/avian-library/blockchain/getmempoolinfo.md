# getmempoolinfo

Returns details on the active state of the TX memory pool.

## Result:
```
{
  "size": xxxxx,               (numeric) Current tx count
  "bytes": xxxxx,              (numeric) Sum of all virtual transaction sizes as defined in BIP 141. Differs from actual serialized size because witness data is discounted
  "usage": xxxxx,              (numeric) Total memory usage for the mempool
  "maxmempool": xxxxx,         (numeric) Maximum memory usage for the mempool
  "mempoolminfee": xxxxx       (numeric) Minimum fee rate in AVN/kB for tx to be accepted
}
```

## Examples:

```avian-cli getmempoolinfo```