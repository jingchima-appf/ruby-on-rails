## Enum type in database
```ruby
enum status: { draft: 0, pulished: 1}
```

## Data Validation
```ruby
  validates_presence_of :title, :body
```

## Data Relationships
- Add relations:
  - 
  `rails g migration add_topic_reference_to_blogs topic:references`
  - In Model file
  ```ruby
    # in topic:
    has_many :blogs
    # in blog:
    belongs_to :topic
  ```
  - For query:
  ```ruby
    t = Topic.first
    t.blogs # references all blogs that belong to t
    
    b = Blog.first
    b.topic # get the topic # give the topic object
  ```
  
  
## SQL
- query
  ```ruby
    Book.where(title: "The Force") # return a collection
    
    # for accessing a single record
    Book.find_by_title("The Force") # Find will only give a single object
    # find_by_title is a dynamic method
  ```
  
  - Attention: if return empty, the return type is actually a collection(empty collection)
    use `.any?` to check
    
  - sum/average/maximum
  ```ruby
    vader = Author.find_by_author("Vader")
    vader.books.sum(:sales) # sum over sales
    vader.maximum(:sales)
    Book.order('sales DESC').first
  ```
- 


## Database Operations
- Default value
  - Set default value in migration file,
  - Set default value in model
  ```ruby
    class EmailValidation < ApplicationRecord
    after_initialize :set_defaults
    def set_defaults
      self.is_valid ||= false
    end
  ```

- Add index
  https://stackoverflow.com/questions/1449459/how-do-i-make-a-column-unique-and-index-it-in-a-ruby-on-rails-migration
  https://apidock.com/rails/ActiveRecord/ConnectionAdapters/SchemaStatements/add_index
  Remove index
  https://apidock.com/rails/ActiveRecord/ConnectionAdapters/SchemaStatements/remove_index

- Some operations 
  - Delete all: `Skill.delete_all`
  
- To do changes to a database, usually use migration
  - generate a migration:
    ` rails g migration migration_name `
  - write the migration file
  - do migration
    `rake db:migrate`
  - delete migration file
    https://stackoverflow.com/questions/3872586/how-to-delete-migration-files-in-rails-3
  - Redo a single migration: rake db:migrate:redo VERSION=xxxxxxx
- Database operations
  - http://guides.rubyonrails.org/active_record_querying.html
  
