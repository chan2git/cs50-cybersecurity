# Lecture 1: Securing Accounts
The below notes are based on HarvardX's CS50 - Introduction to Cybersecurity, Lecture 1: Securing Data You can watch at: https://www.youtube.com/watch?v=X3DVaMnl5n8&list=PLhQjrBD2T383Cqo5I1oRrbC1EKRAKGKUE&index=3


### Hashing

The process of using an input (like a string or a password) and converting it to an output known as a hash value using an algorithm. Passwords are usually stored as a hash value instead of plain clear-text.
- "apple" --> "..ekWXa83dhiA"
- "banana" --> "..ZS4zkCo/P7E"
- "cherry" --> "..rj98gxDTYfM"

The platform can run a hash algorithm on the user's submitted password and converts/stores the username:hash value in their servers. When users log back in, a hash algorithm will be ran again and hash values are compared for authentication. Hash values are typically one way algorithms; you can't reverse a hash value output to reveal the plain-text input.

While hashing raises the bar of effort for threat actors to attempt to compromise, it's still suspectible to attacks.


### Rainbow Table

A list of possible passwords and their hash values already computed often used for quicker comparing of hash values.


### Salting

Adds some element during the hash function as an additional input to the hash function as an attempt to generate a more unique hash value - useful when users have the same passwords which presumably would generate the same hash value unless otherwise an additional element ("salt", "salting") is added to drastically change the output.

NIST recommends:
- Verifiers shall store memorized secrets in a form that is resistant to offline attacks. Memorized secrets shall be salted and hashed using a suitable one-way key derivation function. . . Their purpose is to make each password guessing trial by an attacker who has obtained a password hash file expensive and therefore the cost of a guessing attack high or prohibitive


### Cryptography

The study and practice of securing data, especially when transmitting data. Can be broken down into categories:

- Codes
    - A mapping between code words and actual meanings of the code words
    - Code words typically make no sense unless its read by the intended recipient who has access to the code word mappings to properly decode the message
    - Encoding is taking plaintext and transcribing it into codetext. Decode is the reverse.

- Ciphers
    - An algorithm used to convert a message typically focusing on individual letters/characters instead of whole words/phrases.
    - Encipher is the process of taking plaintext and transcribing it into ciphertext, also known as encrypting. The reverse is decrypt.

- Keys
    - A shared secret between you and a intended recipient that can be used to tailor publicly-tested encryption algorithms to your specific communication.


### Secret-Key Encryption (Symmetric-Key Encryption)

When parties utilize the same key. A message and key is used as a input to produce a ciphertext output. Algorithms include AES and Triple DES.

### Public-Key Cryptography (Assymetric-Key Encryption)

When parties have their own individual pair of public and private keys. Public keys are made known publicly and used by a party to sign/encrypt a message in which only the corresponding private key can be used to decrypt the message. Algorithms include Diffie-Hellman, MQV, and RSA. 

Example:
- Alice uses Bob's public key to encrypt a message and sends it to Bob
- Only Bob's private key (which is only known and held by Bob) can be used to decrypt Alice's message


### Digital Signatures
Used to verify the authenticity of a message or the sender of a message using public/private keys and hashing. Algorithms include DSA, ECDSA, and RSA.

Example:
- Alice applies a hash algorithm to a message and produces a hash value output
- Alice then uses her private key and the hash value output together and produces another output that is her digital signature
- Bob wants to verify Alice's message. Bob takes Alice's message and puts it through the same hash algorithm and produces a hash value output
- Bob then uses Alice's public key and Alice's digital signature together to produce a hash value output that should match the previously produced hash value output
- If the hash values match by using Alice's public key, then it proves that this message was encrypted by Alice's private key, which only Alice should know and have.


### Encryption in Transit

Alice <--> Gmail <--> Bob

While Alice and Bob have individual secure connections to Gmail, it does not mean that Alice and Bob have a secure connection to each other, and or that Gmail couldn't view Alice/Bob's communication. The communication is only encrypted Between Alice to Gmail, and from Gmail to Bob.

End-to-end encryption ensures that communication between Alice and Bob are secured and encrypted. This may prevent intruders or third-parties can view Alice and Bob's communication.


### Deletion

When a file is deleted, the computer is simply freeing up the space where your file location, but the file's underlying data is still there. Over time, the computer may overwrite this underlying data. To securely delete files, the underlying data needs to be overwritten.

### Full Desk Encryption

A state in which your device's data is fully encrypted when it's not actively in use by an authenticated user.


### Ransomware

Malware that encrypts a victim's data. Threat actors will try to extort victims into paying a ransom in order to decrypt and get back their data.

### Quantum Computin

Typically bits can be either 0 or 1. Quantum computing allows for a bit to be in multiple states at once. In theory, if adversaries have access to quantum computing then it's possible to brute force and crack strong algorithms.