# getdifficulty

getdifficulty ( powalgo )

Returns the proof-of-work difficulty as a multiple of the minimum difficulty.

Arguments:

1. "powalgo":"xxxx"     (string, optional) This can be set to "x16rt" or "minotaurx". If omitted, wallet's default is assumed (-powalgo conf option)

Result:
```
n.nnn       (numeric) the proof-of-work difficulty as a multiple of the minimum difficulty.
```

Examples:

```avian-cli getdifficulty```