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
    - We generally push package-lock.json for apllication to github
    - Generally dependencies dont push their package-lock.json
    