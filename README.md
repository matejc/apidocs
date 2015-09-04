# apidocs
stag + slate = apidocs


## Description

This project combines Stag and Slate to autogenerate documentation for Swagger.


## Installation

    npm install
    cd slate && bundle install


## Usage example

apidocs for Loopback

    stag http://localhost:3000/explorer/resources template.md ./slate/source/index.md


Build documentation (to ./slate/build/)

    cd slate && bundle exec rake build


Serve static html inside ./slate/build

- with Nginx
- with Python (`cd ./slate/build && python -m SimpleHTTPServer`)
- with Ruby (`cd ./slate && bundle exec middleman server`)
