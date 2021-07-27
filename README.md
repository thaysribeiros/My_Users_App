# My_Users_App
Simplified user management system.

# Installation instructions

    install:
    gem install sinatra
    gem install sqlite3
    to run the server and create data base:
    ruby app.rb
    User Class stored in my_user_model.rb file

To test with curl requests

#POST on /users to create a new user

curl -X POST -i http://localhost:8080/users -d "firstname=Baby" -d "lastname=Yoda" -d "age=50" -d "password=mandalorian" -d "email=grogu@sw.com"

#GET on /users to return all users (without their passwords)

curl http://localhost:8080/users

#POST on /sign_in (it needs to receive an email and a password) 

curl -c cookies.txt -X POST localhost:8080/sign_in -d email=grogu@mandalorian.sw -d password=mandalorian

#PUT on /users to update a password and return a hash with the user's information

    user needs to be signed in (POST on /sign_in)
    copy cookies from previous POST requests (for signing in)
    
curl -b cookies.txt -X PUT localhost:8080/users -d password=eggs42      

#DELETE on /sign_out

    user needs to be signed in (POST on /sign_in)
    copy cookies from previous POST requests (for signing in)

curl -b cookies.txt -X DELETE localhost:8080/sign_out       

#DELETE on /users to delete user 

   user needs to be signed in (POST on /sign_in)

curl -b cookies.txt -X DELETE localhost:8080/users 
