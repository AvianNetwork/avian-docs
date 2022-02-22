# gettxoutsetinfo

Returns statistics about the unspent transaction output set.

!!! note
    Note this call may take some time.

## Result:
```
{
  "height":n,     (numeric) The current block height (index)
  "bestblock": "hex",   (string) the best block hash hex
  "transactions": n,      (numeric) The number of transactions
  "txouts": n,            (numeric) The number of output transactions
  "bogosize": n,          (numeric) A meaningless metric for UTXO set size
  "hash_serialized_2": "hash", (string) The serialized hash
  "disk_size": n,         (numeric) The estimated size of the chainstate on disk
  "total_amount": x.xxx          (numeric) The total amount
}
```

## Examples:
 
```avian-cli gettxoutsetinfo```