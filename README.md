**NodeJS, ReactJS, MongoDB starter App**

1. Create Folder  
```mkdir node-react-starter``` 

2. Create package.json file  
```npm init -y```  

3. Install dependencies  
```npm install --save express body-parser mongoose```  

4. Install development dependencies  
```npm install --save-dev nodemon concurrently```  

5. Create project structure  
```mkdir models routes```  
```touch index.js```  

6. Add the following code to index.js  
```
const express = require('express');
const mongoose = require('mongoose');
const bodyParser = require('body-parser');

const app = express();

app.use(bodyParser.json());

const uri =
    'mongodb+srv://<your username>:<your password>@<your cluster>.mongodb.net/?retryWrites=true&w=majority&appName=<your app name>';

mongoose
    .connect(uri)
    .then(() => console.log('App connected to MongoDB Atlas'))
    .catch((err) => console.error('Error connecting to MongoDB Atlas:', err));

const PORT = process.env.PORT || 5000;
app.listen(PORT, () => {
    console.log(`App running on port ${PORT}`);
});

```  

7. Add a run script inside your package.json file, under scripts:  
```"server": "nodemon index.js"```  

8. Install your driver for MongoBD if you haven't  
```npm install mongodb```  

9. Install environmental variables module  
```npm install dotenv```

10. Create a .env file  
```touch .env```  

11. Add your connection string into your .env file:  
```MONGODB_URI=mongodb+srv://<your username>:<your password>@<your cluster>.mongodb.net/?retryWrites=true&w=majority&appName=<your app name>```

12. Replace your connection string code portion:   
```   
const uri =
    'mongodb+srv://<your username>:<your password>@<your cluster>.mongodb.net/?retryWrites=true&w=majority&appName=<your app name>';
```   

With the following:
```const uri = process.env.MONGODB_URI;```  

13. Run your project:
```npm run server```   # node-react-starter
