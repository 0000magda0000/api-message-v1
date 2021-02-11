# 👩‍💻 REST API RAILS for maintaining messages

## About api-messages-rails
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
* built with Rails 6.0.3.4
* Ruby 2.6.6p146

## Database creation
* mysql2

## Using api-messages
You can test the API either via localhost or the deployed version

### Localhost
Start with cloning this repository and change to the project directory:

$ git clone https://github.com/0000magda0000/api-messages-v1.git \
in terminal navigate to the api-messagiges-rails folder

You will probalby have to run the commands `bundle install` for the gems and `rails db:create db:migrate` to create the db and migrate the migrations file. Once done, run the server by the command `rails server` in terminal.<br>
Base URL for the requests is `localhost:3000/api/v1`.


### Deployed version
The Base URL is https://api-messages-rails.herokuapp.com/api/v1

## Making requests
The API responds to different types of requests, which will be explained below.
You can also use a browser “Rest Client” (Like Postman) or [ruby code](https://stackoverflow.com/questions/12161640/setting-request-headers-in-ruby/12161762#12161762).

### 1. Get UUIDs of all messages
add the following to the base url: `<BASE_URL>/messages`<br>
and use a `GET` request.<br>
The output is UUIDs of all messages in JSON.
### 2. Get one message by UUID
add a specific UUID to the following: `<BASE_URL>/messages/UUID`<br>
and use a `GET` request.<br>
The output is content, counter and UUID of the specific message.<br>
Anytime this specific message is loaded, the counter will increment by 1.
### 3. Update a specific message by UUID
add a specific UUID to following: `<BASE_URL>/messages/UUID`<br>
and use a `PATCH` request
in JSON format type the key `"content"` and the new text `"this is a great update"` into the body<br>
Example:<br>
`{ "content": "this is a great update" }`
### 4. Create a new message
add the following to the base url: `<BASE_URL>/messages`<br>
and use a `POST` request<br>
in JSON format type the key `"content"` and the some text `"this is a new message"` into the body<br>
Example:<br>
`{ "content": "this is a new message" }`
### 5. Delete a message by UUID
add a specific UUID to the following: `<BASE_URL>/messages/UUID`<br>
and use a `DELETE` request

## License
GNU General Public License

