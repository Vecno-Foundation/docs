# Mining Vecno on Linux

This guide explains how to mine **Vecno** on **Linux** using the official miner (or compatible alternatives). There is **no official pool** — only community-run (unofficial) pools are available.

**Key Notes**:
- The official miner supports **NVIDIA GPUs** (via CUDA plugins), **AMD GPUs** (via OpenCL plugins), and optional CPU mining.
- All pools listed below are community-operated.
- Most modern Linux distributions (Ubuntu, Debian, Fedora, Arch, etc.) work well.
- Make sure you have the appropriate GPU drivers installed:
  - NVIDIA → proprietary drivers + CUDA toolkit
  - AMD → open-source amdgpu + ROCm (for newer cards)

## Step 1: Create a Vecno Wallet

You **must** have a Vecno wallet before mining.

### Option A: Vecno Paper Wallet (Fastest / Beginner-Friendly)

1. Visit: https://paperwallet.vecnoscan.org/
2. Generate a new wallet
3. Carefully save:
   - Wallet address (`vecno:...`)
   - Private key (mnemonic / seed phrase)

**Important:**  
Store the private key/mnemonic completely offline and securely (encrypted USB, paper in safe, metal backup, etc.).  
If you lose it, your mined funds are permanently lost.

**Ideal for:** mining payouts, cold storage, quick setup

### Option B: Vecno Desktop Wallet (Recommended for Long-Term Use)

1. Download the latest release from:  
   https://github.com/Vecno-Foundation/vecno-desktop-wallet/releases  
   (choose Linux `.AppImage`, `.deb`, `.rpm`)
2. Example for AppImage:

   ```bash
   chmod +x Vecno Wallet*.AppImage
   ./Vecno Wallet*.AppImage
   ```

Great for: 
Full interface, balance tracking, sending/receiving, long-term holding.
After setup, copy your wallet address (vecno:...) - you will use it for mining.

## Step 2: Download and Extract the MinerGo to the official releases page:
https://github.com/Vecno-Foundation/vecno-miner/releases
Download the latest Linux GPU bundle
(usually named something like vecno-miner-vX.Y.Z-GPU-linux-bundle.tar.gz)
Extract it:

```bash
mkdir vecno-miner
cd vecno-miner
wget https://github.com/Vecno-Foundation/vecno-miner/releases/download/v0.0.5/vecno-miner-v0.0.5-GPU-linux-bundle.tar.gz
tar -xzf vecno-miner-*.tar.gz
```
You should now have:

- vecno-miner (the main executable)

- plugin files: libvecnocuda.so, libvecnoopencl.so, etc.

Alternative: Build from source (if no suitable binary or you want the latest)

## Step 3: Pool Mining (Recommended)

Pool mining gives you consistent (smaller) rewards instead of waiting to solo-mine a full block.

Create a Mining Shell Script In your miner folder (~/vecno-miner)
```bash
nano start_mining.sh
```

Paste one of the examples below (adjust for your pool)
Save and exit (Ctrl+O → Enter → Ctrl+X)

Make executable
```bash
chmod +x start_mining.sh
```

Start mining
```bash
./start_mining.sh
```


### Example start_mining.sh 

vecnopool.de example

```bash
./vecno-miner \
  --mining-address "vecno:YOUR_WALLET_ADDRESS_HERE" \
  --stratum-server vecnopool.de \
  --stratum-port 6969 \
  --stratum-worker "yourworkername" \
  --stratum-password "x"
```

NinjaPool PPLNS example (check current details on site)

```bash
./vecno-miner \
  --mining-address "vecno:YOUR_WALLET_ADDRESS_HERE" \
  --stratum-server ninjaraider.com \
  --stratum-port 44700 \
  --stratum-worker "yourworkername" \
  --stratum-password "x"
```

Always visit the pool website for the current stratum server, port, worker format, and password.
Replace YOUR_WALLET_ADDRESS_HERE with your real vecno:... address.

Enable CPU Mining (Optional)
Add --threads (adjust to number of logical cores you want to use):bash

```bash
--threads 12
```

Example:

```bash
./vecno-miner \
  --mining-address "vecno:YOUR_WALLET_ADDRESS_HERE" \
  --stratum-server vecnopool.de \
  --stratum-port 6969 \
  --stratum-worker "yourworkername" \
  --stratum-password "x" \
  --threads 12
```

### Community Pools

| Pool              | Fee   | Notes                                                                 | Website                                      |
|-------------------|-------|-----------------------------------------------------------------------|----------------------------------------------|
| vecnopool.de      | 3%    | CUDA/OpenCL optimized – custom miner only                             | https://vecnopool.de                         |
| NinjaPool PPLNS   | 2%    | Community PPLNS pool                                                  | https://ninjaraider.com/vecno                |
| NinjaPool Solo    | 2.5%  | Community solo pool                                                   | https://ninjaraider.com/vecno-solo           |

Always visit the pool website for the **latest stratum URL, port, and instructions**.

### Common Optional GPU Settings

Add these flags to your batch file line if needed:

| Option                          | Example Flag                       | Description                                      |
|---------------------------------|------------------------------------|--------------------------------------------------|
| Disable NVIDIA CUDA             | `--cuda-disable`                   | Force OpenCL only (useful for AMD-only rigs)     |
| Adjust CUDA workload            | `--cuda-workload 256`              | Performance tuning (NVIDIA)                      |
| Disable AMD OPENCL              | `--opencl-amd-disable`             | Force CUDA only (useful for NVIDIA-only rigs)    |
| Adjust OPENCL workload          | `--opencl-workload 256`            | Performance tuning (AMD)                         |

## Step 4: Solo Mining (Advanced / High Hashrate Needed)

Solo mining means you only get paid if you find a full block yourself.

1. Run a Full Vecno Node

Download latest vecnod release
```bash
wget https://github.com/Vecno-Foundation/vecnod/releases/download/v1.0.0/vecnod-v1.0.0-linux.tar.gz
tar -xzf vecnod-*.tar.gz
cd vecnod-*
./vecnod
```
Wait for full blockchain sync (can take some minutes depending on connection).

2. Create solo mining script (start_solo.sh)

```bash
./vecno-miner \
  --mining-address "vecno:YOUR_WALLET_ADDRESS_HERE" \
  --port 7110 \
  # --threads 12   # optional CPU mining
```


```bash
chmod +x start_solo.sh
./start_solo.sh
```

## Step 5: Verify & Monitor Mining

Watch the terminal output for:
Hashrate (MH/s, GH/s, etc.)

Accepted / rejected shares

Check your pool dashboard (usually enter wallet address or worker name)

Monitor blockchain: https://vecnoscan.org/

### Useful Links
- Blockchain Explorer: https://vecnoscan.org/
- Paper Wallet: https://paperwallet.vecnoscan.org/
- Desktop Wallet: https://github.com/Vecno-Foundation/vecno-desktop-wallet
- Official Miner: https://github.com/Vecno-Foundation/vecno-miner
- Vecno Discord: https://discord.gg/Vm7rc49cWm

Happy mining!