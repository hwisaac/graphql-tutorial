Apollo server 를 이용해 graphql 구현하기

## Setup

프로젝트 셋업

1. `mkdir [폴더명]` : 폴더를 만들어준다
2. code [폴더명] : vscode로 실행
3. npm init y : package.json 생성 (.gitignore파일을 만들어서 node_modules 추가)
4. "type": "module" 을 package.json 에 추가해준다. (import 문법을 쓰게 해줌)
5. npm i apollo-server graphql
6. npm i nodemon -D

```json
// package.json
{
  "name": "tweetql",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "dev": "nodemon server.js"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "dependencies": {
    "apollo-server": "^3.12.0",
    "graphql": "^16.6.0"
  },
  "devDependencies": {
    "nodemon": "^2.0.21"
  },
  "type": "module"
}
```

query Type 추가한다.

```js
// server.js
import { ApolloServer, gql } from 'apollo-server';

// GET /text
// GET /hello
// graphql schema
const typeDefs = gql`
  type Query {
    text: String
    hello: String
  }
`;

const server = new ApolloServer({ typeDefs });

server.listen().then(({ url }) => {
  console.log(`Running on ${url}`);
});
```

`type Query` 와 같은 쿼리타입을 gql 에 제공해야만 한다.
