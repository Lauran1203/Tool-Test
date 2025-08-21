DarkFi is an anonymous digital market. 

DarkFi gives install instruction on their website:https://darkrenaissance.github.io/darkfi/index.html


My device is Mac, so here are steps to intall DarkFi on macOS:


# Feature 1: Run a Node 

### 1. Install Rust

Open the terminal and run:

```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

After the installation is complete, restart your terminal.

---

### 2. Install Dependencies

On macOS, it’s recommended to use **Homebrew** to install dependencies.

If you don’t have Homebrew installed yet, run:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Then install the build tools and libraries:

```bash
brew install cmake pkg-config openssl
```

---

### 3. Get the DarkFi Source Code

```bash
git clone https://github.com/darkrenaissance/darkfi.git
cd darkfi
```

---

### 4. Build DarkFi

```bash
cargo build --release
```

---

### 5. Run the Node

After building, the main executable is located in `target/release/`.

Start the main daemon:

```bash
./target/release/darkfid
```

Then it's all set!

<img width="1136" height="742" alt="image" src="https://github.com/user-attachments/assets/d1b362d6-982c-4953-b3a8-5fda6027be0f" />


### 6.Closing the Terminal Will Stop the Node Process

**Details:**

* When a blockchain node (e.g., `darkfid`) is running in the terminal, closing the terminal window or disconnecting will terminate the process.
* The node will no longer participate in network synchronization, consensus, or continue processing blocks or contracts.

---

#### Running the Node in the Background

To keep the node running after closing the terminal, the following methods can be used:

**Using `nohup`**

   * Runs the node in the background, with logs output to the `darkfid.log` file.

**Using `screen` or `tmux`**

   * Install `screen` or `tmux`.
   * Start a `screen` or `tmux` session.
   * Detaching (e.g., `Ctrl+A D` in `screen`) allows the process to continue running in the background even if the terminal is closed.


### 7. Rerun a node 

If `darkfid` is already in `/usr/local/bin`, it can be run directly from the terminal by entering `darkfid`.

### Steps to run the node:

1. Open the terminal.
2. Enter:

   ```bash
   darkfid
   ```
3. Press Enter to start the node.

There is no need to enter the full path or navigate to the folder. As long as `darkfid` is in `/usr/local/bin`, the command can be run directly at any time, making it very convenient.


# Feature 2: Use Dark Wallet

For DarkFi on macOS, you do **not** need to use any cargo commands to run the wallet (`drk`) or the anonymous chat client (`darkirc`). The executables are already included in the main DarkFi project folder. Using `cargo build` or similar commands will **not** produce the required binaries and may cause confusion or errors.


Open Terminal and type:
```sh
drk
```
- If you see “command not found,” it means `drk` is not in `/usr/local/bin`. You can either run it with the full path (e.g., `~/darkfi/drk`) or copy it to `/usr/local/bin`:
  ```sh
  sudo cp /path/to/drk /usr/local/bin/
  ```
- If you get a permission error, make it executable:
  ```sh
  chmod +x /usr/local/bin/drk
  ```
- Once started, follow the prompts to manage your wallet, send/receive assets, or check your balance.

---

## Set Up a DarkFi Wallet Password and Generate a Keypair

### 1. Find and Edit the Wallet Config File

First, set a secure password for the wallet. The config file is usually at:

```
~/.config/darkfi/drk_config.toml
```

To open and edit the file, use this command in the terminal:

```bash
nano ~/.config/darkfi/drk_config.toml
```

(On Mac or Linux, nano is a simple text editor. If a permission error appears, try adding `sudo` before the command.)

---

### 2. Set a New Password

Inside the config file, look for a section like this:

```toml
[network_config."testnet"]
wallet_path = "~/.local/share/darkfi/drk/testnet/wallet.db"
wallet_pass = "changeme"
```

Change `"changeme"` to a custom password (use only English letters/numbers, and keep it between the quotes). For example:

```toml
wallet_pass = "mySuperSecretPassword123"
```

**Don’t use the word `changeme`!**

After making changes, save and exit nano:
- Press `Ctrl + O` (the letter O) to save, then hit Enter.
- Press `Ctrl + X` to exit.

---

### 3. Initialize the Wallet

Back in the terminal, run:

```bash
./drk wallet --initialize
```

This sets up the wallet for the first time. If messages about Merkle trees and contracts appear, the setup worked!

---

### 4. Generate a Keypair (Wallet Address)

Create a wallet address (keypair):

```bash
./drk wallet --keygen
```

The terminal should show something like:

```
Generating a new keypair
New address:
CbaqFqGTgn86Zh9AjUeMw3DJyVCshaPSPFtmj6Cyd5yU
```

Copy and save the new address somewhere safe. This address will be used to receive DRK coins.

---

### 5. Check the Address

To see the default wallet address, run:

```bash
./drk wallet --address
```

To set a different address as the default, use:

```bash
./drk wallet --default-address 1
```

---

**That’s it!**  
A new password is set, the wallet is initialized, and the first keypair is generated. Ready to use DarkFi.

<img width="1112" height="162" alt="image" src="https://github.com/user-attachments/assets/ab99a150-8564-4191-90cc-20e216b4198b" />

---

# Feature 3. Launch darkirc for Anonymous Chat

In Terminal, type:
```sh
darkirc
```
- If you see “command not found,” copy the file to `/usr/local/bin` or use the full path.
- If you get a permission error:
  ```sh
  chmod +x /usr/local/bin/darkirc
  ```
- Once launched, follow the on-screen instructions to join channels or configure anonymous chat.

---

### Important Note About Cargo

- Do **not** use `cargo build` or any cargo commands for these tools.  
- The project’s structure is different from typical Rust apps, and cargo will **not** produce the `drk` or `darkirc` binaries in `target/release/`.
- Just use the provided executables in your DarkFi folder. This will save you time and avoid unnecessary frustration.

---

### Summary

- As long as `drk` and `darkirc` are in `/usr/local/bin`, you can start them from any directory.
- If you encounter any errors, copy the terminal output and ask for help—a step-by-step solution can be provided.
- Skip all cargo commands for the wallet and chat client on macOS—just use the pre-built files!

