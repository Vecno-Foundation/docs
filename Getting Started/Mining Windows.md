# Mining Windows

This guide explains how to mine **Vecno** on **Windows** using the official miner. There is **no official pool** - only community-run (unofficial) pools are available.

**Key Notes**:
- The official miner supports **NVIDIA GPUs** (CUDA), **AMD GPUs** (OpenCL), and optional CPU mining.
- All pools listed below are community-operated.

## Step 1: Create a Vecno Wallet

You **must** create a Vecno wallet before mining.

### Option A: Vecno Paper Wallet (Fastest / Beginner-Friendly)

1. Visit: https://paperwallet.vecnoscan.org/
2. Generate a new wallet
3. Save both:
   - Wallet address (`vecno:...`)
   - Private key (mnemonic)

**Important:** Store the private key offline and securely. If you lose it, your funds are permanently lost.

**Ideal for:**
- Mining
- Cold storage
- Quick setup

### Option B: Vecno Desktop Wallet (Recommended for Long-Term Use)

1. Download the official desktop wallet:  
   https://github.com/Vecno-Foundation/vecno-desktop-wallet
2. Set it up and connect with the network

**Great for:**
- Full wallet interface
- Easier balance tracking
- Sending/receiving Vecno
- Long-term holding

After setup, copy your wallet address for mining.

## Step 2: Download and Extract the Miner

1. Go to the official releases page:  
   https://github.com/Vecno-Foundation/vecno-miner/releases
2. Download the latest Windows release (usually a `.zip` file containing `vecno-miner.exe` and required DLLs)
3. Extract the contents to a folder of your choice (e.g., `C:\vecno-miner`)

**Tip:** You will create a batch file in this folder to start mining easily.

## Step 3: Pool Mining (Recommended)

Pool mining is the easiest way to earn consistent rewards.  
Use one of the community pools below.

### Create a Mining Batch File

1. In your miner folder (e.g., `C:\vecno-miner`), right-click → **New** → **Text Document**
2. Name it `start_mining.bat` (ensure it ends with `.bat`, not `.txt`)
3. Right-click the file → **Edit** (or open with Notepad)
4. Paste the configuration for your chosen pool (examples below)
5. Save and close
6. Double-click `start_mining.bat` to start mining

### Example Configurations for start_mining.bat

#### vecnopool.de (example)

@echo off
cmd /k "./vecno-miner --mining-address "vecno:YOUR_WALLET_ADDRESS_HERE" --stratum-server vecnopool.de --stratum-port 6969 --stratum-worker worker1"


**Important:**
- Replace `vecno:YOUR_WALLET_ADDRESS_HERE` with your actual wallet address.
- Replace worker/password and stratum details with the current values from the pool's website.
- Most pools use password `x` (or leave blank).
- This automatically uses all available GPUs (NVIDIA via CUDA, AMD via OpenCL).

### Enable CPU Mining (Optional)

Add `--threads 8` (or your preferred number) to any of the lines above:

Example:

./vecno-miner --mining-address "vecno:YOUR_WALLET_ADDRESS_HERE" --stratum-server vecnopool.de --stratum-port 6969 --stratum-worker worker1 --threads 8

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

## Step 4: Solo Mining

Solo mining lets you keep full block rewards (if you find a block), but requires a fully synced node and high hashrate.

### Set Up a Vecno Node

1. Download the latest node from:  
   https://github.com/Vecno-Foundation/vecnod/releases
2. Extract and run `vecnod.exe`
3. Wait for full synchronization (check logs)

### Create a Solo Mining Batch File

Create a `.bat` file (e.g., `start_solo.bat`) with:

@echo off
cmd /k "./vecno-miner --mining-address "vecno:YOUR_WALLET_ADDRESS_HERE" --port 7110"


- Add `--threads 8` for CPU mining if desired.
- Double-click to start once the node is fully synced.

## Step 5: Verify Mining

- Watch the miner window for hashrate and accepted shares
- Check the pool dashboard (by wallet address or worker name)
- Monitor the blockchain: https://vecnoscan.org/

## Useful Links

- Blockchain Explorer: https://vecnoscan.org/
- Paper Wallet: https://paperwallet.vecnoscan.org/
- Desktop Wallet: https://github.com/Vecno-Foundation/vecno-desktop-wallet
- Official Miner: https://github.com/Vecno-Foundation/vecno-miner
- Vecno Discord: https://discord.gg/Vm7rc49cWm

Happy mining!
