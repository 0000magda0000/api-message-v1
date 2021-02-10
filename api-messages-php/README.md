# 👩‍💻 REST API for maintaining messages

## About api-messages
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

## Database creation
* mysql

## Using api-messages
In order to use the API, you run it on your local machine. Run the apache server with the command `` by the command `rails server` in terminal, Base URL is `localhost:3000`.
The API responds to different types of requests, which will be explained below.
You can also use a browser “Rest Client” (Like Postman) or [ruby code](https://stackoverflow.com/questions/12161640/setting-request-headers-in-ruby/12161762#12161762).

### 1. Get UUIDs of all messages
add the following to the base url: `<BASE_URL>/api/v1/messages` 
and use a `GET` request
### 2. Get one message by UUID
add a specific UUID to the following: `<BASE_URL>/api/v1/messages/UUID` 
and use a `GET` request
### 3. Update a specific message by UUID
add a specific UUID to following: `<BASE_URL>/api/v1/messages/UUID` 
and use a `POST` request
in JSON format type the key `"content"` and the new text `"this is a great update"` into the body
`{ "content": "this is a great update" }`
### 4. Create a new message
add the following to the base url: `<BASE_URL>/api/v1/messages` 
and use a `POST` request
in JSON format type the key `"content"` and the some text `"this is a new message"` into the body
`{ "content": "this is a new message" }`
### 5. Delete a message by UUID
add a specific UUID to the following: `<BASE_URL>/api/v1/messages/UUID` 
and use a `DELETE` request

## License
GNU General Public License

