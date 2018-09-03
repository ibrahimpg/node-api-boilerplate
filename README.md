# node-api-boilerplate

A boilerplate REST API for user registration built with Node.js. Built to be easily configurable, highly customizable, and easily extendable. Use of direct image saving to MongoDB saves us from using multer, express-validator, and AW3. Optimized for quick deployment on Heroku with the mLab addon. Simply configure the variables found in the index.js file and follow the instructions for the environmental variables to quickly get the API running and implement user registration for your web, desktop, or mobile application.

---

## Install

1. `git clone https://github.com/ibrahimpg/node-api-boilerplate.git`

2. `cd folderName`

3. `npm install`

4. Follow configuration instructions in index.js

---

## Packages

[express](https://github.com/expressjs/express) 4.16.3 --- [mongoose](https://github.com/Automattic/mongoose) 5.2.12 --- [node-jsonwebtoken](https://github.com/auth0/node-jsonwebtoken) 8.3.0 --- [bcrypt.js](https://github.com/dcodeIO/bcrypt.js) 2.4.3 --- [multer](https://github.com/expressjs/multer) 1.3.1

---

## API

Routes | HTTP | Request Objects | Response Objects[1]
-|-|-|-|-
<**url**>/user/view | GET | none | message
<**url**>/user/register | POST | username, password | message, error
<**url**>/user/login | POST | username, password | message, error, token
<**url**>/user/update | PATCH[3] | token[2], bio, display | message, error
<**url**>/user/delete | DELETE | token[2] | message, error

1. Indicate **possible** response objects.
2. Sent in Authorization header as "Bearer <**token**>"
3. Both bio and display must be sent to the update route.

If you're wondering why it isn't necessary to send the username in the update/delete routes, it's because the JWT middleware is able to unpack them from the token that is received.

---

## Tips

1. On the client: automatically log out user (delete sessionStorage/localStorage) if authentication failure response is received from API.

2. Implement "are you sure you would like to delete your account?" functionality on the client-side. The delete route executes if it receives a valid token. The token contains the user's internal ID and username (and the client having a valid token indicates that they signed in to that account with the correct password).

3. How to use FormData();

4. How to show Base64 as image on the client.

---

## Maybe

* Email confirmation during registration
* Password recovery via email
* Admin routes for admin control panel (maybe irrelevant with upper tier mLab clusters)
* GET request for all users? Depending on the app, for admin use or general public use.

---

## User Model

1. internal ID (auto-generated by mongoose)
2. date of registration
3. username (lowercase alphanumeric between 6 and 16 characters)
4. password (hashed, 6 characters minimum)
5. bio (max 200 characters)
6. display picture

---

## Directory Structure

Coming soon.

---

## License

MIT