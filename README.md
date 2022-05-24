# bitcoin_reimplementation

Reimplementation of Bitcoin in Python from scratch. Lots of help from Wikipedia, Andrej Karpathy, Andrea Corbellini, and the open source community.

# Sources:

- https://bitcoin.org/bitcoin.pdf
- http://karpathy.github.io/2021/06/21/blockchain/
- https://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.180-4.pdf
- https://en.bitcoin.it/wiki/Base58Check_encoding
- https://en.bitcoin.it/wiki/Script

# Notes:

### Elliptic Curves:

![Elliptic Curve](./secp256pk.png "Elliptic Curve")

- the set of points described by the equation: y^2 = x^3 + ax + b
- symmetric about the -axis
- an approach to public-key cryptography
- can be used for encryption by combining the key agreement with a symmetric encryption scheme
- Bitcoin uses the secp256k1 curve
- Used for public and private keys in bitcoin

### Public Key:

- uses publicly known and agreed on constants
- point on the curve that results from adding the generator point to itself secret_key times
- tuple (x,y) on generator curve

### Private Key:

- "The private key is simply a random integer that satisfies 1 <= key < n (recall n is the order of G)"
- anyone who knows it can control all of the funds you own on the Bitcoin blockchain, associated with it.
- integer

### Bitcoin Wallet:

- type of digital wallet used to send and receive Bitcoins
- stores the cryptographic information used to access Bitcoin addresses and send transactions.

### Hash Functions:

- Useful in the generation and verification of digital signatures and message authentication codes, and in the generation of random numbers or bits.

### SHA256

- SHA256 processes a message to produce a condensed representation called a message digest.
- two stages: preprocessing and hash computation
- core element in Bitcoin's Proof of Work
- POW goal is to modify the block of transactions until the whole thing hashes to a sufficiently low number (when the bytes of the digest are interpreted as a number)

### SHA Algo:

- Takes bytes to be hashed
- Pads the message
- Breaks it up into chunks
- Passes chunks into a fancy "bit mixer"
- Creates fixed sized hash
- Double Hash is the SHA256 hash of a hash

### RIPEMD-160:

- used because it produces the shortest hashes whose uniqueness is still sufficiently assured. This allows Bitcoin addresses to be shorter
- Double SHA256 hashes are often used in place of a single hash in - Bitcoin for added security, to mitigate a few shortcomings of just one round of SHA256, and some related attacks discovered on the older version of SHA (SHA-1).

### Bitcoin Fees:

- Fees acts as a financial incentive for miners to include the transaction in their block, because they get to keep the change. The higher the fee to the miner, the more likely and faster the transaction is to appear in the blockchain

### BTC Transactions:

- Must be fully spent, so all of it has to go. So to send half, you must send half there and half back
- considered valid if the sum of all outputs is lower than the sum of all inputs. This prevents us from minting BTC

### Locking & Unlocking Scripts:

- encumbrance placed on an output, and it specifies the conditions that must be met to spend the output in the future
  simply a set of instructions that specifies how a UTXO is able to be spent
- this locks or encumbers (to use the official terminology) the future spending of the bitcoin
- Unlocking the bitcoin requires satisfying the script.

### Digital Signature in Transactions:

- used to verify that you are the one receiving/sending BTC

### Big and Little Endian

- describe how bytes are organized in storage
- Big end -> most significant part of value is stored first in the sequence of bytes
- Little end -> least significant value part stored first
