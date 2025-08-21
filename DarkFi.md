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

to be added


