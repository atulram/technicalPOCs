**Oauth authorization_code grant flow**

![auth_code grant digram](https://i0.wp.com/architectxchange.com/wp-content/uploads/2020/10/OAuthWebServerFlow.png?resize=1536%2C1165&ssl=1)

- Register the client with authorization server to get client_id and client_secret. We need to supply the redirect_uri (htp://localhost:80 in this case)
- Get info about all the enpoints of the authorization server by hitting the well known cofiguration url (https://accounts.google.com/.well-known/openid-configuration)
- Get the resorce server endpoints (google photos api in this case)

- Making the GET Auth code call ( __Authorization Enpoint__ )

        curl --location --request GET 'https://accounts.google.com/o/oauth2/v2/auth?response_type=code&client_id=90krq.apps.googleusercontent.com&scope=openid%20profile%20email%20https://www.googleapis.com/auth/photoslibrary.readonly&state=state123&redirect_uri=http://localhost:80&access_type=offline&prompt=consent'

- Extract auth code from the response

        http://localhost/?state=state123&code=4/0AWtwJYfYLnrA&scope=email%20profile%20openid%20https://www.googleapis.com/auth/userinfo.profile%20https://www.googleapis.com/auth/userinfo.email%20https://www.googleapis.com/auth/photoslibrary.readonly&authuser=0&prompt=consent

- Fetch the access token request ( __Token Endpoint__ )

        curl --location --request POST 'https://oauth2.googleapis.com/token' \
        --header 'Content-Type: application/x-www-form-urlencoded' \
        --data-urlencode 'grant_type=authorization_code' \
        --data-urlencode 'client_id=90gkrq.apps.googleusercontent.com' \
        --data-urlencode 'client_secret=GO76Jq3aj729' \
        --data-urlencode 'redirect_uri=http://localhost:80' \
        --data-urlencode 'code=4/0ATtgzhIpA'

        
        Response looks like below

        {
            "access_token": "...",
            "expires_in": 3599,
            "refresh_token": "...",
            "scope": "https://www.googleapis.com/auth/userinfo.profile https://www.googleapis.com/auth/photoslibrary.readonly openid https://www.googleapis.com/auth/userinfo.email",
            "token_type": "Bearer",
            "id_token": "..."
        }

- Make call to the resource server using the acces token

        curl --location --request GET 'https://photoslibrary.googleapis.com/v1/albums' \
        --header 'Authorization: Bearer ya29.a0AKJkPtz2ird-coHaCgYKAQMSARESFQGbdwaIJ8KoOF6sfkILvRNMYjqI_g0163'

Other endpoints to explore

![](auth_code_grant.PNG)

If the client wants to validate the token or after sometime when the access token gets expired. The client/3rd_party_app can check if the access token is valid or not by requesting the __Tokeninfo/Introspect Endpoint__. This endpoint is mainly used by the resource server to verify the access token. The resource server can also use the public key of the authorization server to verify the token instead and that is more performant

        curl --location --request POST 'https://www.googleapis.com/oauth2/v1/tokeninfo' \
        --header 'Content-Type: application/x-www-form-urlencoded' \
        --data-urlencode 'access_token=ya29.a0z2ird-coHaCgYKAQMSARESFQGbdwaIJ8KoOF6sfkILvRNMYjqI_g0163'

To regenerate the access token again after expiry, the client/3rd_party_app need not ask the user to generate it again, The client will make use of the refresh token that it got earlier to generate the access_token. The call happens to the token endpoint 

        curl --location --request POST 'https://oauth2.googleapis.com/token' \
        --header 'Content-Type: application/x-www-form-urlencoded' \
        --data-urlencode 'grant_type=refresh_token' \
        --data-urlencode 'client_id=901796891631-pv3c7ul7rf0lcuomelj615o1ufmqgkrq.apps.googleusercontent.com' \
        --data-urlencode 'client_secret=GOJq3aj429' \
        --data-urlencode 'refresh_token=1//0jkoZRy85QbvzRC1M6UNLTzqqlPj8z4'

Now if the client wants to fetch more info about the user, the scope for the access token should have had openid. If the scope had openid then the client can use the __Userinfo Endpoint__ to get more info about the user

        curl --location --request GET 'https://openidconnect.googleapis.com/v1/userinfo' \
        --header 'Authorization: Bearer ya29.a0AVHuf166'

The resource server need to verify the acces token against the authorization server. It can choose to validate the token by calling the tokeninfo endpoint of the authorization server like above or fetch the public key of the authorization server by calling the __JWKS Endpoint__

        curl --location --request GET 'https://www.googleapis.com/oauth2/v3/certs'



**Oauth authorization_code PKCE grant flow**

![](./auth_code_grant_pkce.PNG)

This is a safer approach than plain Authorization code grant. It can be used when the client is running in a public network (like browser, android phone etc). Here a code_challenge is passed along with the get auth_code call (The get auth code call is happening from the client running in browser). The authorization server remembers this code_challenge. Now when the client makes the call to get the access_token, it needs to also send the code_verifier. The code_challenge is the encrypted then encoded version of code_verifier. The authz server then performs this operation to validate and then sends the acces token. The idea here is if the client id and client secret, auth_code and code_challenge is compromised since it is running in the browser, the hacker will still need to know the code_verifier to get the access token

        curl --location --request GET 'https://accounts.google.com/o/oauth2/v2/auth?response_type=code&client_id=90hjfmq.apps.googleusercontent.com&scope=openid%20https://www.googleapis.com/auth/photoslibrary.readonly&state=state123&redirect_uri=http://localhost:80&prompt=consent&code_challenge=fkhlv2p3j0BoYN3bUDF0wx03bPKgt_xG_5xIYAvI&code_challenge_method=S256'


        Get access_token call will include code_verifier

        curl --location --request POST 'https://oauth2.googleapis.com/token' \
        --header 'Content-Type: application/x-www-form-urlencoded' \
        --data-urlencode 'grant_type=authorization_code' \
        --data-urlencode 'client_id=901796891631-pv3c7ul7rf0lcuomelj615o1ufmqgkrq.apps.googleusercontent.com' \
        --data-urlencode 'client_secret=GO98Uaj429' \
        --data-urlencode 'redirect_uri=http://localhost:80' \
        --data-urlencode 'auth_code=4/05klf9FjObwd7UvGatoYJvwJYfYLnrA' \
        --data-urlencode 'code_verifier=AtulRam'


We should always use pkce grant if possible even if the client is private