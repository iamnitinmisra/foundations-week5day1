# Step-by-step instructions for building out a basic server:

## Basic Instructions

1. create a folder called 'server'
2. inside the server folder create an 'index.js' file
3. use npm to install express, then require it at the top of your index.js file
4. create a variable called app and set its value equal to express invoked
5. Set your server up to accept JSON object responses
6. Set your express server to listen to requests on port 4000

## Detailed Instructions

1. create a folder called 'server'

2. inside the 'server' folder, create a javascript file named 'index.js'

3. in order to get our server working we will need to use Node Package Manager to install a package called 'Express'

   - open up your terminal window and install express using the command

   ```
   npm i express
   ```

4. We will need to import the express package into our index.js file next

   - inside index.js import express

   ```js
   const express = require("express");
   ```

5. Next, for simplicity, we will create a variable called app and set it equal to the invocation of express

   - on the next line, set the invocation of 'express' equal to a variable called 'app'

   ```js
   const app = express();
   ```

6. We would like to accept and use JSON objects in our server's responses, so let's do that.

   - on the next line, use the 'use' method from express to invoke express.json

   ```js
   app.use(express.json());
   ```

7. Finally, we will tell express to set up to listen on port 4000

   - on the next line, set your express server up to listen to requests on port 4000

   ```js
   app.listen(4000, () => console.log("Server running on port 4000"));
   ```

8. Use the nodemon command in your terminal to get your new server listening on port 4000

   - in terminal, use the command

   ```
   nodemon server/index
   ```

9. finally we will create our endpoint and method to handle sending the friends back to the front end

   - add this line BEFORE 'app.listen'

   ```js
   app.get("/api/users", (req, res) => {
     let friends = ["Nitin", "Eric", "Jeddy", "Cameron", "Riley"];
     res.status(200).send(friends);
   });
   ```
