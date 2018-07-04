## Delegate
- document: https://apidock.com/rails/Module/delegate
- Allows parent class to use child class's method
```ruby 
  class Greeter < ActiveRecord::Base
    def hello
      'hello'
    end

    def goodbye
      'goodbye'
    end
  end

  class Foo < ActiveRecord::Base
    belongs_to :greeter
    delegate :hello, to: :greeter
  end

  Foo.new.hello   # => "hello"
  Foo.new.goodbye # => NoMethodError: undefined method `goodbye' for #<Foo:0x1af30c>
  ```
  
## Self Class
- https://stackoverflow.com/questions/1630815/why-isnt-the-eigenclass-equivalent-to-self-class-when-it-looks-so-similar

