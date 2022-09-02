**Running nodejs in prouction**

We use a process manager which manages the node process when running in production
- [This talks about PM2, docker, systemd](https://maximorlov.com/start-node-js-in-production/)
- [Running nodejs with systemd](https://www.axllent.org/docs/nodejs-service-with-systemd/)
- [This talks about setting up a reverse proxy nginx and managing node with PM2](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-node-js-application-for-production-on-debian-10)

**Running angular in prouction**

We need to place the static files to a specifed location
- [Link 1](https://arjunphp.com/deploy-angular-app-production-nginx/)
- [Link 2](https://balramchavan.medium.com/deploy-angular-application-in-nginx-server-on-digitalocean-ubuntu-droplet-28380524811e)


**Connect NodeJS app to a database with and without ORM**

For postgres

- [Without ORM](https://dev.to/miku86/nodejs-postgresql-how-to-connect-our-database-to-our-simple-express-server-without-an-orm-10o0)
- [With ORM](https://dev.to/miku86/nodejs-postgresql-how-to-connect-our-database-to-our-simple-express-server-with-an-orm-gcm)

**TCP and sockets**
- [What is a socket](https://www.howtogeek.com/devops/what-are-unix-sockets-and-how-do-they-work/)
- [Understanding socket with socat utility](https://www.digitalocean.com/community/tutorials/understanding-sockets)
- [Source port allocation to establish a TCP/IP connection](https://idea.popcount.org/2014-04-03-bind-before-connect/)
- [Sockets in a Bind](https://blog.heroku.com/sockets-in-a-bind)
- [Details on the socket queues](https://blog.cloudflare.com/syn-packet-handling-in-the-wild/)

**All about lock files**
- [Yarn lock: how it works](https://11sigma.com/blog/2021/09/03/yarn-lock-how-it-works-and-what-you-risk-without-maintaining-yarn-dependencies-deep-dive/)

- [Lockfiles should be committed on all projects](https://classic.yarnpkg.com/blog/2016/11/24/lockfiles-for-all/)

**Understaning JWTs with proper secure implementaion**
- **[The Ultimate Guide to handling JWTs on frontend clients]**(https://hasura.io/blog/best-practices-of-using-jwt-with-graphql) Read: _Where do we save it then?_ section of this blog also get a complete idea
- [Where should the JWT token stored in client side](https://github.com/OWASP/CheatSheetSeries/blob/master/cheatsheets/JSON_Web_Token_for_Java_Cheat_Sheet.md#token-storage-on-client-side)
- [How CSRF attack actually works](https://owasp.org/www-community/attacks/csrf) Follow the References in this blog to understand other attacks
- [How Cross Site Scripting (XSS) attack works](https://owasp.org/www-community/attacks/xss/)
- [HTML5 Security Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/HTML5_Security_Cheat_Sheet.html)
- [Local Storage vs Session Storage vs Cookie](https://www.xenonstack.com/insights/local-vs-session-storage-vs-cookie)
- [All about cookies](https://developer.mozilla.org/en-US/docs/Web/HTTP/Cookies)
- [Why Bearer before the token](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Authorization#directives) Authorization: _type_ credentials
This is because there are different authorization schemes
- [Heavy debate on stackoverflow - Invalidating JSON Web Tokens](https://stackoverflow.com/questions/21978658/invalidating-json-web-tokens/52407314#52407314)

**All about web secure practices**
- [Golden cheatsheet of OWASP](https://github.com/OWASP/CheatSheetSeries/tree/master/cheatsheets)