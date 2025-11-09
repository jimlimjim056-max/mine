# ashdaemon

Follow these commands to install Rust, prepare tooling, and create the ashdaemon project.

```bash
# 1) Install Rust (Linux/macOS)
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y
# Load cargo into current shell
source "$HOME/.cargo/env"
rustup update stable
rustup component add clippy rustfmt

# 2) Install useful cargo tools
cargo install cargo-edit


# 5) Add common dependencies (adjust as needed)
cargo add ash winit env_logger log

# 6) Build to verify setup (debug)
cargo build


## Build (release) and run

- Build optimized release binary (Linux devcontainer):

# from project root (/workspaces/mine)
cargo clean
cargo build --release

# binary is at:
ls -l target/release/ashdaemon

# run it:
./target/release/ashdaemon --mode native
# if "permission denied":
chmod +x target/release/ashdaemon
./target/release/ashdaemon --mode native
```

- Install binary into your Cargo bin (~/.cargo/bin):
```bash
cargo install --path .
# then run:
ashdaemon --mode native
```


Notes:
- If Cargo.toml uses a local path dependency (ashmaize = { path = "./ce-ashmaize" }), ensure ./ce-ashmaize exists and contains a Cargo.toml. To use the git crate instead, update Cargo.toml:
```toml
# replace local path with git
ashmaize = { git = "https://github.com/input-output-hk/ce-ashmaize" }
```

## Python environment (for scripts or tools)

Add a lightweight Python virtual environment and install requests + rich:

```bash
# from project root (/workspaces/mine)

# 1) create and activate venv
python3 -m venv .venv
source .venv/bin/activate

# 2) upgrade pip and install packages
pip install --upgrade pip
pip install requests rich

# 3) optionally record dependencies
pip freeze > requirements.txt

# 4) when done
deactivate
```

#chưadđươc thì tìm.vscode/ettingjson
{
  "python.defaultInterpreterPath": ".venv/bin/python",
  "python.terminal.activateEnvironment": true
}


/tmp/cargo-target/release/ashdaemon --mode native