# Getting started

*Read this in other languages: [English](README.md), [Spanish](README.es.md)

This is a Node / Express server application that can be used as an API for consuming the public free services from http://www.catastro.meh.es/esp/sede.asp. 

API is deployed here [Catastro API](https://agile-reaches-32584.herokuapp.com/api)

Some other features are included to extend the service:
- [JSON Web Tokens](https://jwt.io/) - The JSON Web Tokens (aka JWT) for secure ht e non public API as User management and CRUD User's Location operations.  
- [Mongo DB](https://docs.mongodb.com/) - MongoDB is an open-source database that provides high performance, high availability, and automatic scaling. MongoDB data structure is composed of field and value pairs similar to JSON.

To get the Node server running locally:

- Clone this repo https://github.com/aurelido/catastro-node-express.git
- `npm install` to install all required dependencies
- Install MongoDB Community Edition ([instructions](https://docs.mongodb.com/manual/installation/#tutorials)) 
- Create default /data/db directory `mkdir -p ./data/db`
- Run MongoDB by executing `mongod --dbpath ./data/db/`. Now MogoDB is runing on port 27017
- `npm run dev` to start the local server

# Code Overview

## References
Project based in https://github.com/gothinkster/react-redux-realworld-example-app

## Dependencies

- [expressjs](https://github.com/expressjs/express) - The server for handling and routing HTTP requests
- [express-jwt](https://github.com/auth0/express-jwt) - Middleware for validating JWTs for authentication
- [jsonwebtoken](https://github.com/auth0/node-jsonwebtoken) - For generating JWTs used by authentication
- [mongoose](https://github.com/Automattic/mongoose) - For modeling and mapping MongoDB data to javascript 
- [mongoose-unique-validator](https://github.com/blakehaswell/mongoose-unique-validator) - For handling unique validation errors in Mongoose. Mongoose only handles validation at the document level, so a unique index across a collection will throw an exception at the driver level. The `mongoose-unique-validator` plugin helps us by formatting the error like a normal mongoose `ValidationError`.
- [passport](https://github.com/jaredhanson/passport) - For handling user authentication
- [slug](https://github.com/dodo/node-slug) - For encoding titles into a URL-friendly format

## Application Structure

- `app.js` - The entry point to our application. This file defines our express server and connects it to MongoDB using mongoose. It also requires the routes and models we'll be using in the application.
- `config/` - This folder contains configuration for passport as well as a central location for configuration/environment variables.
- `routes/` - This folder contains the route definitions for our API.
- `models/` - This folder contains the schema definitions for our Mongoose models.