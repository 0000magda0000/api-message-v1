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

## What is in this repository?
This repository holds two version of an API with the same behaviour as described in About api-messages. One version is writtein in Rails (api-messages-rails) and one version is built in php (api-messages-php).

## Using api-messages-rails and api-messages-php
Start with cloning this repository:

$ git clone https://github.com/0000magda0000/api-messages-v1.git

open the api version that you would like to see. Each version has it's own README.md with further instructions.
