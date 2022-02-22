# disconnectnode

> *disconnectnode "[address]" [nodeid]*

Immediately disconnects from the specified peer node.

Strictly one out of 'address' and 'nodeid' can be provided to identify the node.

To disconnect by nodeid, either set 'address' to the empty string, or call using the named 'nodeid' argument only.

Arguments:
```
1. "address"     (string, optional) The IP address/port of the node
2. "nodeid"      (number, optional) The node ID (see getpeerinfo for node IDs)
```

Examples:

> avian-cli disconnectnode "192.168.0.6:8767"

> avian-cli disconnectnode "" 1