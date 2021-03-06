# addnode

> *addnode "node" "add|remove|onetry"*

Attempts to add or remove a node from the addnode list.
Or try a connection to a node once.

Nodes added using addnode (or -connect) are protected from DoS disconnection and are not required to be
full nodes/support SegWit as other outbound peers are (though such peers will not be synced from).

Arguments:
```
1. "node"     (string, required) The node (see getpeerinfo for nodes)
2. "command"  (string, required) 'add' to add a node to the list, 'remove' to remove a node from the list, 'onetry' to try a connection to the node once
```

Examples:

```avian-cli addnode "192.168.0.6:8767" "onetry"```