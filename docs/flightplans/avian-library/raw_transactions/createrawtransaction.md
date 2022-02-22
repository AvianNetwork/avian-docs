# createrawtransaction

> *createrawtransaction [{"txid":"id","vout":n},...] {"address":(amount or object),"data":"hex",...} ( locktime ) ( replaceable )*

Create a transaction spending the given inputs and creating new outputs.
Outputs are addresses (paired with a AVN amount, data or object specifying an asset operation) or data.
Returns hex-encoded raw transaction.

!!! note
    Note that the transaction's inputs are not signed, and
    it is not stored in the wallet or transmitted to the network.

## Paying for Asset Operations:
  Some operations require an amount of AVN to be sent to a burn address:

    Operation          Amount + Burn Address
    transfer                 0
    transferwithmessage      0
    issue                  500 to n1issueAssetXXXXXXXXXXXXXXXXWdnemQ
    issue (subasset)       100 to n1issueSubAssetXXXXXXXXXXXXXbNiH6v
    issue_unique             5 to n1issueUniqueAssetXXXXXXXXXXS4695i
    reissue                100 to n1ReissueAssetXXXXXXXXXXXXXXWG9NLd
    issue_restricted      1500 to n1issueRestrictedXXXXXXXXXXXXZVT9V
    reissue_restricted     100 to n1ReissueAssetXXXXXXXXXXXXXXWG9NLd
    issue_qualifier       1000 to n1issueQuaLifierXXXXXXXXXXXXUysLTj
    issue_qualifier (sub)  100 to n1issueSubQuaLifierXXXXXXXXXYffPLh
    tag_addresses          0.1 to n1addTagBurnXXXXXXXXXXXXXXXXX5oLMH (per address)
    untag_addresses        0.1 to n1addTagBurnXXXXXXXXXXXXXXXXX5oLMH (per address)
    freeze_addresses         0
    unfreeze_addresses       0
    freeze_asset             0
    unfreeze_asset           0

## Assets For Authorization:
  These operations require a specific asset input for authorization:

    Root Owner Token:
      reissue
      issue_unique
      issue_restricted
      reissue_restricted
      freeze_addresses
      unfreeze_addresses
      freeze_asset
      unfreeze_asset

    Root Qualifier Token:
      issue_qualifier (when issuing subqualifier)
      
    Qualifier Token:
      tag_addresses
      untag_addresses

## Output Ordering:
  Asset operations require the following:

    1) All coin outputs come first (including the burn output).

    2) The owner token change output comes next (if required).

    3) An issue, reissue, or any number of transfers comes last
       (different types can't be mixed in a single transaction).

## Arguments:
```json
1. "inputs"                                (array, required) A json array of json objects
     [
       {
         "txid":"id",                      (string, required) The transaction id
         "vout":n,                         (number, required) The output number
         "sequence":n                      (number, optional) The sequence number
       } 
       ,...
     ]
2. "outputs"                               (object, required) a json object with outputs
     {
       "address":                          (string, required) The destination avian address.
                                               Each output must have a different address.
         x.xxx                             (number or string, required) The AVN amount
           or
         {                                 (object) A json object of assets to send
           "transfer":
             {
               "asset-name":               (string, required) asset name
               asset-quantity              (number, required) the number of raw units to transfer
               ,...
             }
         }
           or
         {                                 (object) A json object of describing the transfer and message contents to send
           "transferwithmessage":
             {
               "asset-name":              (string, required) asset name
               asset-quantity,            (number, required) the number of raw units to transfer
               "message":"hash",          (string, required) ipfs hash or a txid hash
               "expire_time": n           (number, required) utc time in seconds to expire the message
             }
         }
           or
         {                                 (object) A json object describing new assets to issue
           "issue":
             {
               "asset_name":"asset-name",  (string, required) new asset name
               "asset_quantity":n,         (number, required) the number of raw units to issue
               "units":[1-8],              (number, required) display units, between 1 (integral) to 8 (max precision)
               "reissuable":[0-1],         (number, required) 1=reissuable asset
               "has_ipfs":[0-1],           (number, required) 1=passing ipfs_hash
               "ipfs_hash":"hash"          (string, optional) an ipfs hash for discovering asset metadata
             }
         }
           or
         {                                 (object) A json object describing new unique assets to issue
           "issue_unique":
             {
               "root_name":"root-name",         (string, required) name of the asset the unique asset(s) 
                                                      are being issued under
               "asset_tags":["asset_tag", ...], (array, required) the unique tag for each asset which is to be issued
               "ipfs_hashes":["hash", ...],     (array, optional) ipfs hashes corresponding to each supplied tag 
                                                      (should be same size as "asset_tags")
             }
         }
           or
         {                                 (object) A json object describing follow-on asset issue.
           "reissue":
             {
               "asset_name":"asset-name", (string, required) name of asset to be reissued
               "asset_quantity":n,          (number, required) the number of raw units to issue
               "reissuable":[0-1],          (number, optional) default is 1, 1=reissuable asset
               "ipfs_hash":"hash",        (string, optional) An ipfs hash for discovering asset metadata, 
                                                Overrides the current ipfs hash if given
               "owner_change_address"       (string, optional) the address where the owner token will be sent to. 
                                                If not given, it will be sent to the output address
             }
         }
           or
         {                                 (object) A json object describing how restricted asset to issue
           "issue_restricted":
             {
               "asset_name":"asset-name",(string, required) new asset name
               "asset_quantity":n,         (number, required) the number of raw units to issue
               "verifier_string":"text", (string, required) the verifier string to be used for a restricted 
                                               asset transfer verification
               "units":[0-8],              (number, required) display units, between 0 (integral) and 8 (max precision)
               "reissuable":[0-1],         (number, required) 1=reissuable asset
               "has_ipfs":[0-1],           (number, required) 1=passing ipfs_hash
               "ipfs_hash":"hash",       (string, optional) an ipfs hash for discovering asset metadata
               "owner_change_address"      (string, optional) the address where the owner token will be sent to. 
                                               If not given, it will be sent to the output address
             }
         }
           or
         {                                 (object) A json object describing follow-on asset issue.
           "reissue_restricted":
             {
               "asset_name":"asset-name", (string, required) name of asset to be reissued
               "asset_quantity":n,          (number, required) the number of raw units to issue
               "reissuable":[0-1],          (number, optional) default is 1, 1=reissuable asset
               "verifier_string":"text",  (string, optional) the verifier string to be used for a restricted asset 
                                                transfer verification
               "ipfs_hash":"hash",        (string, optional) An ipfs hash for discovering asset metadata, 
                                                Overrides the current ipfs hash if given
               "owner_change_address"       (string, optional) the address where the owner token will be sent to. 
                                                If not given, it will be sent to the output address
             }
         }
           or
         {                                 (object) A json object describing a new qualifier to issue.
           "issue_qualifier":
             {
               "asset_name":"asset_name", (string, required) a qualifier name (starts with '#')
               "asset_quantity":n,          (numeric, optional, default=1) the number of units to be issued (1 to 10)
               "has_ipfs":[0-1],            (boolean, optional, default=false), whether ifps hash is going 
                                                to be added to the asset
               "ipfs_hash":"hash",        (string, optional but required if has_ipfs = 1), an ipfs hash or a 
                                                txid hash once RIP5 is activated
               "root_change_address"        (string, optional) Only applies when issuing subqualifiers.
                                                The address where the root qualifier will be sent.
                                                If not specified, it will be sent to the output address.
               "change_quantity":"qty"    (numeric, optional) the asset change amount (defaults to 1)
             }
         }
           or
         {                                 (object) A json object describing addresses to be tagged.
                                             The address in the key will used as the asset change address.
           "tag_addresses":
             {
               "qualifier":"qualifier",          (string, required) a qualifier name (starts with '#')
               "addresses":["addr", ...],        (array, required) the addresses to be tagged (up to 10)
               "change_quantity":"qty",          (numeric, optional) the asset change amount (defaults to 1)
             }
         }
           or
         {                                 (object) A json object describing addresses to be untagged.
                                             The address in the key will be used as the asset change address.
           "untag_addresses":
             {
               "qualifier":"qualifier",          (string, required) a qualifier name (starts with '#')
               "addresses":["addr", ...],        (array, required) the addresses to be untagged (up to 10)
               "change_quantity":"qty",          (numeric, optional) the asset change amount (defaults to 1)
             }
         }
           or
         {                                 (object) A json object describing addresses to be frozen.
                                             The address in the key will used as the owner change address.
           "freeze_addresses":
             {
               "asset_name":"asset_name",        (string, required) a restricted asset name (starts with '$')
               "addresses":["addr", ...],        (array, required) the addresses to be frozen (up to 10)
             }
         }
           or
         {                                 (object) A json object describing addresses to be frozen.
                                             The address in the key will be used as the owner change address.
           "unfreeze_addresses":
             {
               "asset_name":"asset_name",        (string, required) a restricted asset name (starts with '$')
               "addresses":["addr", ...],        (array, required) the addresses to be untagged (up to 10)
             }
         }
           or
         {                                 (object) A json object describing an asset to be frozen.
                                             The address in the key will used as the owner change address.
           "freeze_asset":
             {
               "asset_name":"asset_name",        (string, required) a restricted asset name (starts with '$')
             }
         }
           or
         {                                 (object) A json object describing an asset to be frozen.
                                             The address in the key will be used as the owner change address.
           "unfreeze_asset":
             {
               "asset_name":"asset_name",        (string, required) a restricted asset name (starts with '$')
             }
         }
           or
       "data": "hex"                       (string, required) The key is "data", the value is hex encoded data
       ,...
     }
3. locktime                  (numeric, optional, default=0) Raw locktime. Non-0 value also locktime-activates inputs
```

## Result:
```
"transaction"              (string) hex string of the transaction
```

## Examples:

> avian-cli createrawtransaction "[{\"txid\":\"mycoin\",\"vout\":0}]" "{\"address\":0.01}"

> avian-cli createrawtransaction "[{\"txid\":\"mycoin\",\"vout\":0}]" "{\"data\":\"00010203\"}"

> avian-cli createrawtransaction "[{\"txid\":\"mycoin\",\"vout\":0}]" "{\"RXissueAssetXXXXXXXXXXXXXXXXXhhZGt\":500,\"change_address\":change_amount,\"issuer_address\":{\"issue\":{\"asset_name\":\"MYASSET\",\"asset_quantity\":1000000,\"units\":1,\"reissuable\":0,\"has_ipfs\":1,\"ipfs_hash\":\"43f81c6f2c0593bde5a85e09ae662816eca80797\"}}}"

> avian-cli createrawtransaction "[{\"txid\":\"mycoin\",\"vout\":0}]" "{\"RXissueRestrictedXXXXXXXXXXXXzJZ1q\":1500,\"change_address\":change_amount,\"issuer_address\":{\"issue_restricted\":{\"asset_name\":\"$MYASSET\",\"asset_quantity\":1000000,\"verifier_string\":\"#TAG & !KYC\",\"units\":1,\"reissuable\":0,\"has_ipfs\":1,\"ipfs_hash\":\"43f81c6f2c0593bde5a85e09ae662816eca80797\"}}}"

> avian-cli createrawtransaction "[{\"txid\":\"mycoin\",\"vout\":0}]" "{\"RXissueUniqueAssetXXXXXXXXXXWEAe58\":20,\"change_address\":change_amount,\"issuer_address\":{\"issue_unique\":{\"root_name\":\"MYASSET\",\"asset_tags\":[\"ALPHA\",\"BETA\"],\"ipfs_hashes\":[\"43f81c6f2c0593bde5a85e09ae662816eca80797\",\"43f81c6f2c0593bde5a85e09ae662816eca80797\"]}}}"

> avian-cli createrawtransaction "[{\"txid\":\"mycoin\",\"vout\":0},{\"txid\":\"myasset\",\"vout\":0}]" "{\"address\":{\"transfer\":{\"MYASSET\":50}}}"

> avian-cli createrawtransaction "[{\"txid\":\"mycoin\",\"vout\":0},{\"txid\":\"myasset\",\"vout\":0}]" "{\"address\":{\"transferwithmessage\":{\"MYASSET\":50,\"message\":\"hash\",\"expire_time\": utc_time}}}"

> avian-cli createrawtransaction "[{\"txid\":\"mycoin\",\"vout\":0},{\"txid\":\"myownership\",\"vout\":0}]" "{\"issuer_address\":{\"reissue\":{\"asset_name\":\"MYASSET\",\"asset_quantity\":2000000}}}"

> curl --user myusername --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "createrawtransaction", "params": ["[{\"txid\":\"mycoin\",\"vout\":0}]", "{\"data\":\"00010203\"}"] }' -H 'content-type: text/plain;' http://127.0.0.1:8766/
