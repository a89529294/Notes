### credentials
Whatever is needed to identify a user on the server side.
e.g. username/password

### single sign on
is used for **authentication** within a single enterprise or across web apps owned by different parties, allowing a user to use one set of login credentials to access multiple applications.

### two factor authentication
username/password is __one factor authentication__. On top of that we can add in __email__, __sms__ to the user's phone as the second factor.

### OAuth 2.0
**OAuth2** is an **authorization** protocol that allows third-party applications to access a user’s data from another application, without needing the user’s credentials. It’s often used in scenarios where you want to give an application limited access to your data from another service.

- login to website A
- website A redirects you to google
- you login to google
- google asks if you want to share certain info with website A
- after you accept, you get redirected back to website A
- you are logged into website A

### OTP (One Time Password)
Where the user receives a code via sms or email. 
__Magic link__ also does something similar.

### magic link (similar to otp)
the user must be on the same browser for the initial request and the follow up clicking on the link.
1. **Server generates a unique token**: The server creates a unique token that will be used to identify the user’s session.
2. **Token is stored in a secure, HTTP-only cookie**: The server sets this token in a secure, HTTP-only cookie in the user’s browser. This means the token can’t be accessed by client-side JavaScript, which helps prevent cross-site scripting (XSS) attacks.
3. **Server sends an email with the magic link**: The server embeds the token in a URL, which is then sent to the user’s email as a magic link.
4. **Server verifies the token**: When the user clicks the magic link, the server checks if the token in the URL matches the one stored in the user’s browser cookie. If they match, the server authenticates the user.
    
This process ensures that even if someone else gets hold of the magic link, they won’t be able to use it unless they also have access to the user’s original browser session. This adds an extra layer of security compared to traditional OTP methods.

### passwordless/webAuthn
1. **Key Pair Generation**:
    - To set up passwordless authentication, you generate a **key pair** consisting of a **public key** and a **private key**.
    - The **private key** remains securely stored on your local workstation.
    - The **public key** is placed on each remote system you want to access.
2. **Generating the Key Pair**:
    - Run the following command to generate the key pair (using RSA as an example):
        ```
        $ ssh-keygen
        ```
    - You’ll be prompted to choose a location to save the keys (defaults to `~/.ssh/id_rsa`).
    - Optionally, you can set a passphrase for added security.
3. **Key Storage**:
    - The default location for storing keys is the `~/.ssh` directory.
    - Ensure that the directory is created with the correct permissions.
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

Note that it is possible to add more security by guarding the access of the private key using fingerprint or facial id.

