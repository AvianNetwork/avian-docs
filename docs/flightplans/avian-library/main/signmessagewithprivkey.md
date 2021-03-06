# signmessagewithprivkey

Sign a message with the private key of an address

## Arguments:
```
1. "privkey"         (string, required) The private key to sign the message with.
2. "message"         (string, required) The message to create a signature of.
```

## Result:
```
"signature"          (string) The signature of the message encoded in base 64
```

## Examples:

* Create the signature

> avian-cli signmessagewithprivkey "privkey" "my message"

* Verify the signature

> avian-cli verifymessage "1D1ZrZNe3JUo7ZycKEYQQiQAWd9y54F4XX" "signature" "my message"

* As json rpc

> curl --user myusername --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "signmessagewithprivkey", "params": ["privkey", "my message"] }' -H 'content-type: text/plain;' http://127.0.0.1:8766/
