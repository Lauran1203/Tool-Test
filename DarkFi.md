DarkFi is an anonymous digital market. 

DarkFi gives install instruction on their website:https://darkrenaissance.github.io/darkfi/index.html


My device is Mac, so here are steps to intall DarkFi on macOS:

# Step 1: Run a Node 

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



# Step 2: Use Dark Wallet

to be added


