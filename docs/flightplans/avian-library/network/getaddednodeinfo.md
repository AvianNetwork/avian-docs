# getaddednodeinfo

Returns information about the given added node, or all added nodes

!!! note
    Note that onetry addnodes are not listed here.

Arguments:
```
1. "node"   (string, optional) If provided, return information about this specific node, otherwise all nodes are returned.
```

Result:
```json
[
  {
    "addednode" : "192.168.0.201",   (string) The node IP address or name (as provided to addnode)
    "connected" : true|false,          (boolean) If connected
    "addresses" : [                    (list of objects) Only when connected = true
       {
         "address" : "192.168.0.201:8767",  (string) The avian server IP and port we're connected to
         "connected" : "outbound"           (string) connection, inbound or outbound
       }
     ]
  }
  ,...
]
```

Examples:

> avian-cli getaddednodeinfo "192.168.0.201"
