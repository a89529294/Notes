cryptography is about encrypting and decrypting data. Encryption transforms a key and input, called the "plaintext", into an encrypted output, called the "ciphertext". Only the person with the key can then decrypt the ciphertext back into the plaintext.

### Encryption
Encryption is the process of converting plaintext (the original, readable data) into ciphertext (the encrypted, unreadable data) using an algorithm and a key. The key is a piece of information that determines the functional output of the cryptographic algorithm.

- **Plaintext**: This is the original data that you want to protect. It can be any form of data, such as text, images, or binary files.
- **Ciphertext**: This is the result of the encryption process. It appears random and cannot be understood without decrypting it.
- **Key**: The secret piece of information used in conjunction with the algorithm to transform plaintext into ciphertext and back again. The security of encrypted data depends significantly on the secrecy of the key.

### Decryption
Decryption is the reverse process of encryption. It converts ciphertext back into plaintext using the same or a corresponding key and algorithm.

Only those who possess the correct key can decrypt the ciphertext back into its original plaintext form. This ensures that unauthorized parties cannot access the underlying data even if they manage to intercept the ciphertext.

### Types of Cryptography
There are two main types of cryptographic algorithms: symmetric and asymmetric.
#### Symmetric Cryptography
In symmetric cryptography, the same key is used for both encryption and decryption. This means that both the sender and receiver must have the same key and keep it secret.

- **Example Algorithms**: Advanced Encryption Standard (AES), Data Encryption Standard (DES)
- **Advantages**: Faster and more efficient for large amounts of data.
- **Disadvantages**: Key distribution can be challenging because the same key must be securely shared between both parties.

#### Asymmetric Cryptography
In asymmetric cryptography, two different but mathematically related keys are used: a public key and a private key. The public key is used for encryption, and the private key is used for decryption.

- **Example Algorithms**: RSA (Rivest-Shamir-Adleman), ECC (Elliptic Curve Cryptography)
- **Advantages**: Simplifies key distribution as the public key can be shared openly, while the private key remains secure.
- **Disadvantages**: Generally slower and more computationally intensive than symmetric cryptography.

### Applications of Cryptography
Cryptography is used in various applications to secure information and communications, including:
- **Secure Communication**: Encrypting emails, instant messages, and other forms of communication.
- **Data Protection**: Protecting data stored on devices and in databases.
- **Authentication**: Verifying the identity of users and devices.
- **Digital Signatures**: Ensuring the authenticity and integrity of digital documents.
- **Cryptographic Hashing**: Creating unique fingerprints for data, which is useful in data integrity checks and digital signatures.

### Notes
- [Symmetric encryption](https://blog.boot.dev/cryptography/aes-256-cipher/#symmetric-encryption-vs-asymmetric-encryption) should typically just be used to encrypt information for _oneself_. If you're encrypting data for someone else, you should use asymmetric encryption.