# getchaintxstats

Compute statistics about the total number and rate of transactions in the chain.

Arguments:

1. nblocks      (numeric, optional) Size of the window in number of blocks (default: one month).
2. "blockhash"  (string, optional) The hash of the block that ends the window.

Result:
```
{
  "time": xxxxx,                (numeric) The timestamp for the final block in the window in UNIX format.
  "txcount": xxxxx,             (numeric) The total number of transactions in the chain up to that point.
  "window_block_count": xxxxx,  (numeric) Size of the window in number of blocks.
  "window_tx_count": xxxxx,     (numeric) The number of transactions in the window. Only returned if "window_block_count" is > 0.
  "window_interval": xxxxx,     (numeric) The elapsed time in the window in seconds. Only returned if "window_block_count" is > 0.
  "txrate": x.xx,               (numeric) The average rate of transactions per second in the window. Only returned if "window_interval" is > 0.
}
```

Examples:

```avian-cli getchaintxstats```