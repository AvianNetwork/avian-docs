---
title: Inner workings
description: Inner workings of Avian Flight Plans
---

# Inner workings

## Infographic
![afp info](https://aviannetwork.github.io/avian-docs/assets/img/image3.png)

## How was this created?
We used Lua, a scripting language, because it allowed us to embed it in C++ which means we can easily connect our RPC and other functions to it easily. Refer to Figure 6 to see how this can be implemented in a UTXO model, and Figure 7 for a local model.

## UTXO Model
![utxo](https://aviannetwork.github.io/avian-docs/assets/img/image29.png)

*Figure 5 - Infographic explaining deploying contracts and executing them.*

## Local Model
![local](https://aviannetwork.github.io/avian-docs/assets/img/image30.png)

*Figure 6 shows the data-dir folder containing a new folder called “flight plans” to store the contracts.*
