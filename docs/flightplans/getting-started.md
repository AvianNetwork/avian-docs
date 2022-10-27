---
title: Getting Started
---

# Getting Started

## GUI Method

### First time install

!!! note
    v4.0 or above is required to run flight plans.

1. Install the latest Avian wallet here: [Latest Avian wallet ↗](https://github.com/AvianNetwork/Avian/releases)
2. Extract the ZIP

### Enable Flightplans

#### Windows

You can either create a shortcut or run it from Command Prompt.

=== "Create shortcut"

    1. Go to the folder that contains `avian-qt.exe`
    2. ++rbutton++ on `avian-qt.exe`
    3. Click on `Create shortcut`
    4. Go to newly added shortcut location
    5. ++rbutton++ on shortcut
    6. Click on `Properties`
    7. Find `Execute` and click on it
    8. Add `-flightplans` to the end of the input box.

=== "Command Prompt"

    1. Go to the folder that contains `avian-qt.exe`
    2. ++shift+rbutton++
    3. Click on `Open in Command Prompt`
    4. Type: `avian-qt.exe -flightplans`
    5. Avian wallet should open.

#### Linux or macOS

You can run Avian from the terminal to enable flight plans.

=== "Run from terminal"

    1. Using `cd` go to the folder that contains `avian-qt`
    2. Type:
    ```bash
    chmod +x avian-qt
    ./avian-qt -flightplans
    ```

### Creating the "flightplans" folder

If you used a custom datadir, then go to it.

If you used the default datadir, then it should be in the folder stated below:

#### Windows
```C:\Users\<Username>\AppData\Roaming\Avian```
    
#### macOS
```~/Library/Application Support/Avian```
    
#### Unix
```~/.avian```

Once you have opened this folder, create a new folder called `flightplans` in it.

![flightplans](https://aviannetwork.github.io/avian-docs/assets/img/image30.png)

Go inside this folder, and create a new file with any name you want. Make sure it ends in `.lua`

For this example, let's make a new file called `test.lua`

### Write flightplan code in new file

Refer to other pages to learn how to write flightplan code.

For this example, we will make code that returns `Hello, World!`

Code is shown below:
```lua
function hello_world ()
    return "Hello, World!"
end
```

### Run flightplan from wallet

First, open your wallet with flightplans enabled (shortcut or via terminal)

Go to Help -> Debug -> Console

To run the function `hello_world` in the file called `test.lua`, type the following command:
```
call_function test hello_world
```

The format of the RPC call is below:
```
call_function <file name> <function name> <args>
```

## Links

### [Examples ↗](../examples)

### [Inner workings ↗](../inner-workings)

### [Avian Lib ↗](../avian-library)

### [Web3 Lib ↗](../web3-library)
