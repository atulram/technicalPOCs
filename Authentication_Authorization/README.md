Authentication Methods

[Source this website](https://www.pingidentity.com/en/resources/blog/post/the-top-6-authentication-mechanisms.html)
 - Passwords
 
        A password is a shared secret known by the user and presented to the server to authenticate the user
 - Hard Tokens

        These are small hardware devices that the owner carries to authorize access to a network service. The device may be in the form of a smart card, or it may be embedded in an easily-carried object such as a key fob or USB drive. The device itself contains an algorithm (a clock or a counter), and a seed record used to calculate the pseudo-random number. Users enter this number to prove that they have the token. The server that's authenticating the user must also have a copy of each key fob's seed record, the algorithm used and the correct time. The historical challenge of relying on hardware tokens for MFA has been the requirement that users always carry these tokens with them.
 - Soft Tokens

        Soft tokens leverage mobile phones' ability to generate an OTP and, possibly, their communication network. A user can demonstrate possession of his/her previously registered phone by receiving a message sent to that device. An OTP can be sent to the phone by SMS, voice call, or with an app that receives an authentication prompt via the mobile OS notification services, which is then entered by the user into a sign-on screen.
 - Biometric Authentication
 - Contextual Authentication

        Contextual authentication collects signals like geolocation, IP address and time of day in order to help establish assurance that the user is valid. Typically, a user's current context is compared to previously established context (or blacklists/whitelists) in order to spot inconsistencies and identify potential fraud. These checks are invisible to the authorized user, so there are no usability issues, but they can create a significant barrier to an attacker. As an example, Visa's mobile location confirmation mechanisms determine the location of the user's mobile phone to verify that the user is physically near the location where the credit card is being used. The chances of a fraudulent transaction are higher if the transaction takes place in a different location from the phone.
 - Device Identification

        Device identification establishes a fingerprint that's somewhat unique to that device. Over time, this fingerprint allows the authentication server to recognize that device and determine when the user associated with it attempts to authenticate from a different device, which could indicate fraudulent activity

[Source1 this website](https://blog.miniorange.com/different-types-of-authentication-methods-for-security/)

[Source1 this website](https://www.educba.com/authorization-types/)

- Multi-Factor Authentication

        Multi-Factor Authentication (MFA) is an authentication method in which an individual must pass multiple factors in order to gain access to a service or network. It’s an extra layer of security on top of the standard password-based login. Individuals must also submit a second factor in the form of a one-time code that they will receive through phone or email in addition to their Username and Password.
    
- Certificate-based authentication

        A certificate is made up of a user’s digital identity, which contains a public key and a certification authority’s digital signature. This certificate verifies that the public key and the person who issued the certificate are both the same person. When a user attempts to log in to a server, they must first present their digital certificate

- Token-Based Authentication

        Token-Based Authentication allows users to enter their credentials only once and obtain a one-of-a-kind encrypted string exchange in return. After that, you won’t have to input your credentials every time you want to log in or acquire access. The digital token ensures that you have already been granted access. Most use cases, such as Restful APIs that are accessed by many frameworks and clients, require token-based authentication.
    
- Single Sign-On Authentication (SSO

        Single Sign-On is a subset of basic username-password-based Authentication. Going with SSO authentication will provide advanced security and multiple features with frictionless experience to your end-users. Single Sign-On as the name depicts allows individuals to enter their username and password once and get access to all configured applications. Simply stating you will have the provision to configure “N no apps”

- API Passwords

         An API key is a unique identifier for web service requests that identifies their source (or similar types of requests).When a user attempts to get allowed access to a system for the first time through registration, a key is produced.Following that, the API key is paired with a secret token and is submitted with subsequent queries.When a user tries to re-enter the system, their unique key is used to verify that they are the same person who used the system previously.
        
- OAuth

        OAuth is a popular API authentication technique that allows for both authentication and authorization.OAuth allows the API to authenticate and access the system or resource requested by establishing scope.





