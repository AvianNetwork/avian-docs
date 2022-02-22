# verifymessage

Verify a signed message

!!! note
    Not to be confused with messaging assets. This command is used to verify signed messages via `signmessage` from `localWallet`

## Arguments:
```
1. "address"         (string, required) The avian address to use for the signature.
2. "signature"       (string, required) The signature provided by the signer in base 64 encoding (see signmessage).
3. "message"         (string, required) The message that was signed.
```

## Result:
```
true|false   (boolean) If the signature is verified or not.
```

## Examples:

Unlock the wallet for 30 seconds
> avian-cli walletpassphrase "mypassphrase" 30
Verify a signed message

Arguments:
1. "address"         (string, required) The avian address to use for the signature.
2. "signature"       (string, required) The signature provided by the signer in base 64 encoding (see signmessage).
3. "message"         (string, required) The message that was signed.

Result:
true|false   (boolean) If the signature is verified or not.

Examples:

Unlock the wallet for 30 seconds
> avian-cli walletpassphrase "mypassphrase" 30

Create the signature
> avian-cli signmessage "1D1ZrZNe3JUo7ZycKEYQQiQAWd9y54F4XX" "my message"

Verify the signature
> avian-cli verifymessage "1D1ZrZNe3JUo7ZycKEYQQiQAWd9y54F4XX" "signature" "my message"

As json rpc
> curl --user myusername --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "verifymessage", "params": ["1D1ZrZNe3JUo7ZycKEYQQiQAWd9y54F4XX", "signature", "my message"] }' -H 'content-type: text/plain;' http://127.0.0.1:8766/
Create the signature
> avian-cli signmessage "1D1ZrZNe3JUo7ZycKEYQQiQAWd9y54F4XX" "my message"

Verify the signature
> avian-cli verifymessage "1D1ZrZNe3JUo7ZycKEYQQiQAWd9y54F4XX" "signature" "my message"

As json rpc
> curl --user myusername --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "verifymessage", "params": ["1D1ZrZNe3JUo7ZycKEYQQiQAWd9y54F4XX", "signature", "my message"] }' -H 'content-type: text/plain;' http://127.0.0.1:8766/