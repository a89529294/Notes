### credentials
Whatever is needed to identify a user on the server side.
e.g. username/password

### single sign on
SSO is a **user authentication system** that allows a user to log in once and access multiple related or unrelated systems without having to log in again.
In tje example of Google services:
- If you log into **Gmail** and then open **Google Calendar**, you don't need to log in again.
- This is because **SSO** allows a single login session across multiple **related services** (all part of Google's ecosystem).

### two factor authentication
username/password is __one factor authentication__. On top of that we can add in __email__, __sms__ to the user's phone as the second factor.

### OAuth 2.0
**OAuth2** is an **authorization** protocol that allows third-party applications to access a user’s data from another application, without needing the user’s credentials. It’s often used in scenarios where you want to give an application limited access to your data from another service.

example 1
- login to website A
- website A redirects you to google
- you login to google
- google asks if you want to share certain info with website A
- after you accept, you get redirected back to website A
- you are logged into website A

example 2 
Imagine an app (like a fitness tracker) requesting permission to access your Google Calendar. With OAuth 2.0, you can grant the app access to your calendar events without sharing your Google credentials.

### OTP (One Time Password)
Where the user receives a code via sms or email. 
__Magic link__ also does something similar.

### magic link (similar to otp)
the user must be on the same browser for the initial request and the follow up clicking on the link.
1. **Server generates a unique token**: The server creates a unique token that will be used to identify the user’s session.
2. **Token is stored in a secure, HTTP-only cookie**: The server sets this token in a secure, HTTP-only cookie in the user’s browser. This means the token can’t be accessed by client-side JavaScript, which helps prevent cross-site scripting (XSS) attacks. Or better yet, **store the token in the DB**.
3. **Server sends an email with the magic link**: The server embeds the token in a URL, which is then sent to the user’s email as a magic link.
4. **Server verifies the token**: When the user clicks the magic link, the server checks if the token in the URL matches the one stored in the user’s browser cookie. If they match, the server authenticates the user.
    
This process ensures that even if someone else gets hold of the magic link, they won’t be able to use it unless they also have access to the user’s original browser session. This adds an extra layer of security compared to traditional OTP methods.

### ssh authentication
1. **Key Pair Generation**:
    - To set up passwordless authentication, you generate a **key pair** consisting of a **public key** and a **private key**.
    - The **private key** remains securely stored on your local workstation.
    - The **public key** is placed on each remote system you want to access.
2. **Generating the Key Pair**:
    - Run the following command to generate the key pair (using ed25519 as an example):
        ```
        $ ssh-keygen -t ed25519
        ```
    - You’ll be prompted to choose a location to save the keys (defaults to `~/.ssh/id_ed25519`).
    - Optionally, you can set a passphrase for added security.
3. **Key Storage**:
    - The default location for storing keys is the `~/.ssh` directory.
    - Ensure that the directory is created with the correct permissions. 
    ```bash
# Private key permissions MUST be strict
chmod 600 ~/.ssh/id_ed25519     

# Public key can be more permissive
chmod 644 ~/.ssh/id_ed25519.pub

# .ssh directory permissions
chmod 700 ~/.ssh

# authorized_keys permissions on remote
chmod 600 ~/.ssh/authorized_keys
 .  ```
    - The `.pub` file contains the **public key**, which you’ll transfer to remote systems.
4. **Using the Public Key**:
    - On each remote system, add the **public key** to the `~/.ssh/authorized_keys` file.
    - This allows the system to authenticate you using the corresponding **private key**.
5. **Authentication Process**:
    - When you connect to a remote system, the server issues a challenge that can only be solved using your private key.
    - The server verifies the signature using the **public key** stored in `authorized_keys`.
    - If the signature matches, you’re granted access without needing a password.
    - The private key does not leave your physical device.

By using this method, you eliminate the risk of leaked passwords and enhance security. [It’s commonly used for SSH access to servers and other systems](https://www.redhat.com/sysadmin/passwordless-ssh)[1](https://www.redhat.com/sysadmin/passwordless-ssh)[2](https://medium.com/@sudheer.barakers/ansible-passwordless-ssh-authentication-using-public-private-key-pairs-1bf91fff349e). 

On some operating systems like macOS, you can use biometrics to unlock your SSH key passphrase stored in the system keychain, but this is different from the SSH authentication process itself.

### WebAuthn
1. **Registration:**
    - When a user registers for a service, a new passkey is created.
    - The user's username, the service name, and the generated public key are stored together in the passkey.
    - The corresponding private key is securely stored on the user's device.
2. **Authentication:**
    - When the user attempts to log in, the service sends a challenge.
    - The device looks for a passkey that matches the provided username and service.
    - If a matching passkey is found, it contains the public key associated with the user's account.
    - The device uses the private key corresponding to this public key to sign the challenge.

Here's a breakdown of where the different components are stored:
- **Public Key:** This is stored in the relying party's database, associated with the user's account. It's used to verify signatures during authentication.
- **Private Key:** This is stored securely on the user's device. It's used to sign challenges during authentication.
- **Passkey:** The passkey, which includes the user's identity (username, service) and the associated public key, is typically stored on the user's device. It acts as a bridge between the user's identity and their cryptographic keys.