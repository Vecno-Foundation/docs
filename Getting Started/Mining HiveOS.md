# Mining HiveOS

This guide explains how to mine **Vecno** on **HiveOS** using any supported miner.  
A worked example using **vecnopool.de** (PPLNS) is included below.

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

## Step 2: Add Wallet to HiveOS

1. Open your **HiveOS** dashboard
2. Go to **Wallets** → **Add Wallet**
3. Enter:
   - **Coin**: Vecno
   - **Address**: `vecno:YOUR_WALLET_ADDRESS`
   - **Name**: Vecno (or any name you prefer)
4. Save

## Step 3: Create a Flight Sheet (General)

1. Go to **Flight Sheets**
2. Click **Create Flight Sheet**

**General Flight Sheet Layout:**

| Field       | Setting                  |
|-------------|--------------------------|
| Coin        | Vecno                    |
| Wallet      | Select your Vecno wallet |
| Pool        | Configure in miner       |
| Miner       | Custom Miner             |

## Step 4: Custom Miner Configuration (General)

Each Vecno miner requires these key settings:

- **Miner Name** — Any descriptive name (e.g. `vecno-miner`)
- **Installation URL** — Provided by the miner or pool (e.g. GitHub release archive)
- **Wallet Template** — Most stratum miners use: `%WAL%.%WORKER_NAME%`  
  (Some may only need `%WAL%` — always check miner documentation)
- **Pool** (stratum URL) or node info
- **Optional** extra arguments

## Step 5: Apply the Flight Sheet

1. Save the flight sheet
2. Go to **Workers**
3. Apply the flight sheet to your rig(s)
4. Wait 1–2 minutes for it to take effect

## Step 6: Verify Mining

- Hashrate should appear in HiveOS dashboard
- Check your worker on the pool dashboard
- Monitor the blockchain: https://vecnoscan.org/

## Example: Vecno on HiveOS using vecnopool.de (PPLNS)

This example uses **vecnopool.de** — a popular PPLNS pool with CUDA & OpenCL support.

- **Pool fee**: 3%
- **Stratum URL**: `vecnopool.de:6969`

### Custom Miner Settings (Example)

| Field                     | Value / Setting                                      |
|---------------------------|------------------------------------------------------|
| Miner Name                | vecnopool-miner                                      |
| Installation URL          | https://github.com/voodoo-vecno/vecnopool-de-miner/releases/ <br>(Use the HiveOS-compatible archive, e.g. latest `.tar.gz`) |
| Hash Algorithm            | vecno (leave blank if not selectable)                |
| Wallet & Worker Template  | `%WAL%.%WORKER_NAME%`                                |
| Pool URL                  | `vecnopool.de:6969`                                  |
| Pass                      | `x`                                                  |
| Extra Config Arguments    | (optional – usually leave empty)                     |

### Apply & Mine

1. Save the flight sheet
2. Apply it to your worker
3. Wait 60–90 seconds

### Verify on Pool

1. Visit: https://vecnopool.de/
2. Search for:
   - Your wallet address
   - Your worker name

You should see:
- Hashrate
- Shares submitted
- PPLNS payouts (may take time to appear)

**Important Notes**
- PPLNS rewards are based on shares over time — variance is normal
- Do **not** pool hop (it hurts your expected rewards)
- First payouts may take several minutes/hours depending on hashrate & luck

## Useful Links

- Explorer: https://vecnoscan.org/
- Paper Wallet: https://paperwallet.vecnoscan.org/
- Desktop Wallet: https://github.com/Vecno-Foundation/vecno-desktop-wallet
- Discord: https://discord.gg/Vm7rc49cWm
- Official Vecno Miner: https://github.com/Vecno-Foundation/vecno-miner


Happy mining!  
