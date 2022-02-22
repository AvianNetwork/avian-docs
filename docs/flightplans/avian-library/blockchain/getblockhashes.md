# getblockhashes

Returns array of hashes of blocks within the timestamp range provided.

Arguments:

1. high         (numeric, required) The newer block timestamp
2. low          (numeric, required) The older block timestamp
3. options      (string, required) A json object
```
    {
      "noOrphans":true   (boolean) will only include blocks on the main chain
      "logicalTimes":true   (boolean) will include logical timestamps with hashes
    }
```

Result:
```
[
  "hash"         (string) The block hash
]
[
  {
    "blockhash": (string) The block hash
    "logicalts": (numeric) The logical timestamp
  }
]
```

Examples:

```avian-cli getblockhashes 1231614698 1231024505```