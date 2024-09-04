# Fleek-network
### Prerequisites

1. **Server Requirements**:
   - **OS**: Ubuntu 22.04 LTS or Debian 11 (64-bit only).
   - **CPU**: Minimum of 4 cores with 2.0 GHz speed, x86_64 architecture.
   - **RAM**: At least 32 GB.
   - **Disk Space**: Minimum 20 GB.
   - **Intel SGX Support**: Required for trusted computing functionalities.

2. **Network Ports**:
   - Ensure the following port ranges are open:
     - TCP: `4200-4299`
     - UDP: `4300-4399`

### Installation Steps

1. **Install Dependencies**:
   Install the necessary build tools and dependencies:
   ```bash
   sudo apt-get install build-essential clang pkg-config libssl-dev gcc-multilib protobuf-compiler
   ```

2. **Install Rust**:
   Fleek Network is built with Rust, so you need to install it if you haven't already:
   ```bash
   curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
   source $HOME/.cargo/env
   ```

3. **Clone the Fleek Network Repository**:
   Clone the source code from the Fleek Network GitHub repository:
   ```bash
   git clone -b testnet-alpha-1 https://github.com/fleek-network/lightning.git ~/fleek-network/lightning
   cd ~/fleek-network/lightning
   ```

4. **Build the Node**:
   Navigate to the project directory and build the node binary:
   ```bash
   cargo clean
   cargo update
   cargo +stable install --locked --path core/cli --features services
   ```

5. **Create a Symbolic Link**:
   To simplify access to the node binary, create a symbolic link:
   ```bash
   sudo ln -s "~/.cargo/bin/lightning-node" /usr/local/bin/lgtn
   ```

6. **Verify Installation**:
   Check if the binary is correctly installed by running:
   ```bash
   lgtn --version
   ```

### Running the Validator Node

1. **Opt-in to Network Participation**:
   Before running the node, opt-in to participate in the network:
   ```bash
   lgtn opt in
   ```

2. **Start the Node**:
   Launch the node by executing:
   ```bash
   lgtn run
   ```

### Monitoring and Maintenance

- **Systemd Service**: It’s recommended to set up the node as a `systemd` service for easier management. This ensures the node restarts automatically if it fails and starts on boot.

- **Health Checks and Logs**: Regularly check the health of your node and monitor logs to ensure everything is running smoothly.
