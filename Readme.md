# BackendSelfLearning

## node.js

- is a server environment
- runs on V8 javascript engine
- commands execute in parallel

## express

- backend web application framework for building RESTful APIs
- **basic commands**

```
import express from "express";
import * as dotenv from "dotenv";

// used to hide environmentals (like API_KEY, PORT,....)

dotenv.config();

// initializes app
const app = express();
const port = process.env.PORT || 9000;

// necessary to use input from user

app.use(express.urlencoded({ extended: true }));

// what happens when someone tries to access [route]

app.get([route],(req,res)=>{res.send("Hello World!")})

// what happens if, for example, someone submits content of a form

app.post([route],(req,res)=>{
    res.send("received your request);
console.log(req.body)
})

// listens to PORT, so we can actually see what we are doing in localhost

app.listen(port, ()=>{ console.log("server listening at", port)}
```

if you want to use the **parameters** in an url, you need to include them with a ":", like this:

```
app.get("/:[YourParameterKeyWord]", (req,res)=>{
res.send(req.params)
})
```

In this example, whenever someone opens the page on "/" with anything attached (like "/lkajsdlöj" or "/123123" or "/hello"), the response will send everything, that follows the "/" (in this case "lkajsdlöj", "123123" or "hello")

To use **query**, you can access everything that comes after the "?" in an url, like "/home?fname=John&lname=Doe":

```
app.get("/", (req,res)=>{
    res.send(`${req.query.fname} ${req.query.lname}`)
})
```

### middlewares

- middlewares are basically functions that you can call in an express function
- they need the "next" keyword as an argument, like for example

```
app.use('/user/:id', (req, res, next) => {
  console.log('Request URL:', req.originalUrl)
  next()
}, (req, res, next) => {
  console.log('Request Type:', req.method)
  next()
})
```

## MVC Model-View-Controller

- architectural pattern

### Model

- manages behaviour and data of the application domain ( Interaction with Database)

### View

- typically: User Interface and presentation

### Controller

- is a link between View and Model: it takes User Input and initiates a response by calling model objects

## SQL(Structured Query Language) vs

- scales vertically by default
- difficult to scale
- good at relations
- mature --> you will find more infos and help on the net and it is not subject to so many changes
- requires SCHEMA
- examples:MySQL, Oracle,

**basic commands**

```
// to create a database
CREATE DATABASE [databasename]

// to create a table
CREATE TABLE [table_name]

// to insert data into table - columns are optional

INSERT INTO table_name (column1, column2, column3, ...)
VALUES (value1, value2, value3, ...);

// to show stuff from table in general

SELECT column1, column2, ...  // you can use "*" here, to show everything
FROM table_name;

// to show all people named Jane from table customers
SELECT *
FROM customers
WHERE fname="Jane"

// to update
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;

// to delete
DELETE FROM table_name WHERE condition;

```

## noSQL (not only structured query language)

- scales horizontally by default
- easier to scale
- bad at relations
- younger --> things like syntax change frequently
- can be used Schema free / is flexible
- examples: MongoDB

## MongoDB

- noSQL database
- everybody "loves" it
- we used it with Mongoose and Compass

**basic commands for shell**

```
// to create database or use a specific database
use [databasename]

// to create a collection
db.createCollection([collectionnameInString])

//to show all documents in a collection
db.[collectionname].find()

//to insert One item into the collection
db.[collectionname].insertOne({key1:"value1", key2: "value2",....})

//to update One item in collection
db.[collectionname].updateOne([filter],[update]) for example
db.users.updateOne({name:"Jane},{$set:{age:20}})

// to delete an item in a collection
db.[collectionname].deleteOne([filter]) for example
db.users.deleteOne({name:"Jane"})
```

## Schemas

- are some kind of pattern or model on how you structure your data
- https://de.wikipedia.org/wiki/Schema_(Informatik)

## JSON vs BSON

### JavaScript Object Notation (JSON)

- maps string keys with string values like {"key1":"value1"}

### Binary JSON (BSON)

- includes information on length and type of object

### example for JSON vs BSON

```
{"hello": "world"} →
\x16\x00\x00\x00           // total document size
\x02                       // 0x02 = type String
hello\x00                  // field name
\x06\x00\x00\x00world\x00  // field value
\x00                       // 0x00 = type EOO ('end of object')
```

https://www.mongodb.com/json-and-bson

## CRUD (Create, Read, Update, Delete)

- those are the basic functions, models should be able to perform

## [POST, GET, PUT, PATCH, DELETE]

- POST, GET, PUT, DELETE are HTTP methods, that correspond to CRUD respectively (Post - Create, Get - Read, Put / Patch - Update, Delete)
- PUT replaces an item / ressource / representation completely
- PATCH only modifies it partially

## callback hell

- i dont know what that meant

## REST (Representational State Transfer)

- refers to a specific software architecture, that aims to standardize the use of information exchange systems / web services

https://en.wikipedia.org/wiki/Representational_state_transfer
