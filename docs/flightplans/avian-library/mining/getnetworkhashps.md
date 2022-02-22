# getnetworkhashps

Returns the estimated network hashes per second based on the last n blocks.
Pass in `[blocks]` to override # of blocks, -1 specifies since last difficulty change.
Pass in `[height]` to estimate the network speed at the time when a certain block was found.

## Arguments:

1. nblocks     (numeric, optional, default=5) The number of blocks, or -1 for blocks since last difficulty change.
2. height      (numeric, optional, default=-1) To estimate at the time of the given height.
3. powalgo     (string, optional) This can be set to "minotaurx" or "x16rt". If omitted, wallet's default is assumed (-powalgo conf option)

## Result:
```x             (numeric) Hashes per second estimated```

## Examples:

```avian-cli getnetworkhashps```
