# helix-config 🧬

My personal Helix IDE [config](./config.toml). 

For an introduction to the Helix IDE, please see the [Helix website](https://helix-editor.com/) and consider practicing with daily keystroke-efficient drills using [Keyglide](https://keygli.de/). 

## Setup (on Ubuntu)

1. Install the Rust toolchain via Rustup: `curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh`.
2. Install `rust-analyzer` (https://rust-analyzer.github.io/book/rust_analyzer_binary.html): `rustup component add rust-analyzer`.
3. Install Helix (https://docs.helix-editor.com/package-managers.html#ubuntudebian):
    ```bash
    sudo add-apt-repository ppa:maveonair/helix-editor
    sudo apt update
    sudo apt install helix
    ```
4. Copy the contents of [config.toml](./config.toml) from this repo into `~/.config/helix/config.toml`.
5. Start Helix and enjoy! `hx .`
