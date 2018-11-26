# Icebreaker test project
This project is a test project. 

In business level, you are able to create and maintain user and article through REST api.

## 1. Pre-condition to run the project

### 1.1 Install and run mongodb.
Download MongoDB from the following link:
```
https://www.mongodb.com/download-center/community
```
After MongoDB is installed, you can run the server daemon, by the following steps
```
# 1. change to bin folder
cd <MongoDB root folder>
# 2. Run the daemon
./bin/mongod
```
### 1.2 Install nodejs
Skiped.

### 1.3 Install Postman or curl
Skipped
## 2.Run the project
### 2.1 Get dependencies
Change to the project root directory, and run the following command to get dependencies.
```
npm update
```
### 2.2 Start the project
```
node app.js
```

## 3. The following operation can be done through curl
### 3.1 Create user
```
curl --header "Content-Type: application/json" \
  --request POST \
  --data '{"user":{"username":"test","email":"test@gmail.com","password":"123"}}' \
  http://localhost:3000/api/users
```
The response will be like:
```
{"user":{"username":"testuser","email":"testuser@gmail.com","token":"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6IjViZmJiYzk5ZGVkYmNhY2IzODk1N2ZlNyIsInVzZXJuYW1lIjoidGVzdHVzZXIiLCJleHAiOjE1NDg0MDg0NzMsImlhdCI6MTU0MzIyNDQ3M30.hPG-Or0QrwhOAxlyKEJS9j94gECKerF4jcH4YEg-zy0"}}
```
Token is returned, and the token is required to do the other operations. Also, if the token is expired, you can do login to get a new token.
### 3.2 Login
```
curl --header "Content-Type: application/json" \
  --request POST \
  --data '{"user":{"email":"test@gmail.com","password":"123"}}' \
  http://localhost:3000/api/users/login
```
### 3.3 Get user information
```
curl --header "Authorization: Token eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6IjViZmJiZjRhMzEwMGYyNjgzOWExMTQ5MCIsInVzZXJuYW1lIjoidGVzdCIsImV4cCI6MTU0ODQwOTE4MCwiaWF0IjoxNTQzMjI1MTgwfQ.VYz10SeCiPsS8-Q9-nInkpasvkKL331DSugPsotN_XM" \
    --request GET \
    http://localhost:3000/api/user?id=test
```
### 3.4 Create article
```
curl --header "Authorization: Token eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6IjViZmJiZjRhMzEwMGYyNjgzOWExMTQ5MCIsInVzZXJuYW1lIjoidGVzdCIsImV4cCI6MTU0ODQwOTE4MCwiaWF0IjoxNTQzMjI1MTgwfQ.VYz10SeCiPsS8-Q9-nInkpasvkKL331DSugPsotN_XM" \
    --request POST \
    --data '{"article":{"slug":"123","title":"1234","description":"a description","body":"123123123","author":"123"}}' \
    http://localhost:3000/api/articles?id=test
```
The following information will be return if successful.
```
{"article":{"createdAt":"2018-11-26T09:50:21.159Z","updatedAt":"2018-11-26T09:50:21.159Z","author":"test"}}
```
## 4. Conclusion
This simple project contains functionality like authentication, and REST APIs. They are pretty basic, and good to prove my javascript experience within limited time. I am concentrated in JAVA in the last two years, but able to pick front-end/javascript development up in a short time.
