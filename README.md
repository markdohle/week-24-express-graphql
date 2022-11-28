# week-24-express-graphql
MIT xPro - Week 24 - Video 24.11, 24.12

1. ```npm init```

2. [express-graphql](https://graphql.org/graphql-js/express-graphql/). Click on the tutorial to see what you need to do.

```npm install express express-graphql graphql --save```

```cat package.json``` to see dendencies

3. Create index.js. Paste in code from the graphql tutorial(Use link provided in step 2).

```
var express = require('express');
var { graphqlHTTP } = require('express-graphql');
var { buildSchema } = require('graphql');

// Construct a schema, using GraphQL schema language
var schema = buildSchema(`
  type Query {
    hello: String
  }
`);

// The root provides a resolver function for each API endpoint
var root = {
  hello: () => {
    return 'Hello world!';
  },
};

var app = express();
app.use('/graphql', graphqlHTTP({
  schema: schema,
  rootValue: root,
  graphiql: true,
}));
app.listen(4000, function() {
    console.log('Running a GraphQL API server at http://localhost:4000/graphql');
});
```

run app ```node index.js```

Bring up ```http://localhost:4000/graphql``` for a nice interface.

- make queries and run them.

type ```{hello}```, and get back
```
{
  "data": {
    "hello": "Hello world!"
  }
}
```