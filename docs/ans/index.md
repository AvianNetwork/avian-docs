# Avian Name System

!!! note

    This document is based on [Avian Improvement Proposals #4](https://github.com/alamshafil/aips/blob/main/aip-0004.mediawiki)

!!! warning

    Avian Name System is rapidly changing in development and any info stated to subject to change.

```
  AIP: 4
  Title: Avian Name System (ANS)
  Author: Shafil Alam <alamshafil@pm.me>
  Comments-Summary: No comments yet.
  Comments-URI: https://github.com/AvianNetwork/aips
  Status: Draft
  Type: Standards
  Created: 2022-08-29
```

## Abstract
Create a system that allows assets to be mapped to an Avian address or IP address for DNS purposes.

## Motivation
Currently, assets can store an IPFS hash or a TXID hash as metadata. This limit to the on-chain metadata length is 64 characters, 
meaning we can store any arbitrary data that is less than 64 characters. Using this fact, we can store metadata in a standardized manner that maps to an Avian address 
or IP address for DNS purposes. This increases the possible use-cases of assets and increases demand for them. People will be able to sell assets like domain names or 
sell them for custom names to link their address to. However, abuses and everything else must be considered and researched.

## Specification
The ANS system requires multiple specifications to work efficiently.

### ANS IDs
In order to efficiently store data within the 64 character limit, a standardized system will be in place to express addresses, IPs, etc. in the shortest manner possible.

- *(Prefix)* An ANS ID will be less than or equal to 64 characters and will start with unique character to distinguish it from IPFS hash or TXID. 
    - It is proposed to start an ANS ID with "ANS". It is recommended that this prefix is less than 3 characters to allow more data to be stored within the 64 character limit.
- *(Type)* An single hex value from 0-F will determine the type of ANS ID. This will make it easy to quickly get the type of data stored in the ANS ID.
    - 0 = Avian address
    - 1 = IP address (DNS A record)
- *(Raw data)* After the type, the data raw will come next. This can a Base58 address or a hex-encoded IP address. Examples:
    - Address = RXBurnXXXXXXXXXXXXXXXXXXXXXXWUo9FV
    - IP = 7f000001 (127.0.0.1)

Using the IP address in hex format is compact and efficient. IPv4 address can go up to 255 in decimal, which is 0xFF in hex. Since IPv4 address have four octets, only 8 *(4\*2)* characters are needed (ff-ff-ff-ff).

Base58 address can have 26 to 36 characters which will fit in our 64 character limit. 3 char *(prefix)* + 1 char *(type hex)* + 36 char *(address)* = 40 characters which is <= 64 characters limit.

Examples

- ANS0RXBurnXXXXXXXXXXXXXXXXXXXXXXWUo9FV (addr)
- ANS17f000001 (ip)

### Extra metadata
When creating an asset, the user has the option to add both an IPFS hash or ANS data together. 
The IPFS hash can link to extra metadata related to the ANS data, such as an address for another cryptocurrency, social media handle, etc.
The IPFS data can be a JSON file with a special identifier, although this identifier will not be standardized by this AIP. 
It is recommended to use something like *"hasANS"* or *"isANS"* for external services to easily find extra ANS metadata.

## RPC
It it proposed to create helper RPC methods for encoding and decoding ANS IDs.

### ansdecode
This RPC method will decode an ANS ID given the ID passed as a string.

### ansencode
This RPC method will encode and generate an ANS ID given the ANS type and raw data as a string.
The rawData will be checked based on the given type. The RPC method should convert the type string into a proper type hex as defined above.

### getansdata
This RPC method will return ANS data *(if it exists)* based on the given asset name.

Furthermore, the "getassetdata" RPC method will be updated to include infomation about ANS. If an asset contains ANS data attached then the RPC method should be state the
asset has ANS data (hasANS) and give the raw ANS ID (ans_id). Using the ANS ID the RPC method should also append ANS info based on the type. 
For example: if an asset contains ANS data that links to an Avian address, then the RPC method should return this info for use by external programs.

## QT UI
The QT UI should be updated to allow the user to attach ANS data when creating or reissuing an asset. 
There will be a drop-down box allowing the user to choose the ANS type (ex: addeess, IP) and a input box to input ANS data based on the selected type.
The input box will be type-checked with strict requirements.

When reissuing an asset, the UI should allow the user to change ANS data.

## Backwards Compatibility

This AIP is a *consensus* change since it will change the asset database and render all current asset data incompatibile. 
This will cause all blocks with asset data to become invalid and lead to consensus split and a possible rollback.
**However,** this will not affect the Avian mainnet since assets are not active *(as of writing)* and should not cause any hardfork/rollback once assets do go live.

!!! note "Update"
    Avian 4.1.0 was successfully performed without issues regrading ANS (disabled in mainnet)

## Electrum wallet
It can be optional to implement into the Electrum wallet *(given that these changes do not affect the current wallet).*

## Diagram
<img src="https://aviannetwork.github.io/avian-docs/assets/img/ans.png" />

## Copyright/public domain
This document is hereby placed in the public domain. 
