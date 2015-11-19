# Directions
These steps will explain how to deploy the CE 186 Nano DB to Heroku without installing anything on your laptop.

### Accounts
- Setup a [Heroku] account. Its free. 
- Setup a [Cloud9]. Its free. We will use Cloud9 to edit and deploy the app.

### Clone The App
 - Create a new work station on Cloud9 (c9.io) and use the Custom template.This will take a minute as Cloud9 creates a virtual machine.
 - Use the console at the bottom of the page to clone the app into your work station  (if you are unfamilliar with git, the remainder of these directions will seem odd).
```sh
$ git clone https://github.com/ericburger/nano-db-for-heroku
```
 - You now have your own copy of the Nano DB server which you can edit from the Cloud9 work station.
 
### Connect To Heroku
 - Next we will login to Heroku from Cloud9.
```sh
$ heroku login
```

### Create a New Heroku App with a PostreSQL Database
```sh
$ heroku create
$ heroku addons:create heroku-postgresql:hobby-dev
```

### Create a Git Repository
```sh
$ cd nano-db-for-heroku/
$ git init
$ git add --all
$ git commit -m "Initial Save"
```

### Deploy the App
```sh
$ git push heroku master
```
 - That is it. Below are a few more notes.
 
### Run from Cloud9
 - If you have not already done so, install the necessary Python modules.
```sh
$ pip install Flask gunicorn psycopg2
```
 - To run the app from Cloud9, login to Heroku from the Cloud9 console and run
```sh
$ DATABASE_URL=$(heroku config:get DATABASE_URL) heroku local
```
 - The app will be running at https://WORKSPACE-USERNAME.c9users.io/ where WORKSPACE is the name you your workspace and USERNAME is your Cloud9 username. Use CTRL+C to close the app. 
 
### Saving Changes and Pushing to Heroku
 - After making changes to your app, enter these commands to push the changes to Heroku.
```sh
$ cd nano-db-for-heroku/
$ git add --all
$ git commit -m "Message Describing Changes"
$ git push heroku master
```


   [Heroku]: <https://www.heroku.com/>
   [Cloud9]: <https://www.c9.io/>


