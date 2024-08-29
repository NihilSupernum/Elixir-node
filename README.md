# Elixir-node
Here’s how to set up and run a node in the Elixir project:

### 1. **System Preparation**
Ensure your system meets the following minimum requirements:
- **RAM**: 4 GB
- **Disk**: 30 GB (minimum)
- **CPU**: 1 core
- **Network Connection**: Stable with 100 Mbps bandwidth

### 2. **Install Docker**
Install Docker on your server. You can find installation instructions on the [official Docker website](https://docs.docker.com/get-docker/). After installation, verify it with the command:
```bash
docker ps
```

### 3. **Create a Wallet**
Create a new wallet specifically for running the Elixir node. This can be done using MetaMask, for instance. Copy the wallet address and private key for later use.

### 4. **Download and Configure the Dockerfile**
Download the [Dockerfile for the validator](https://files.elixir.finance) and open it in a text editor. Enter your wallet address and private key, and also set a name for your validator.

### 5. **Build the Docker Image**
Build the validator image using the following command:
```bash
docker build . -f Dockerfile -t elixir-validator
```

### 6. **Start the Validator**
Start the validator with the command:
```bash
docker run -it --name ev elixir-validator
```
To ensure the validator automatically restarts on server reboot, use:
```bash
docker run -d --restart unless-stopped --name ev elixir-validator
```

### 7. **Update the Validator**
To update and get the latest version of the validator, periodically execute the following commands:
```bash
docker kill ev
docker rm ev
docker pull elixirprotocol/validator:testnet-2
docker build . -f Dockerfile -t elixir-validator
```
Then restart the validator.
