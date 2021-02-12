# 👩‍💻 REST API PHP for maintaining messages

## About api-messages-php
The following statements are true about a message:
* it has a non-guessable identifier (UUID v4),
* it can contain characters coming from different languages,
* it does not support the usage of html tags,
* it has a maximum number of chars (255 characters),
* e-mail(s) and http link(s) can be part of the message,
* it has an internal counter of how many times the message was
retrieved (unsigned number)

## System dependencies
* built on macOS Catalina Version 10.15.3
* PHP 7.3.11
* mysql Ver 8.0.23 for osx10.15 on x86_64 (Homebrew)

## Database
* mysql

## Using api-messages
You can test the API either via localhost or the deployed version

### Localhost
Start with cloning this repository and change to the project directory:

$ git clone https://github.com/0000magda0000/api-messages-v1.git \
in terminal navigate to the api-messages-php folder

In order to use the API locally, run the apache server with the command `sudo apachectl start` and run the mysql server for example by running the command `mysql.server start` (depending on how mysql was installed, this may vary from machine to machine).
Move the project folder api-messages-php into your Sites folder (~/Sites). If you don't have a Sites folder create one and change your server settings accordingly.

Create a database e.g. with mysql in the command line by typing `create database apimessages;`. <br>
Database credentials: 

```
    host: localhost
    db_name: apimessages
    username: root
    password: 12345678
```
Next in mysql type `use apimessages;` and after that create a table in your DB with the following SQL statement:

```
CREATE TABLE messages (
  uuid VARBINARY(36) NOT NULL,
  content CHAR NOT NULL,
  counter INT UNSIGNED DEFAULT 0,
  PRIMARY KEY ( uuid )
) ENGINE=InnoDB  DEFAULT CHARSET=utf8mb4;

DELIMITER //
CREATE TRIGGER init_uuid BEFORE INSERT ON messages
  FOR EACH ROW SET NEW.uuid = UUID();
//
DELIMITER ;

SELECT BIN_TO_UUID(uuid) AS UUID FROM messages;  
```
For the following instructions when using localhost use the base URL http://localhost/api/message


### Deployed version
The Base URL is https://api-messages-php.herokuapp.com/api/message

## Using api-messages
The API responds to different types of requests, which will be explained below.
Use a “Rest Client” like Postman.
### 1. Get UUIDs of all messages
add the following URL path: `<BASE_URL>/read.php`<br> 
### 2. Get one message by UUID
add the following URL path and a specific UUID: `<BASE_URL>/read_one.php?uuid=UUID`<br>
### 3. Update a specific message by UUID
add the following URL path: `<BASE_URL>/update.php`<br> 
Set the body to `raw` and choose `JSON`\
In JSON format type the keys `"content"` and `"uuid"` with the new text `"this is a great update"` and the UUID as string into the body.<br>
Example:<br>
`{ "content": "this is a great update",
   "uuid": "82bdfc48-6c93-11"
 }`
### 4. Create a new message
add the following URL path: `<BASE_URL>/create.php`<br>
in JSON format type the key `"content"` and the some text `"this is a new message"` into the body.<br>
Example:<br>
`{ "content": "this is a new message" }`
### 5. Delete a message by UUID
add the following URL path: `<BASE_URL>/delete.php`<br> 
Set the body to `raw` and choose `JSON`.<br>
In JSON format type `"uuid"` UUID as string into the body<br>
Example:<br>
`{
   "uuid": "82bdfc48-6c93-11"
 }`

## License
GNU General Public License

