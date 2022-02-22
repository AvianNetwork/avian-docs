# transfer

> *transfer "asset_name" qty "to_address" "message" expire_time "change_address" "asset_change_address"*

Transfers a quantity of an owned asset to a given address

## Arguments:
```
1. "asset_name"               (string, required) name of asset
2. "qty"                      (numeric, required) number of assets you want to send to the address
3. "to_address"               (string, required) address to send the asset to
4. "message"                  (string, optional) Once RIP5 is voted in ipfs hash or txid hash to send along with the transfer
5. "expire_time"              (numeric, optional) UTC timestamp of when the message expires
6. "change_address"       (string, optional, default = "") the transactions AVN change will be sent to this address
7. "asset_change_address"     (string, optional, default = "") the transactions Asset change will be sent to this address
```

## Result:
```
txid[ 
txid
]
```

## Examples:
> avian-cli transfer "ASSET_NAME" 20 "address" "" "QmTqu3Lk3gmTsQVtjU7rYYM37EAW4xNmbuEAp2Mjr4AV7E" 15863654
> avian-cli transfer "ASSET_NAME" 20 "address" "" "QmTqu3Lk3gmTsQVtjU7rYYM37EAW4xNmbuEAp2Mjr4AV7E" 15863654
