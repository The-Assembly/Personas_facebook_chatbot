# Personas Facebook Chatbot

##1. Install Node.js

##2. Setting up a Facebook Page

##3. Creating a Facebook App

##4. Dialogflow

##5. Setting up your webhook server

Create a directory with the name of your choice. Inside the directory run the following command. 
```
npm init
```
Fill out the necessary information. This creates a _package.json_ file. 

Create a folder named _src_, this will be the root directory.
```
npm install body-parser express
```
Once the installation is complete, create an _index.js_ file in the _src_ directory. 

````
const express = require('express');
const bodyParser = require('body-parser');

const app = express();

app.use(bodyParser.json());
app.use(bodyParser.urlencoded({ extended: true }));

app.listen(5000, () => console.log('Express server is listening on port 5000'));
````
Save the file and run **node index.js** from the _src_ in the terminal.

##6. Set up Facebook verification endpoint

Create a file called _verify-webhook.js_ in the _src_ folder.
```
const verifyWebhook = (req, res) => {
let VERIFY_TOKEN = 'token-name';

let mode = req.query['hub.mode'];
let token = req.query['hub.verify_token'];
let challenge = req.query['hub.challenge'];

if (mode && token === VERIFY_TOKEN) {
    res.status(200).send(challenge);
} else {
    res.sendStatus(403);
    }
};

module.exports = verifyWebhook;
```

Set up our endpoint by adding the following code to your _index.js_ file.
````
const verifyWebhook = require('./verify-webhook');

    app.get('/', verifyWebhook);
```` 
Stop your server by pressing **ctrl + c** and restart it with **node index.js**

#7. Expose your server to the web

Go to https://ngrok.com/download and follow the steps to download and install ngrok. Make sure after installation the ngrok file is in your _src_ folder
````
./ngrok http 5000 
````
Facebook App Webhook verification

Dialogflow integration bot

````
npm install --save dotenv
````

Add the following line to the top of your _index.js_ file.
````
require('dotenv').config({ path: 'variables.env' });
````

Installing the Dialogflow API and install **node-fetch** which will be used to send request to facebook.
````
npm install --save dialogflow
npm install --save node-fetch

````
Now create a file called 


