# cypress-postgres-10v-compatibility

Updates the cypress-postgres module to be compatible with Cypress 10.x.x+ versions after migration from 9.x.x versions

# Installation
* Run below command in terminal to install the cypress postgres
```bash
npm i -D cypress-postgres-10v-compatibility

```
* Open your `cypress/plugins/index.js` file and register a new task
```
module.exports = on => {
    on("task", {
        dbQuery:(query)=> require("cypress-postgres")(query.query,query.connection)
    });
};
```

# How to use it

To query postgres database follow below steps-
* Add postgres database connection details in cypress.json file. Details like-
```
"db":
{"user": "postgres",
"host": "localhost",
"database": "postgres",
"password": "*****",
"port":5432
}
```

* Use dbQuery task in your tests to query postgres database like below-
```
cy.task("dbQuery", {"query":"your sql query"}).then(queryResponse => {
  expect(queryResponse).to.equal("[{Your expected query result}]")
});
```
* If you need to query multiple database you can also pass the connection from scripts like below-
* Create connection in your scripts-
```
let connection={"user": "postgres",
"host": "localhost",
"database": "postgres",
"password": "*****",
"port":5432
}
```
* And use this in your test scripts like below-
```
  cy.task("dbQuery", {"query":"your sql query","connection":connection}).then(queryResponse => {
            expect(queryResponse).to.equal("[{Your expected query result}]")
        });
```
## Contributors


<!-- ALL-CONTRIBUTORS-LIST:START - Do not remove or modify this section -->
<!-- prettier-ignore -->
<table><tr><td align="center"><a href="https://www.linkedin.com/in/siddharth-kala-575ba6175/"><img src="https://media-exp1.licdn.com/dms/image/C4E03AQFSKgEAqprkcA/profile-displayphoto-shrink_400_400/0?e=1602115200&amp;v=beta&amp;t=dXeAXbqHe7MyENd7o8zdH_bbAFdffnAdVx3rsQkygjg" width="100px;" alt="Siddharth Kala"/><br /><sub><b>Siddharth Kala</b></sub></a><br /><a href="https://github.com/siddharth23/cypress-postgres.git" title="Code">💻</a> <a href="https://github.com/siddharth23/cypress-postgres.git" title="Tests">⚠️</a></td></tr></table>

<!-- ALL-CONTRIBUTORS-LIST:END -->

This project follows the [all-contributors](https://github.com/all-contributors/all-contributors) specification. Contributions of any kind welcome!
