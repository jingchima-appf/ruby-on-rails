## To do tests, type in command line:
 `ruby -I test test/controllers/email_validation_controller_test.rb`
 
## 'Setup' Method: this method will be executed before each test
```ruby
  setup do 
    @auth_headers = {"Athorization" => http_login_email}
    @params = { ... }
```

## Detailed Reference:
http://guides.rubyonrails.org/testing.html
