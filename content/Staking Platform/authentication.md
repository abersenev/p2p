# Authentication

Get your authentication token

Staking Platform APIs use bearer JSON Web Token (JWT). Each client is assigned a unique authentication token for secure access to the service.

Currently, the process of obtaining these tokens is manual as we are in the development phase of an API interface. Follow the steps below to get your free authentication token:

1. **Contact us**

   Email **alessandro.maci@p2p.org**, providing your account details (such as company name), and request an authentication token.

2. **Check your email**

   Our Product team will manually generate authentication token and send it to you via email.

Specify the received authentication token when accessing Staking Platform via the API. Pass the token in the Authorization header in the following format:

```curl
authorization: Bearer <token>
```

Please note that this manual process is temporary. We are actively working on an automated interface to allow you to retrieve authentication tokens independently. We appreciate your patience and cooperation during this period.
