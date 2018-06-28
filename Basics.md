## prefix in routes
- to see all routes, use `rake routes`
- Each prefix is actually a method. 
e.g. prefix: portfolio_new
     `portfolio_new_path # portfolio/new/..`
     `portfolio_new_url # localhost:3000/portfolio/new/..`
- Can also pass parameter 
e.g.  edit_porfolio_path(protfolio_item.id) 

## routes
- root route
```ruby
root to: 'pages#home' 
```
- controler#action pattern
e.g. 
```ruby
  get 'about-me', to: 'pages#about'
  # map 'about-me' to 'pages#about', pages is the controller, and about is the action
```
- override resources
```ruby
   resources :portfolios, except: [:show]
   resources :portfolios, only: [:show]
   get 'portfolio/:id', to: 'portfolio#show', as: 'portfolio_show' # 'as' specifies the prefix
```

- 



## redirect
- 
