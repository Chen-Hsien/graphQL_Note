# graphql_Try

## Rest API vs GraphQL

#### library
npm install --save express express-graphql graphql lodash


#### schema
紀錄data type, 以及相互之間的關係
GraphQLObjectType有兩個必要參數, name, fields
```javascript
const UserType = new GraphQLObjectType({
  name: "User",
  //need to define the fields with GraphQL type.
  fields: {
    id: { type: GraphQLString },
    firstName: { type: GraphQLString },
    age: { type: GraphQLString },
  },
});
```

#### Root Query
Entry point to Data


### GraphiQL
![image](https://user-images.githubusercontent.com/24216536/210709469-a18898d3-d3cb-44d3-a389-baa21fa96f18.png).   
![image](https://user-images.githubusercontent.com/24216536/210710698-d7526fba-1dd2-4e36-93b9-5fa9d530ec99.png).  

50% write Query , 50% write schema

#### Json server
npm install --save json-server
npm run json:server
```javascript
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "json:server": "json-server --watch db.json"
  },
  ```
![image](https://user-images.githubusercontent.com/24216536/210713725-002d8dec-9f55-4952-8e22-cc05bd5fe0cb.png)
resovle function 會轉換Company Type為實際使用到的型態
User Model | User Type
------|------
id | id
firstName | firstName
age| age
companyId | company(CompanyType)
來看看實際在resolve function中回傳的資料是什麼
```Javascript
const UserType = new GraphQLObjectType({
  name: "User",
  //need to define the fields with GraphQL type.
  fields: {
    id: { type: GraphQLString },
    firstName: { type: GraphQLString },
    age: { type: GraphQLString },
    company: {
        type: CompanyType,
        resolve(parentValue, args) {
            console.log(parentValue, args);
        }
    }
  },
});
```
<img width="505" alt="image" src="https://user-images.githubusercontent.com/24216536/210723688-adbfa717-d66b-44b9-a884-6596e3a0085d.png">

#### Resolve Function

#### Query Fragement
可以預先定義好可重複使用的回傳內容, dont repeat yourself.  
```
fragment companyDetails on Company{
  id
  name
  description
}
```

#### Mutations
允許通過GraphQL進行資料的修改
GraphQLNonNull-> 必填

#### Apollo Server
<img width="1470" alt="image" src="https://user-images.githubusercontent.com/24216536/212226772-8fa6cf3b-5362-4355-8c4d-ceb61dae2771.png">。  
藉由觀察於Apollo Server送出的request可以得到幾個關於GraphQL Query的資訊。 
* Request Method: POST
* Content-Type: application/json
* Response -> {"data":{"greeting":"Hello World"}}

#### graphql-request 輕量http取資料
npm add graphql-request graphql

import {request , gql } from 'graphql-request'
