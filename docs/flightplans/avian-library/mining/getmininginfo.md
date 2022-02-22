# getmininginfo

Returns a json object containing mining-related information.

## Result:
```json
{
  "blocks": nnn,             (numeric) The current block
  "currentblockweight": nnn, (numeric) The last block weight
  "currentblocktx": nnn,     (numeric) The last block transaction
  "difficulty": xxx.xxxxx    (numeric) The current difficulty for pre-Crow
  "difficulty_algorithm": x.x (numeric) the current difficulty for Crow once activated per algorithm
  "networkhashps": nnn,      (numeric) The network hashes per second
  "hashespersec": nnn,       (numeric) The hashes per second of built-in miner
  "pooledtx": n              (numeric) The size of the mempool
  "chain": "xxxx",           (string) current network name as defined in BIP70 (main, test, regtest)
  "warnings": "..."          (string) any network and blockchain warnings
  "errors": "..."            (string) DEPRECATED. Same as warnings. Only shown when aviand is started with -deprecatedrpc=getmininginfo
}
```

## Examples:

```avian-cli getmininginfo```