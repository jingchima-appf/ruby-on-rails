## Ruby Pretzel Colons
https://technology.customink.com/blog/2015/06/08/ruby-pretzels/

## ActionController::API
http://api.rubyonrails.org/classes/ActionController/API.html

## Routes in ruby on rails
http://guides.rubyonrails.org/routing.html#restricting-the-routes-created

## Dynamoid 
https://github.com/Dynamoid/Dynamoid

## HTTP request and response
- Note that `ActionController` doesn't have the method render.
- render function: https://apidock.com/rails/ActionController/Base/render
  e.g. `render json: {key: value} status: not-found`
- params['email'] or params[:email] to access a certain parameter
- to issue an HTTP request 
  e.g. get email_validation_validate_url, headers: @auth_headers
- to get the response, use @response
- to parse JSON, use JSON.parse 

## Command Lines
http://guides.rubyonrails.org/command_line.html
