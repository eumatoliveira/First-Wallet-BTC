# Bitcoin Wallet Generator with Node.js

## 🚀 Overview
A secure Bitcoin wallet generator implemented in Node.js that creates HD (Hierarchical Deterministic) wallets following the BIP44 standard. This project demonstrates the fundamental concepts of Bitcoin wallet creation, including mnemonic phrases, seed generation, and address derivation.

## ⚡ Features
- Generate secure mnemonic seed phrases (BIP39)
- Create HD wallets (BIP32)
- Derive Bitcoin addresses using BIP44 path
- Generate private keys in WIF format
- Mainnet Bitcoin address generation

## 🛠️ Technologies Used
- Node.js
- bitcoinjs-lib
- bip32
- bip39
- ecpair

## 📋 Prerequisites
```bash
node --version  # v12 or higher
npm --version   # Latest version recommended
```

## 🔧 Installation

1. Clone the repository:
```bash
git clone https://github.com/eumatoliveira/First-Blockchain-Wallet-with-Nodejs-JS.git
```

2. Install dependencies:
```bash
npm install bitcoinjs-lib bip32 bip39 ecpair
```

## 💻 Usage

Run the wallet generator:
```bash
node src/createWallet.js
```

## 📝 Code Example

```javascript
const bitcoin = require('bitcoinjs-lib');
const bip32 = require('bip32');
const bip39 = require('bip39');

async function createWallet() {
    try {
        const mnemonic = bip39.generateMnemonic();
        const seed = await bip39.mnemonicToSeed(mnemonic);
        const root = bip32.fromSeed(seed);
        const path = "m/44'/0'/0'/0/0";
        const child = root.derivePath(path);
        
        const { address } = bitcoin.payments.p2pkh({
            pubkey: child.publicKey,
            network: bitcoin.networks.bitcoin
        });

        console.log('Seed Phrase:', mnemonic);
        console.log('Bitcoin Address:', address);
        console.log('Private Key (WIF):', child.toWIF());
    } catch (error) {
        console.error('Wallet creation error:', error);
    }
}
```

## 🔐 Security Considerations

⚠️ **IMPORTANT WARNINGS:**
1. Never share your seed phrase or private keys
2. Store your seed phrase securely
3. This is a demonstration project - use at your own risk
4. For real transactions, consider using established wallet solutions

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📜 License

This project is licensed under the MIT License.

## 👤 Author

Matheus Oliveira
- GitHub: [@eumatoliveira](https://github.com/eumatoliveira)

---
⚡ **Note**: Always practice safe key management and backup procedures when dealing with cryptocurrency wallets!
