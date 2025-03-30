Here's a simple example of how to use AWS KMS to encrypt and decrypt data using the AWS SDK for JavaScript (Node.js). Before you start, make sure you have the following prerequisites:

1. AWS account
2. AWS CLI installed and configured with your credentials
3. A KMS key created in your AWS account

### Step 1: Install the AWS SDK

If you haven't already, install the AWS SDK for Node.js:
`npm install aws-sdk`

### Step 2: Encrypt Data

Here’s an example of how to encrypt data using AWS KMS in Node.js:
```javascript
const AWS = require('aws-sdk'); const kms = new AWS.KMS();  // The plaintext data you want to encrypt 
const plaintext = "This is a secret message";  
// The KMS key ID (either the key ID or ARN of the key) 
const keyId = "arn:aws:kms:us-east-1:123456789012:key/abcd1234-12ab-34cd-56ef-1234567890ab";  // Encrypt the plaintext 
const params = {   KeyId: keyId, 
// Key ID or ARN of the KMS key   
Plaintext: plaintext 
// Data to encrypt 
};  

kms.encrypt(params, (err, data) => {   if (err) {     console.log("Error encrypting data:", err);   } else {     console.log("Encrypted data:", data.CiphertextBlob.toString('base64'));   } });
```


### Step 3: Decrypt Data

Now, let’s decrypt the data using the KMS key:
```javascript
const encryptedData = "<your-encrypted-base64-data>"; // Replace with the encrypted data from the previous step  
const decryptParams = {   CiphertextBlob: Buffer.from(encryptedData, 'base64') }; // Convert the base64-encoded encrypted data back to a buffer 

kms.decrypt(decryptParams, (err, data) => {   if (err) {     console.log("Error decrypting data:", err);   } else {     console.log("Decrypted data:", data.Plaintext.toString());   } });
```

### Step 4: Run the Code

- When you run the encryption part, it will return an encrypted version of your data.
- You then run the decryption code, passing the encrypted data, and it will return the original plaintext.

### Notes:

1. Replace `keyId` with your actual KMS key ID or ARN. You can find this in the AWS KMS console.
2. Ensure that your AWS IAM user or role has the necessary permissions to perform encryption and decryption operations using KMS.
3. **HTTPS** only encrypts data during transmission. Once the data reaches its destination (like a database or file storage), it is typically stored in an unencrypted format unless explicitly encrypted.
4. **KMS** allows you to encrypt your data at rest, ensuring that even if someone gains unauthorized access to your storage system (e.g., S3 buckets, databases), they cannot read the encrypted data without the proper key.