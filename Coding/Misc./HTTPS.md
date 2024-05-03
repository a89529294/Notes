HTTPS uses what’s known as an **asymmetric public key infrastructure**. [This type of security system uses two different keys to encrypt communications between two parties: The private key and the public key](https://www.cloudflare.com/learning/ssl/what-is-https/)[2](https://www.cloudflare.com/learning/ssl/what-is-https/).

The **private key** is controlled by the owner of a website and it’s kept private. [This key lives on a web server and is used to decrypt information encrypted by the public key](https://www.cloudflare.com/learning/ssl/what-is-https/)[2](https://www.cloudflare.com/learning/ssl/what-is-https/).

The **public key** is available to everyone who wants to interact with the server in a secure way. [Information that’s encrypted by the public key can only be decrypted by the private key](https://www.cloudflare.com/learning/ssl/what-is-https/)[2](https://www.cloudflare.com/learning/ssl/what-is-https/).

### workflow
1. **Client-to-Server Communication**:
    - When a client (e.g., a web browser) connects to a server over HTTPS (HTTP Secure), the server sends its public key to the client during the SSL/TLS handshake.
    - The client then uses this public key to encrypt a symmetric encryption key (session key) and sends it securely back to the server.
    - Upon receiving the encrypted session key, the server uses its private key to decrypt it and obtain the session key.
2. **Server-to-Client Communication**:
    - After the SSL/TLS handshake is completed and a secure session key is established, both the client and server can encrypt and decrypt data symmetrically using this session key.
    - When the server sends data (e.g., a webpage) back to the client, it encrypts the data using the session key.
    - The client, upon receiving this encrypted data, uses the same session key (already securely exchanged) to decrypt and access the original data.
