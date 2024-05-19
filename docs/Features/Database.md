# Database

##### MongoDB Setup

1. Create a new project and deploy your cluster on [MongoDB Atlas](https://www.mongodb.com/).
2. In your project, click `Network Access` then `+ Add IP Addresss`. Enter your `IP address` or `0.0.0.0/0` to allow access to the database from anywhere.
3. Then click `Database Access`, and then `+ Add New Database User`. Enter your a Username and Password for the database access. Click on `Built-in Role`, and allow `Read and Write To Any Database`.
4. Then click `Database`, and then `Connect`, and then `Drivers`, and copy the URL. Enter your username + password, and paste your url into .env inside your Backend folder `DB_URL=""`.

With MongoDB Atlas, we will be using Mongoose. In the `Backend/src/services/mongodb/schema`. Where the User Schema is prebuilt for you. But you can add schemas based on your conditions, the example provided.
