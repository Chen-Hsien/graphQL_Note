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



  
  
