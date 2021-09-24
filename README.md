<div align="center"> <img align="center" alt="Chords" src="https://user-images.githubusercontent.com/52379890/133371696-2488b42d-62fa-4210-b49f-9ebfea97fcd0.png" height='400' width='600'></div>

# E-POTLI

### Live Example :- https://epotli-wallet.herokuapp.com/

## Deployment

Config.env file should have to provided which contains following field:
1. PORT
2. dbURL
3. email
4. password

__Command For Installing Dependencies :__ npm install <br>
__Command To Run Application :__ npm start


## Base URL

https://epotli-wallet.herokuapp.com/
    
    
# API Documentation

The REST API to E-POTLI is described below :

## Create Wallet

### Request

**Action :** Create Wallet

**Method :** POST

        "email": "testing@gmail.com",
        "password": "password"
    }

### Response

#### Case 1: Wallet created Successfully

    {
        "code": 200,
        "message": "Wallet Created Successfully, Please check your email and verify"
    }

#### Case 2: Either of the fields missing in POST request

     {
        "code": 404,
        "message": "Enter all the fields"
     }

#### Case 3: User registering again with same email id

    {
        "code": 404,
        "message": "User already registed with the given email ID"
    }
    
#### Case 4: Some server side error occurred

    {
        "code": 404,
        "message": "Some Error Occured"
    } 

#### Case 4: Some server side error occurred

    Response

## Login

### Request

**Action :** Login

**Method :** POST

**URL :** https://ewallet-server.herokuapp.com/login

__URL     :__   https://epotli-wallet.herokuapp.com/login

     {
        "email":"kryptonites.ju@gmail.com",
        "password": "Ayush"
     }
    

### Response

#### Case 1: Logged-in Successfully

    {
        "code": 200,
        "message": "Login Successful"
    }

#### Case 2: Incorrect Password

    {
        "code": 404,
        "message": "Incorrect Password"
    }

> **_NOTE :_** **After successfully login the response header will contain a cookie named as “jwt” which contains a json web token that is needed to be sent in each one of the following requests and that will serve the purpose of authentication before accessing each one of the protected route.**

## Logout

### Request

__Action  :__   Logout

__Method  :__   GET

__URL     :__   https://epotli-wallet.herokuapp.com/signout

**Method :** GET

**URL :** https://ewallet-server.herokuapp.com/signout

> **_NOTE :_** **Request with the jwt token as cookies and in response the server will clear the cookie “jwt”**

## Get Wallet Info

### Request

**Action :** Get Wallet Info

**Method :** GET

__URL     :__   https://epotli-wallet.herokuapp.com/getInfo
  

### Response

#### Case 1 : If there is a “jwt” token stored as cookie (When successful login), it will return all the account information
    
  
    {
     "fname": "Ayush",
     "lname": "Addhyan",
     "email": "kayush479@gmail.com",
     "phone": "9801254033",
     "balance": 1,
     "investment": 0,
     "currentInvestment": 0,
     "verified": true
    }

#### Case 2 : If the token is not stored (i.e. the user is not logged in) then it will return

     {
     "code": 404,
     "message": "You need to login first."
     }

#### Case 3 : If there is some server side error it will return

     {
       "code": 404,
       "message": "Some error occured"
     }

## Get Price Index for last 10 days relative to Re.1

### Request

**Action :** Get Price Index for last 10 days relative to Re.1

**Method :** GET

__URL       :__     https://epotli-wallet.herokuapp.com/prices 
    

### Response

    {  
     "priceList": [
     {
      "_id": "6146f7491a24d75f1b0c149f",
      "onDate": "2021-09-19T00:00:00.000Z",
      "price": 0.5,
      "__v": 0
    }
    ] ....
    }  
    


