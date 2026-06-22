# SecureDoc Chain — Hackathon Prototype

A simple, high-impact prototype for **Secure Document Sharing**.

## What it demonstrates

- AES-compatible authenticated encryption through Fernet
- SHA-256 document fingerprints
- Off-chain encrypted file storage
- Blockchain-style chained audit ledger
- Owner-controlled grant and revoke permissions
- Secure recipient access
- Independent authenticity verification
- Live tampering attack simulation
- Downloadable immutable-style audit evidence

## Quick start

1. Install Python 3.10 or newer.
2. Open a terminal in this folder.
3. Run:

```bash
pip install -r requirements.txt
streamlit run app.py
```

4. Open the local address shown by Streamlit, normally:
   `http://localhost:8501`

## Best 4-minute judge demonstration

1. Act as **Cryptographiccollective**.
2. Upload a PDF or text file and click **Encrypt and register**.
3. Open **Share Access** and grant access to **Team4**.
4. Change the sidebar identity to **Team4**.
5. Open the shared document and show successful verification/decryption.
6. Switch back to **Cryptographiccollective**, open **Threat Simulation**, and tamper with the encrypted file.
7. Switch to **Team4** and try opening it again. The tool blocks access because the hash changed.
8. Open **Blockchain Audit** and show that every action is recorded in linked blocks.

## Architecture

```text
User Browser
    |
    v
Streamlit Application
    |-- Identity and access-control checks
    |-- SHA-256 integrity verification
    |-- Fernet authenticated encryption
    |
    +--> Encrypted off-chain vault: data/encrypted_files/
    |
    +--> Tamper-evident ledger: data/ledger.json
         Each block contains the previous block hash
```

## Important security design

The document itself is **not stored on-chain**. Only fingerprints, permissions and events are registered in the ledger. This avoids exposing confidential content and reflects a realistic blockchain document-sharing architecture.

## Prototype limitation

This offline version stores the master key locally to make the hackathon demo fast and reliable. A production system should use:

- Hardware security module or cloud key-management service
- Decentralised identity or enterprise SSO
- A deployed smart contract on a permissioned blockchain or Ethereum testnet
- IPFS/private object storage
- Multi-factor authentication
- Independent security testing and formal smart-contract review
