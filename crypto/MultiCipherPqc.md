# Multi Cipher PQC

## Signatures

- RSA-Signature
- Curve25519-Signature (Ed25519)
- Crystals Dilithium

## Encryption

- RSA-Encryption
- Curve25519-Encryption (X25519)
- Crystals Kyber

## Symmetric Cipher

- ChaCha20-Poly1305

## Tool-Features

- Create a key set (RSA-Enc, RSA-Sign, X25519, Ed25519, Kyber, Dilithium)
- Sign data with any algorithm
- Encrypt data with any algorithm

## Commandline

### Create key

````
pqc.jar -keygen <keystore-file> -pw <password>
````

### Sign

````
pqc.jar -sign <keystore-file> -pw <password> -data <data-file> -sig-out <sign-file>
````

### Encrypt

````
pqc.jar -enc <keystore-file> -pw <password> -data-in <data-file-in> -data-out <data-file-out>
````



## Glosar

| Short | Long |
| ----- | ---- |
| CRYSTALS | Cryptographic Suite for Algebraic Lattices |
