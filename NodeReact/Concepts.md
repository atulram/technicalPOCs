- react will only work for the root element (the element we specify), thus its a library(working on small part of your code)
- npm
    - package.json is the configuration for npm
    - ^1.1.1 indicates minor and patch version can change (<2.0.0)
    - ~1.1.1 indicate on patch verssion can change (<1.2.0)
    - [stackoverflow](https://stackoverflow.com/questions/22343224/whats-the-difference-between-tilde-and-caret-in-package-json)
    ![](https://bytearcher.com/goodies/semantic-versioning-cheatsheet/wheelbarrel-with-tilde-caret-white-bg-w1000.jpg)
    - Every dependency in node_modules has its own package.josn
    - The purpose of package-lock.json is to ensure that the same dependencies are installed consistently across different environments
    - If package-lock.json is present, dependencies are installed from it
    - We push package-lock.json for apllication to github
    - Dependencies dont push their package-lock.json
    - Node_modules are not pushed
    - devDependencies doesn't go to production code (install with production flag)
    - Anything in the script section can be run using `npm run`, start key doesn't need run, `npm start` will do
- [npx](https://www.freecodecamp.org/news/npm-vs-npx-whats-the-difference/)

    To execute a package with npm you either have to type the local path, like this:

    `$ ./node_modules/.bin/your-package` or you can run a locally installed package by adding it into your package.json file in the scripts section, like this:

    `{
    "name": "your-application",
    "version": "1.0.0",
    "scripts": {
        "your-package": "your-package"
     }
    }`
    Then you can run the script using npm run:
    `npm run your-package`

    With npx

    If you wish to execute a locally installed package, all you need to do is type:
    
    `npx your-package`
    
    npx will check whether _command_ or _package_ (node_modules .bin folder has commands scripts or binary packages) exists in $PATH, or in the local project binaries, and if so it will execute it.

    Another major advantage is the ability to execute a package that wasn’t previously installed

    `npx create-react-app myproj`

    