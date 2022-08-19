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

- [Source port allocation to establish a TCP/IP connection](https://idea.popcount.org/2014-04-03-bind-before-connect/)
- [Sockets in a Bind](https://blog.heroku.com/sockets-in-a-bind)
- [Details on the socket queues](https://blog.cloudflare.com/syn-packet-handling-in-the-wild/)