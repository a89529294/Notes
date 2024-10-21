The **WebOTP API** provides a streamlined user experience for web apps to verify that a phone number belongs to a user when using it as a sign-in factor. WebOTP is an extension of the [Credential Management API](https://developer.mozilla.org/en-US/docs/Web/API/Credential_Management_API).

The verification is done via a two-step process:
1. The app client requests a one-time password (OTP), which is obtained from a specially-formatted SMS message sent by the app server.
2. JavaScript is used to enter the OTP into a validation form on the app client and it is submitted back to the server to verify that it matches what was originally sent in the SMS.