# getrawtransaction

!!! note
    NOTE: By default this function only works for mempool transactions. If the -txindex option is
    enabled, it also works for blockchain transactions.

!!! warning
    DEPRECATED: for now, it also works for transactions with unspent outputs.

Return the raw transaction data.

* If verbose is 'true', returns an Object with information about 'txid'.

* If verbose is 'false' or omitted, returns a string that is serialized, hex-encoded data for 'txid'.

## Arguments:
```
1. "txid"      (string, required) The transaction id
2. verbose       (bool, optional, default=false) If false, return a string, otherwise return a json object
```

## Result (if verbose is not set or set to false):
```
"data"      (string) The serialized, hex-encoded data for 'txid'
```

## Result (if verbose is set to true):
```json
{
  "hex" : "data",       (string) The serialized, hex-encoded data for 'txid'
  "txid" : "id",        (string) The transaction id (same as provided)
  "hash" : "id",        (string) The transaction hash (differs from txid for witness transactions)
  "size" : n,             (numeric) The serialized transaction size
  "vsize" : n,            (numeric) The virtual transaction size (differs from size for witness transactions)
  "version" : n,          (numeric) The version
  "locktime" : ttt,       (numeric) The lock time
  "vin" : [               (array of json objects)
     {
       "txid": "id",    (string) The transaction id
       "vout": n,         (numeric) 
       "scriptSig": {     (json object) The script
         "asm": "asm",  (string) asm
         "hex": "hex"   (string) hex
       },
       "sequence": n      (numeric) The script sequence number
       "txinwitness": ["hex", ...] (array of string) hex-encoded witness data (if any)
     }
     ,...
  ],
  "vout" : [              (array of json objects)
     {
       "value" : x.xxx,            (numeric) The value in AVN
       "n" : n,                    (numeric) index
       "scriptPubKey" : {          (json object)
         "asm" : "asm",          (string) the asm
         "hex" : "hex",          (string) the hex
         "reqSigs" : n,            (numeric) The required sigs
         "type" : "pubkeyhash",  (string) The type, eg 'pubkeyhash'
         "addresses" : [           (json array of string)
           "address"        (string) avian address
           ,...
         ]
       }
     }
     ,...
  ],
  "blockhash" : "hash",   (string) the block hash
  "confirmations" : n,      (numeric) The confirmations
  "time" : ttt,             (numeric) The transaction time in seconds since epoch (Jan 1 1970 GMT)
  "blocktime" : ttt         (numeric) The block time in seconds since epoch (Jan 1 1970 GMT)
}
```

## Examples:

> avian-cli getrawtransaction "mytxid"

> avian-cli getrawtransaction "mytxid" true
