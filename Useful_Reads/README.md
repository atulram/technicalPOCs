**Running nodejs in prouction**

We use a process manager which manages the node process when running in production
- [This talks about PM2, docker, systemd](https://maximorlov.com/start-node-js-in-production/)
- [Running nodejs with systemd](https://www.axllent.org/docs/nodejs-service-with-systemd/)
- [This talks about setting up a reverse proxy nginx and managing node with PM2](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-node-js-application-for-production-on-debian-10)
- [A step by step guide to deploy in aws EC2](https://gist.github.com/piyushgarg-dev/8b14c87c8ff4d626ecbc747b6b9fc57f)

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

**Tunneling**

- [Tunneling using cloudflare](https://www.youtube.com/watch?v=BnWfbv7Fy-k)

**All about lock files**
- [Yarn lock: how it works](https://11sigma.com/blog/2021/09/03/yarn-lock-how-it-works-and-what-you-risk-without-maintaining-yarn-dependencies-deep-dive/)

- [Lockfiles should be committed on all projects](https://classic.yarnpkg.com/blog/2016/11/24/lockfiles-for-all/)

**Understaning JWTs with proper secure implementaion**
- **[The Ultimate Guide to handling JWTs on frontend clients](https://hasura.io/blog/best-practices-of-using-jwt-with-graphql) Read: _Where do we save it then?_ section of this blog also get a complete idea**
- [Where should the JWT token stored in client side](https://github.com/OWASP/CheatSheetSeries/blob/master/cheatsheets/JSON_Web_Token_for_Java_Cheat_Sheet.md#token-storage-on-client-side)
- [How CSRF attack actually works](https://owasp.org/www-community/attacks/csrf) Follow the References in this blog to understand other attacks
- [How Cross Site Scripting (XSS) attack works](https://owasp.org/www-community/attacks/xss/)
- [HTML5 Security Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/HTML5_Security_Cheat_Sheet.html)
- [Local Storage vs Session Storage vs Cookie](https://www.xenonstack.com/insights/local-vs-session-storage-vs-cookie)
- [All about cookies](https://developer.mozilla.org/en-US/docs/Web/HTTP/Cookies)
- [Why Bearer before the token](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Authorization#directives) Authorization: _type_ credentials
This is because there are different authorization schemes
- [Heavy debate on stackoverflow - Invalidating JSON Web Tokens](https://stackoverflow.com/questions/21978658/invalidating-json-web-tokens/52407314#52407314)
- Also research on chained tokens

**All about web secure practices**
- [Golden cheatsheet of OWASP](https://github.com/OWASP/CheatSheetSeries/tree/master/cheatsheets)

**Kubernetes autentication and authorization**
- [Authentication explained](https://www.weave.works/blog/kubernetes-authentication)
- [Authorization explained RBAC](https://learnk8s.io/rbac-kubernetes)

**DNS**
- [How dns works](https://www.namecheap.com/dns/what-is-dns-domain-name-system-definition/)
- [How dns works with images](https://howdns.works/)
- [Similar how dns works](https://phoenixnap.com/kb/what-is-domain-name-system-works)
- [Dns Propagation explained](https://www.namecheap.com/support/knowledgebase/article.aspx/9622/10/dns-propagation-explained)
- Run Your Own Authoritative DNS Servers
    - [Prebaked scripts](https://www.joshmcguigan.com/blog/run-your-own-dns-servers/)
    - [Setup in linux](https://opensource.com/article/17/4/build-your-own-name-server)
    - [Digital ocean blog](https://www.digitalocean.com/community/tutorials/how-to-configure-bind-as-an-authoritative-only-dns-server-on-ubuntu-14-04)

**Certs**

- [Client Certs](https://medium.com/@sevcsik/authentication-using-https-client-certificates-3c9d270e8326)

**Docker**
- Making secure containers with reduced user privileges
    - [Understanding linux user, read this completely](https://www.freecodecamp.org/news/how-to-manage-users-in-linux/#how-to-create-users)
    - We need to change the user in the docker file before starting the main process (the entrypoint), so that it is run on behalf of the less privileged user
    - Less privileged user can be created like below
    
        `RUN useradd --no-log-init --create-home --shell /bin/bash --uid "1000" --no-user-group "atul" `
    - User can be changed by USER id command, all the below actions are then performed by this user
        
        `USER 1000`
    - WORKDIR creates a directory by root user always, we might also want to change the user of this directory [check this](https://github.com/moby/moby/issues/36408)

            WORKDIR /opt/app
            RUN chown 1000:1000 $(pwd)
            USER 1000
    - We can copy folders and change the owner together
            
            COPY --chown="1000:1000" . .
     - Debugging tricks [here](https://docs.docker.com/engine/reference/builder/#understand-how-arg-and-from-interact) 

            RUN [ "sh", "-c", "whoami"]
            RUN [ "sh", "-c", "ls -al"]
            RUN [ "sh", "-c", "cd .. && ls -al"]
    - Example

            FROM golang:1.21 as builder
            ARG OTEL_VERSION=0.87.0
            WORKDIR /
            COPY . .
            RUN go install go.opentelemetry.io/collector/cmd/builder@v${OTEL_VERSION}
            RUN CGO_ENABLED=0 GOOS=linux GOARCH=amd64 builder --config hv-otel/builder.yaml
            RUN mkdir -p /oteldata
            FROM scratch
            COPY --from=builder /out/hv-otelcol /otel
            COPY --from=builder --chown=10001:10001 /oteldata /oteldata
            USER 10001
            ENTRYPOINT ["/otel"]
