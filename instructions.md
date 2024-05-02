## Setting up the Database 

- **Windows:** To set up the database and dashboard application locally we will need to install the [Mongo Shell](https://www.mongodb.com/try/download/shell) and [Mongo Compass](https://www.mongodb.com/try/download/compass).

- **Mac:** To set up the database and dashboard application locally we will need to install [Mongo Compass](https://www.mongodb.com/try/download/compass) and
 [Homebrew](https://brew.sh). We will also install MongoDB community using the terminal 

  ```bash
  brew tap mongodb/brew
  brew install mongodb-community
  brew services start mongodb-community
  ```
  We can stop the service using
  ```bash
  brew services stop mongodb-community
  ```

## Instructions
This guide will walk you through importing AAC data into MongoDB, creating a user, and connecting to the database using the Linux shell. To begin working with this software on Windows OS, first follow these instructions to install the bash shell. Otherwise, when working with the environment provided on the Apporto virtual lab, proceed with the following: 

### 1. Import the AAC data

To import AAC data into MongoDB, you can use the `mongoimport` command. Make sure to replace `${MONGO_USER}`, `${MONGO_PASS}`, `${MONGO_PORT}`, and `${MONGO_HOST}` with your actual MongoDB credentials.

```bash
# in the linux shell run the following command to import the aac_shelter_outcomes excel document
mongoimport --username="${MONGO_USER}" --password="${MONGO_PASS}" --port=${MONGO_PORT} --host=${MONGO_HOST} --type=csv --headerline --db AAC --collection animals --authenticationDatabase admin --drop /usr/local/datasets/aac_shelter_outcomes.csv
```

### 2. Create the user

```bash
use admin;
db.createUser({
  user: "username",
  pwd: "password",
  roles: [
    { role: "readWrite", db: "AAC" }
  ]
});
```

### 3. Set the environment variables

```bash
# set the environment
# determine the port number for python connection settings 
printenv | grep -i mongo
# login the user
MONGO_USER=username
MONGO_PASS=password

```

### 4. Verify connection
```mongosh
# open the mongo shell
mongosh
// verify access to the database
show dbs
use AAC
// verify the database has the animals collection
show collections
// verify the collection has the csv document imported successfully 
db.animals.findOne()
// demonstrate connection to the database using the logged in user
db.runCommand({connectionStatus:1})
```

### 5. Add indexes to our database 
To increase data retrieval speed and our database's overall efficiency, we will add indexes for searches that we expect will be frequently used. We will add indexes for the breed and outcome type. 

```mongosh
db.animals.createIndex({ breed: 1 })
db.animals.createIndex({ breed: 1, outcome_type: 1 })
// verify the successful creation with simple queries: 
db.animals.find({ breed: "beagle" }).explain("executionStats")
db.animals.find({ breed: "beagle", outcome_type: "Transfer" }).explain("executionStats")
```

### 6. Install packages

Bash:
```bash
pip install dash==2.8.1
pip install dash-leaflet==0.1.9
pip install pandas==1.4.2
pip install plotly
pip install jupyter-dash
pip install numpy
pip install matplotlib
pip install pymongo
```

### 7. Run the Jupyter Notebook file

You can easily run the Jupyter Notebook file in [Visual Studio Code](https://code.visualstudio.com/download) using the latest Python language extension along with the latest Jupyter Notebook extension. 

<div style="text-align: center;">
  <p><strong>Proudly crafted with ❤️ by <a href="https://github.com/sheraadams" target="_blank">Shera Adams</a>.</strong></p>
</div>
