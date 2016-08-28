authkeeper
======

###About###
An isomorphic javascript ( React + Redux + Node + Express + MongoDB ) starter app which utilizes JWTs (JSON Web Tokens) and React HOCs (Higher-Order Components) for authentication and role-based authorization.


###Installation###

server installation:  from /authkeeper/server run `npm install`

client installation:  from /authkeeper/client run `npm install`

database setup:  setup a mongodb database and connect to it with `mongoose.connect()` in the server's index.js file


###Getting Started###

to start up mongodb run:  `mongod`

to start the server up, go to /authkeeper/server/ and run:  `npm run dev`

to start the client up, go to /authkeeper/client/ and run:  `npm start`


###Usage###

In the client's index.js file we have our components being mapped to various URL routes.  Routes which require authentication/authorization have their components wrapped with the appropriate Higher Order Component (HOC).  RequireAuth limits access to authenticated users and RequireAdmin limits access to admins.  The HOCs here check to see if the user has appropriate credentials by checking their authentication and authorization state which is set by the JSON Web Token (JWT) given to the client on signin.  If the user has the appropriate authentication and authorization credentials, then the HOC will allow the component it wraps to be rendered, otherwise it will kick the user back to the root route ('/').

Examples of routes with access protected by HOCs:

	<Route path="protected_content" component={RequireAuth(ProtectedContent)} />

	<Route path="admin_area" component={RequireAdmin(AdminArea)} />


###Dependencies###

Client-Side

* react - javascript library for creating views/interfaces with components

* redux - responsible for managing the client application's state

* react-router - maps react components to URL routes, thus enabling single-page navigation

* redux-thunk - redux middleware that allows allows us to dispatch actions asynchronously by allowing action creators to return functions

* axios - for making AJAX requests to the server

* jwt-decode - for decoding the data carried in the JWTs given to the authenticated client by the server

* redux-form - an HOC which enables us to store our form state in the redux store

* webpack - builds the client-side portion of our app out of various assets, dependencies, and modules


Server-Side

* express - a node.js http server framework and interface

* mongoose - mongoDB object modeling tool

* jwt-simple - we use this module's encode method to create our JSON Web Tokens (JWTs)

* passportJS
    * passport - express authentication middleware
    * passport-jwt - passport strategy/plugin for authenticating with JSON Web Tokens
    * passport-local - passport strategy/plugin for authenticating with a username and password.

* bcrypt-nodejs - for encrypting user passwords before saving them to the database

* cors - gives clients cross-origin access to the server
