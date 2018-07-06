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

## Test including HTTP Requests
- If use WebMock Gem, then in test real HTTP request is not allowed. To deal with this problem, one way is to use stub_request
```ruby 
    test "unknown email address" do
    email_address = 'disposable@example.com'
    expected_response_body = '{"address":"unknown@example.com","status":"Unknown","sub_status":"mail_server_temporary_error","account":null,"domain":null,"disposable":false,"toxic":false,"firstname":"Zero","lastname":"Bounce","gender":"male","location":null,"creationdate":null,"processedat":null}'
    # stub_request will mask the request and use the 'response' you provide as the http response.
    stub_request(:get, 'https://api.zerobounce.net/v1/validate').with(
      query: hash_including({'email' => email_address}) # this is partial matching
    ).to_return(
      body: expected_response_body,
      :headers => {"Content-Type"=> "application/json"}
    ) # Note that WebMock doesn't allow body to be of hash type, so we have to use json. To change body into hash in response.body, we can specify headers, i.e. :headers => {"Content-Type"=> "application/json"}
    res = send_to_validate email_address
    assert_response :ok
    assert_equal res.body, {:status => :ok, :email => email_address, :message => 'valid : valid email address'}.to_json
  end
```
see documents: https://github.com/bblimke/webmock

## Errors in Module/Gem
- If error occurs in module/gem, we can still use command + b to trace back, and even modify the gem (e.g. add output to help debug)
