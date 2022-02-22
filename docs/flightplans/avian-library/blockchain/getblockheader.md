# getblockheader

If verbose is false, returns a string that is serialized, hex-encoded data for blockheader 'hash'.
If verbose is true, returns an Object with information about blockheader <hash>.

## Arguments:

1. "hash"          (string, required) The block hash
2. verbose           (boolean, optional, default=true) true for a json object, false for the hex encoded data

## Result (for verbose = true):
```
{
  "hash" : "hash",     (string) the block hash (same as provided)
  "powtype" : "x16rt"|"minotaurx"|"unrecognised", (string) Indicates the pow mining type of the block
  "confirmations" : n,   (numeric) The number of confirmations, or -1 if the block is not on the main chain
  "height" : n,          (numeric) The block height or index
  "version" : n,         (numeric) The block version
  "versionHex" : "00000000", (string) The block version formatted in hexadecimal
  "merkleroot" : "xxxx", (string) The merkle root
  "time" : ttt,          (numeric) The block time in seconds since epoch (Jan 1 1970 GMT)
  "mediantime" : ttt,    (numeric) The median block time in seconds since epoch (Jan 1 1970 GMT)
  "nonce" : n,           (numeric) The nonce
  "bits" : "1d00ffff", (string) The bits
  "difficulty" : x.xxx,  (numeric) The difficulty
  "nTx", : "x",        (string) The number of transactions in the block
  "chainwork" : "0000...1f3"     (string) Expected number of hashes required to produce the current chain (in hex)
  "previousblockhash" : "hash",  (string) The hash of the previous block
  "nextblockhash" : "hash",      (string) The hash of the next block
}
```

## Result (for verbose=false):
```
"data"             (string) A string that is serialized, hex-encoded data for block 'hash'.
```

Examples:

```avian-cli getblockheader "00000000c937983704a73af28acdec37b049d214adbda81d7e2a3dd146f6ed09"```