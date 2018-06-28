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
  
