# Vecno Documentation

Vecno is a blockchain platform designed to overcome the limitations of existing consensus mechanisms by using Proof of History (PoH), blockDAGs, and an optimized consensus structure. In certain cases, Vecno will also rely on Proof of Work (PoW) to validate transactions, ensuring maximum security and integrity. This unique combination introduces a high-performance, low-energy system that maintains decentralization while offering scalability, speed, and security. This innovative approach challenges the dominance of Proof of Work and Proof of Stake models by providing a more efficient alternative for real-time transaction validation.

The MemHash algorithm is a custom Proof-of-Work mechanism designed specifically for the Vecno blockchain. Its goal is to secure the network in a way that is fair, energy-efficient in context, and resistant to domination by specialized hardware (like ASICs). This promotes true decentralization by allowing anyone with a standard CPU or GPU to participate in mining effectively. 

MemHash is built on top of BLAKE3, one of the fastest and most secure cryptographic hash functions available today. BLAKE3 is much quicker than older functions like SHA-256 (used in Bitcoin) or Keccak (used in old Ethereum), while providing strong protection against attacks.
To make the algorithm memory-hard, MemHash adds layers that require accessing a moderate amount of memory in an unpredictable way. This slows down specialized hardware (which excels at pure computation) but doesn't heavily impact regular computers. The result is a balanced PoW that encourages broad participation.


To connect with the Vecno community, join the Discord [here](https://discord.gg/Vm7rc49cWm).

[![Join the Vecno Discord Server](https://img.shields.io/discord/1180853066090692638.svg?label=&logo=discord&logoColor=ffffff)](https://discord.gg/Vm7rc49cWm)


## Table of Contents

1. [Getting Started](Getting%20Started/README.md)
   * [Full Node Installation](Getting%20Started/Full%20Node%20Installation%20Guide.md)
   * [Extending RpcApi](Getting%20Started/Extending%20RpcApi.md)
   * [Vecno WASM SDK](Getting%20Started/Vecno%20WASM%20SDK.md)
   * [Mining Windows](Getting%20Started/Mining%20Windows.md)
   * [Mining Linux](Getting%20Started/Mining%20Linux.md)
   * [Mining HiveOS](Getting%20Started/Mining%20HiveOS.md)
2. [dApps](dApps/README.md)
   * [Vecno Paper Wallet](dApps/Vecno%20Paper%20Wallet.md)
   * [Windows Desktop Wallet](dApps/Vecno%20Desktop%20Wallet.md)
3. [About Vecno](About%20Vecno/README.md)
   * [Vision](About%20Vecno/Vision.md)
   * [Founders](About%20Vecno/Founders.md)