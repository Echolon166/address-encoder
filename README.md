# address-encoder
This typescript library encodes and decodes address formats for various cryptocurrencies.

Text-format addresses are decoded into their native binary representations, and vice-versa. In the case of Bitcoin-derived chains, this means their scriptPubKey; for Ethereum-derived chains this is their hash.

This library was written for use with [EIP 2304](https://eips.ethereum.org/EIPS/eip-2304), but may be useful for anyone looking for a general purpose cryptocurrency address codec.

## Installation

### Using NPM

```
npm install --save @ensdomains/address-encoder
```

## Usage

```
import { formatsByName, formatsByCoinType } from '@ensdomains/address-encoder';

const data = formatsByName['BTC'].decoder('1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa');
console.log(data.toString('hex')); // 76a91462e907b15cbf27d5425399ebf6f0fb50ebb88f1888ac
const addr = formatsByCoinType[0].encoder(data);
console.log(addr); // 1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa
```

## Supported cryptocurrencies

This library currently supports the following cryptocurrencies and address formats (ordered alphabetically):

 - ADA (bech32)
 - ALGO (checksummed-base32)
 - ARK (base58check)
 - ATOM (bech32)
 - BCH (base58check and cashAddr; decodes to cashAddr)
 - BNB (bech32)
 - BTC (base58check P2PKH and P2SH, and bech32 segwit)
 - CELO (checksummed-hex)
 - DASH (base58check P2PKH and P2SH)
 - DCR (base58, no check)
 - DOGE (base58check P2PKH and P2SH)
 - DOT (ss58)
 - EGLD (bech32)
 - EOS
 - ETC (checksummed-hex)
 - ETH (checksummed-hex)
 - HBAR
 - HIVE (base58+ripemd160-checksum)
 - HNS
 - ICX
 - KSM (ss58)
 - LTC (base58check P2PHK and P2SH, and bech32 segwit)
 - MONA (base58check P2PKH and P2SH, and bech32 segwit)
 - NEM (base32)
 - NEO (base58check)
 - ONT (base58check)
 - PPC (base58check P2PKH and P2SH)
 - QTUM (base58check)
 - RSK (checksummed-hex)
 - SOL (base58check)
 - STEEM (base58+ripemd160-checksum)
 - TRX (base58check)
 - VET (checksummed-hex)
 - XDAI (checksummed-hex)
 - XLM (ed25519 public key)
 - XRP (base58check-ripple)
 - XTZ (base58check)
 - ZEC (transparent addresses: base58check P2PKH and P2SH, and Sapling shielded payment addresses: bech32; doesn't support Sprout shielded payment addresses)
 - ZIL (bech32)

PRs to add additional chains and address types are welcome.
