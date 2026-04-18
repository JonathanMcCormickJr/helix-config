# helix-config 🧬

My personal Helix IDE [config](./config.toml). 

For an introduction to the Helix IDE, please see the [Helix website](https://helix-editor.com/) and consider practicing with daily keystroke-efficient drills using [Keyglide](https://keygli.de/). 

## Setup (on Ubuntu)

1. Install C build tools and common Rust dependencies:
    ```bash
    sudo apt update
    sudo apt install build-essential curl pkg-config libssl-dev
    ```
2. Install the Rust toolchain via Rustup:
    ```bash
    curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
    ```
3. Install essential Rust components:
    ```bash
    rustup component add rust-analyzer rustfmt clippy
    ```
4. Install LLDB for DAP (in-editor debugging support):
    ```bash
    sudo apt install lldb
    ```
    Helix uses `lldb-dap` (included with LLDB) as its default Rust debug adapter. On Ubuntu the binary is sometimes installed with a version suffix (e.g. `lldb-dap-18`). If `hx --health rust` reports the debugger as unavailable, create an unversioned symlink:
    ```bash
    # Replace 18 with the version installed on your system
    sudo ln -s /usr/bin/lldb-dap-18 /usr/local/bin/lldb-dap
    ```
5. Install Helix (https://docs.helix-editor.com/package-managers.html#ubuntudebian):
    ```bash
    sudo add-apt-repository ppa:maveonair/helix-editor
    sudo apt update
    sudo apt install helix
    ```
6. Copy the editor config from this repo into `~/.config/helix/`:
    ```bash
    mkdir -p ~/.config/helix
    cp config.toml ~/.config/helix/config.toml
    cp languages.toml ~/.config/helix/languages.toml
    cp ignore ~/.config/helix/ignore
    ```
7. Verify that Helix can see `rust-analyzer` and all grammars:
   ```bash
   hx --health rust
   ```
8. Start Helix and enjoy!
    ```bash
    hx .
    ```

## Optional productivity tools

- **[Zellij](https://zellij.dev/) or [tmux](https://github.com/tmux/tmux/wiki)** — Helix has no built-in terminal, so a terminal multiplexer is strongly recommended for running `cargo build`/`cargo test` in a split pane alongside the editor.
    - ```bash
      cargo install --locked zellij
      rustup update
      zellij
      ```
- **[Alacritty](https://alacritty.org/)** — a terminal with support for copy-pasting in a compatible way with Zellij. i.e. run `alacritty` instead of Bash.
    - ```bash
      cargo install alacritty
      ``` 
- **[cargo-nextest](https://nexte.st/)** — A faster, more ergonomic test runner (`cargo install cargo-nextest`).
    - ```bash
      cargo binstall cargo-nextest --secure
      ```
    - And if you have a library crate:
      ```bash
      cargo nextest run && cargo test --doc
      ```
- **[direnv](https://direnv.net/)** — Per-project environment variable management, useful for custom `RUSTFLAGS`, feature flags, or toolchain overrides via `.envrc` files (`sudo apt install direnv`).
