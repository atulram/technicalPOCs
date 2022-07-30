Authentication Methods
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

[Source this website](https://www.pingidentity.com/en/resources/blog/post/the-top-6-authentication-mechanisms.html)