---
sidebar_position: 5
---

# Api 

For **Mamaket** we used Graph Ql for Api consumption

## Introduction to Graphql
This guide provides an overview of how to use GraphQL queries and mutations in this project. GraphQL is a powerful query language for APIs and a runtime for executing those queries by using a type system you define for your data.

Please check the [Utils Directory](/docs/src-doc/utils) for the configurations of  `ApolloInstance`, `Cache` necessary to set up and run GraphQL.


```jsx title="ApolloInstance.js"
  return {
    headers: {
      ...headers,
      authorization: token ? `Bearer ${token}` : "",
         "content-type": "application/json",
        'apollo-require-preflight': true,
    },
  };
});

const client = new ApolloClient({
  link: authLink.concat(httpLink),
  cache: customInMemoryCache,
});

```

[ApolloInstance](https://www.google.com)

``` jsx title="Cache.js

export const customInMemoryCache = new InMemoryCache({
  typePolicies: {
    Query: {
      fields: {
        cartItems: {
          read() {
            return cartItemsVar();
          },
        },
        serviceCarts: {
          read() {
            return serviceCartVar();
          },
        },
        favItemsVar: {
          read() {
            return favItemsVar();
          },
        },
      },
    },
  },
});

```

[Cache](https://www.google.com)


