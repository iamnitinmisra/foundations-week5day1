# Step-by-step instructions for building out a basic server:

## Basic Instructions

1. create a folder called 'server'
2. inside the server folder create an 'index.js' file
3. use npm to install express, then require it at the top of your index.js file
4. create a variable called app and set its value equal to express invoked
5. Set your server up to accept JSON object responses
6. Set your express server to listen to requests on port 4000
7. Create a get request for the endpoint '/api/users' that sends an array of your friends to the front end
8. Start your server up using the nodemon command in your terminal

## Detailed Instructions

1. create a folder called 'server'

2. inside the 'server' folder, create a javascript file named 'index.js'

3. in order to get our server working we will need to use Node Package Manager to install two packages.

   - open up your terminal window and install express and cors using the command

   ```
   npm i express cors
   ```

4. We will need to import the express package into our index.js file next

   - inside index.js, import express

   ```js
   const express = require("express");
   ```

5. import the cors pacakge next, similar to how you imported express

   - inside index.js, import cors

   ```js
   const cors = require("cors");
   ```

   Note: cors is a package that allows our client and server to communicate with each other without the need for advanced configuration

6. Next, to avoid repeating lengthy code, we will create a variable called app that we will reuse to initialize express commands. Set app equal to the invocation of express

   - on the next line, set the invocation of 'express' equal to a variable called 'app'

   ```js
   const app = express();
   ```

7. We would like to accept and use JSON objects in our server's responses, so let's do that.

   - on the next line, use the 'use' method from express to invoke express.json

   ```js
   app.use(express.json());
   ```

8. We will create first endpoint and method to handle sending a friends array back to the client (front end)

   - on the next line create the follow GET endpoint and method as follows:

   ```js
   app.get("/api/users", (req, res) => {
     let friends = ["Nitin", "Eric", "Jeddy", "Cameron", "Riley"];
     res.status(200).send(friends);
   });
   ```

9. Let's add another endpoint and method that will tell us how the weather is today

   - on the next line, create another GET endpoint and method as follows:

   ```js
   app.get("/weather/:temperature", (req, res) => {
     const phrase = `<h3>It was ${req.params.temperature} today</h3>`;
     res.status(200).send(phrase);
   });
   ```

   With object destructuring, we can make the above code a little easier to read

   ```js
   app.get("/weather/:temperature", (req, res) => {
      const { temperature } = req.params;
      const phrase = `<h3>It was ${temperature} today</h3>`
      res.status(200).send(phrase)
   }
   ```

10. Let's now tell express to set our server up to listen on port 4000

    - on the next line, set your express server up to listen to requests on port 4000

    ```js
    app.listen(4000, () => console.log("Server running on port 4000"));
    ```

11. Use the nodemon command in your terminal to get your new server listening on port 4000

    - in terminal, use the command

    ```
    nodemon server/index
    ```

12. Launch the index.html file in your browser and test out your endpoints by clicking the "GET Friends List" button or by navigating to either http://localhost:4000/weather/hot or to http://localhost:4000/weather/cold
